## Backup EC2 using Lambda

### Problems with Lifecycle Manager

1. Policies are effective only after 1 hour of creation
2. Multiple lifecycle policy can not share tags, even if one of the lifecycle policy is disabled
3. On removal of policy all the snapshots which were created previously will not be deleted, someone has to delete manually
4. Snapshots are only created in 12 & 24 hour period, no option for choosing shorter or longer duration

### Using Lambda

1. Create function which will iterate over all EC2 instances based on tags (backup=true)
```python
  from datetime import datetime
  import boto3

  def lambda_handler(event, context):
      ec2_client = boto3.client('ec2')
      regions = [region['RegionName']
                 for region in ec2_client.describe_regions()['Regions']]

      for region in regions:

          print('Instances in EC2 Region {0}:'.format(region))
          ec2 = boto3.resource('ec2', region_name=region)

          instances = ec2.instances.filter(
              Filters=[
                  {'Name': 'tag:backup', 'Values': ['true']}
              ]
          )

          # ISO 8601 timestamp, i.e. 2019-01-31T14:01:58
          timestamp = datetime.utcnow().replace(microsecond=0).isoformat()

          for i in instances.all():
              for v in i.volumes.all():

                  desc = 'Backup of {0}, volume {1}, created {2}'.format(
                      i.id, v.id, timestamp)
                  print(desc)

                  snapshot = v.create_snapshot(Description=desc)

                  print("Created snapshot:", snapshot.id)
```
2. Create another function which will iterate over all snapshots of that account and retain only recent 3 snapshots, delete all other
```python
  import boto3

  def lambda_handler(event, context):

      account_id = boto3.client('sts').get_caller_identity().get('Account')
      ec2 = boto3.client('ec2')
      regions = [region['RegionName']
                 for region in ec2.describe_regions()['Regions']]

      for region in regions:
          print("Region:", region)
          ec2 = boto3.client('ec2', region_name=region)
          response = ec2.describe_snapshots(OwnerIds=[account_id])
          snapshots = response["Snapshots"]

          # Sort snapshots by date ascending
          snapshots.sort(key=lambda x: x["StartTime"])

          # Remove snapshots we want to keep (i.e. 3 most recent)
          snapshots = snapshots[:-3]

          for snapshot in snapshots:
              id = snapshot['SnapshotId']
              try:
                  print("Deleting snapshot:", id)
                  ec2.delete_snapshot(SnapshotId=id)
              except Exception as e:
                  print("Snapshot {} in use, skipping.".format(id))
                  continue
```
3. Use cloudwatch add cron jobs for both the functions




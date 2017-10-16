# Automatically deleting AMI snapshots
When an Amazon Machine Image (AMI) is deregistered, the backing snapshot(s) will remain in your account. This CloudFormation script will deploy a Lambda function to delete these snapshots when an AMI is deregistered.

Each deletion operation is logged as "Deleting `[snapshot_id]` pertaining to `[ami_id]`." An obvious suggestion would be to include the image name. Unfortunately, the Lambda function executes after the AMI has deregistered, and only the AMI ID appears in the CloudTrail JSON. Therefore, it is not possible to obtain the AMI name. 
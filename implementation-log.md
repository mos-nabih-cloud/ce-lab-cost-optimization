# Implementation Log

## What do I have?

EC2:
- 2 running t3.micro, 1 stopped t3.micro

EBS:
- 4 volumes total, 1 unattached 100 GB


```
aws ec2 describe-instances \
  --query 'Reservations[].Instances[].[InstanceId,InstanceType,State.Name,PublicIpAddress]' \
  --output table


aws ec2 describe-volumes \
  --query 'Volumes[].[VolumeId,Size,State,VolumeType]' \
  --output table


aws ec2 describe-volumes \
  --filters "Name=status,Values=available" \
  --query 'Volumes[].[VolumeId,Size,CreateTime]' \
  --output table
```

## Delete unattached volume

Command:
```
aws ec2 delete-volume --volume-id vol-0995c274445241bba
```

Reason: 100 GB gp3 volume sitting unused. Saves $8/month.

## Terminate stopped instance

Command:
```
aws ec2 terminate-instances --instance-ids i-039c39ae5101fd302
```

Reason: instance is stopped, not using it. Frees the 8 GB EBS.

## Verify

After both run:
```
aws ec2 describe-instances --query 'Reservations[].Instances[].[InstanceId,State.Name]' --output table
aws ec2 describe-volumes --query 'Volumes[].[VolumeId,State]' --output table
```

Expected: stopped instance gone, 100 GB volume gone.

#### TASK 3 — Attach IAM Role to EC2 Instance

The EC2 instance profile is used to associate the IAM role with the instance, enabling the use of temporary credentials without access keys.

#### Objective
Attach the IAM role DemoRoleForEC2 to an existing EC2 instance so it can access S3 without access keys.

##### 1 - Identify the EC2 Instance:
List instances and identify the InstanceId:
```bash
aws ec2 describe-instances --query "Reservations[].Instances[].InstanceId" --output text
```


# AWS RESOURCES
Aws scripts repo that contains all basic scripts for perform automatically the creation/update for the cloud formation stack

The script run
**aws cloudformation create-stack --stack-name MyStack --template-body file://MyCloudformationScript.yml  --parameters file://MyEnvironmentVariables.json --region eu-central-1**

**./create.sh ${params1} ${params2} ${params3}**

* params1 = out stack name
* params2 = .yml yaml configuration stack
* params2 = .json yaml parameters

# AWS ENCRYPTION

aws configure in EC2 instance
secret and acccess key
add region
With a user that have key copy the key and complete the commands

# CREATE A FULL CODE DEPLOY FLOW

1) To create your EC2 instance using CloudFormation, first save CF_Template.json to your own S3 bucket, 
then update the command below to reference your bucket as well as the name of a Key pair that you own in the 
region that you are working in. 

WINDOWS users will need to use ^ (Shift + 6) instead of \ for line continuation.

aws cloudformation create-stack --stack-name CodeDeployDemoStack \
--template-url http://s3-eu-west-1.amazonaws.com/cftemplates-faye/CF_Template.json \
--parameters ParameterKey=InstanceCount,ParameterValue=1 \
ParameterKey=InstanceType,ParameterValue=t2.micro \
ParameterKey=KeyPairName,ParameterValue=irkp \
ParameterKey=OperatingSystem,ParameterValue=Linux \
ParameterKey=SSHLocation,ParameterValue=0.0.0.0/0 \
ParameterKey=TagKey,ParameterValue=Name \
ParameterKey=TagValue,ParameterValue=CodeDeployDemo \
--capabilities CAPABILITY_IAM

2) Verify that the Cloud Formation stack has completed using: 
aws cloudformation describe-stacks --stack-name CodeDeployDemoStack --query "Stacks[0].StackStatus" --output text

3) Log in to your instance and check that the CodeDeploy agent has correctly installed:  
sudo service codedeploy-agent status

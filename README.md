# AWS
- Aws scripts repo that contains all basic scripts for perform automatically the cration and the update for the cloud formation stack

The script run
aws cloudformation create-stack --stack-name MyStack --template-body file://MyCloudformationScript.yml  --parameters file://MyEnvironmentVariables.json --region eu-central-1

**./create.sh ${params1} ${params2} ${params3}

params1 = name of the out stack
params2 = .yml yaml configuration stack
params2 = .json yaml parameters



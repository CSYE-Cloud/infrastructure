# infrastructure
**Infrastructure as Code-**

We are going to start setting up our AWS infrastructure. 
This assignment will focus on setting up our networking resources such as Virtual Private Cloud (VPC), Internet Gateway, Route Tables, and Routes. We will use AWS CloudFormation for infrastructure setup and tear down.

**To set up Infrastructure as Code with Cloud Formation-**
Run following commands-

**1)Install AWSCLI-**
- Download and Extract file from https://awscli.amazonaws.com/AWSCLIV2.pkg (for MAC),
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install (for linux), and https://awscli.amazonaws.com/AWSCLIV2.msi (For Windows)

- Move the executable into a directory searched for executables

- Run it to check the path and version- $ which aws

$ aws --version



**2) Create Infrastructure using Cloud Formation-**
- Create CLI Profile for dev and demo separately.

- Give them administrator access.

- Secret key will be generated for both the profiles.
- You should save the access ID and the keys for future use.

- Run these commands- aws configure --profile='name'(dev or demo) and enter the credentials as per accounts

- Assign it for both the profiles.

- Check for both the profiles- .aws vi config and .aws vi credentials



**3) Commands to view VPCs through aws CLI-**
- aws --profile=dev ec2 describe-vpcs
 
- aws ec2 describe-vpcs

To set a default profile in your local machine.
- export AWS_PROFILE=<profile_name> (for Linux/Mac)
- setx AWS_PROFILE=<profile_name> (for Windows)

- export AWS_REGION=<region_name> (for mac/Linux)
- setx AWS_REGION=<region_name> (for Windows)


**4) Run the .yml file on cmd with the command-**
- aws cloudformation deploy --profile name <profile_name> --stack-name <stack_name> --template-file <yml_filename>

- For Parameter changes- (**create/update stack**)

- aws cloudformation deploy --profile <profile_name> --stack-name <stack_name> --template-file <yml_filename>--parameter-overrides VpcCIDR=10.1.1.0/16 PublicSubnet1CIDR=10.1.0.0/24 PublicSubnet2CIDR=10.1.2.0/24 PublicSubnet3CIDR=10.1.3.0/24

**- Delete the Stack-**
- aws cloudformation delete-stack --stack-name <stack_name>

**Command to import the stack through aws cli**
- aws acm import-certificate --certificate <certificate-name> --certificate-chain <bundle-name> --private-key <Private-key filename> --profile=demo

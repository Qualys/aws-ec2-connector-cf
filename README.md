# aws-ec2-connector-cf
THIS SCRIPT IS PROVIDED TO YOU "AS IS."  TO THE EXTENT PERMITTED BY LAW, QUALYS HEREBY DISCLAIMS ALL WARRANTIES AND LIABILITY FOR THE PROVISION OR USE OF THIS SCRIPT.  IN NO EVENT SHALL THESE SCRIPTS BE DEEMED TO BE CLOUD SERVICES AS PROVIDED BY QUALYS

# Qualys API Access Configuration
CloudFormation Template to create a Qualys EC2 Connector and associated role and
managed policy. To run the script you will need to supply credentials for the
Qualys user name and password for Qualys API Access.

Parameters:
  UserName:
    Default: {supply_Qualys_user_name}
...

  Password:
    Default: {supply_Qualys_user_password}

...

BaseUrl:
  Default: <ENTER QUALYS API URL>


# Activating Qualys modules
This file will activate the Vulnerability Management (VM) module by default. If you want to activate other modules you will need to update line 78 to contain a list of the required modules.

Activate VM for the EC2 Connector example
> "ActivationModule": "VM"

Activate VM and Policy Compliance (PC) example
> "ActivationModule": ["VM", "PC"]


# EC2 Connector Name
The Qualys EC2 Connector will be named based on the AWS Account Alias. This value is found by making a call via IAM List Account Alias.


# Modify the Role or Policy Name

If you want to change the Role or Policy name you can edit these settings in line number 27 and/or 182

RoleName:
  Default: CF-QualysEC2ConnectorRole

...

PolicyName:
  Default: Qualys-EC2Connector-CrossAccount-Policy

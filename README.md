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

# Specifying connector default tags
To specify a default tag to all assets inventoried by the connector you can add the tag as part of the json body between line 92 & 93, where tagId is the ID of the tag you want to be applied at the connector level. 
Single Default Connector Tag Example:

"defaultTags": {
  "set": {
    "TagSimple": {
      "id": "tagId"
    }
 }
},

Multiple Default Connector Tags Example

"defaultTags": {
  "set": {
    "TagSimple": {
      "id": [
        "tagId-1",
        "tagId-2",
        "tagId-3"
      ]
    }
  }
},

# Activating Qualys modules
This file will activate the Vulnerability Management (VM) module by default. If you want to activate other modules you will need to update line 78 to contain a list of the required modules.

Activate VM for the EC2 Connector example
> "ActivationModule": "VM"

Activate VM and Policy Compliance (PC) example
> "ActivationModule": ["VM", "PC"]

# Qualys CloudView Connector creation
The CloudView Connector will be created when this CloudFormation Template is run. If you want to disable this feature change line 83 to false
Line 83 - "useForCloudView":"true"

# EC2 Connector Name
The Qualys EC2 Connector will be named based on the AWS Account Alias. This value is found by making a call via IAM List Account Alias.


# Modify the Role Name

If you want to change the Role name you can edit these settings in line number 27

RoleName:
  Default: CF-QualysConnectorRole

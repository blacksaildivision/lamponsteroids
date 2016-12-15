AWSCLI role
===========

This role will install AWS CLI command line tool for accessing AWS services.

**Configuration**
AWS CLI can be configured for several users. Default user is `developer`. If you are using whole LampOnSteroids project such user will be created.
If you are just using this role, you need to set `awscli_users` to existing users. 

Other values that should be set (normally there are requested during aws configure command )are: 
 - `awscli_aws_access_key_id`
 - `awscli_aws_secret_access_key`
 - `awscli_default_region_name`
 - `awscli_default_output_format`

AWS access Key and Secret Access Key should not be stored in repository directly. Please use Ansible Vault for that purpose.

AWS CLI role
===========

This role will install AWS CLI command line tool for accessing AWS services.

Variables
---------
Here is the list of configurable variables for this role:

 - `awscli_version` AWS CLI version to install.

 - `awscli_zip_file_location` directory where zip file with AWS CLI should be downloaded.
 
 - `awscli_users` list of users where configuration files will be saved. Defaults to `root` and `developer`.
 
 - `awscli_aws_access_key_id` AWS Access Key ID.
  
 - `awscli_aws_secret_access_key` AWS Secret Access Key.
 
 - `awscli_default_region_name` AWS Region.
 
 - `awscli_default_output_format` Output format of AWS console. Defaults to `text`.

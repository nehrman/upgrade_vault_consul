role_vault_upgrade
=========

This ansible role manages the upgrade of vault enterprise edition.

Warnings
------------

* Make sure to set the variable `vault_version` appropriately. This role assumes the version specified is correct, and there is no version comparison with the existing deployed vault binary.

Requirements
------------

Todo.

Role Variables
--------------

The role uses variables defined in these 2 places:

- Inventory variables  (host or group variables )
- `defaults/main.yml` 

Some role variables can also take their values from environment variables as well; those are noted in the description where appropriate.

#### `vault_aws_access_key` (**Mandatory**)

- AWS access key for downloading vault enterprise binaries

#### `vault_aws_secret_key` (**Mandatory**)

- AWS access key for downloading vault enterprise binaries


#### `vault_aws_bucket`

- Name of the AWS S3 bucket on which vault binaries are available
- Default value: hc-enterprise-binaries
  
#### `vault_version` (**Mandatory**)

- Version of the vault package to install. Make sure the value is greater to the current deployed version.
  
#### `vault_pkg`

- Name of the vault package 
- Default value: vault-enterprise_{{ vault_version }}+prem.hsm_linux_amd64.zip

#### `vault_download_path`

- Path for downloaded vault binary package
- Default value: /tmp

#### `vault_bin_path`

- Location of vault binarie on target hosts
- Default value: /usr/local/bin

Dependencies
------------

This role make use of the following roles. Make sure you set dependencies of your playbook accordingly.
- 

 
Example Playbook
----------------

This example shows how to use the role in a playbook:

    - hosts: servers
      roles:
         - role: role_vault_upgrade
           vault_aws_secret_key: <my-secret-key> 
           vault_aws_access_key: <my-access-key>
           vault_version: '1.3.0'


License
-------

BSD

Author Information
------------------

Orleant Epal Njamen (IT OP NU)
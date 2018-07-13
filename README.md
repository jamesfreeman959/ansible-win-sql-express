# ansible windows mssql express 
playbooks for installing windows sql server express edition

# Compatibility
These playbooks have been tested on Windows Server 2016, and both using Ansible 2.5.5 from the shell, and via Ansible Tower 3.2.5

# Getting Up and Running
Before running these playbooks, there is some bare minimum configuration that must be performed. For the instance you wish to install, edit the file named **files/sql_conf.ini.j2**

The bare minimum to edit in this file is:

* SQLSVCACCOUNT="DOMAIN\user"
* SQLSVCPASSWORD="xxxxxx" 
* RSSVCACCOUNT=""
* RSSVCPASSWORD="xxxxxx"

Of these, __SQLSVCACCOUNT__ must be a valid local or domain account specified appropriately, with the corresponding password in the __SQLSVCPASSWORD__ parameter. If you want another group other than local Administrators to have admin access to the database, you must also edit:

* SQLSYSADMINACCOUNTS="BUILTIN\Administrators"

The __RSSVCACCOUNT__ and __RSSVCPASSWORD__ fields are mandatory and specified the startup account for reporting services. For more information, see:

https://docs.microsoft.com/en-us/sql/database-engine/install-windows/install-sql-server-from-the-command-prompt?view=sql-server-2017

Finally, to allow the playbook to become a local administrator you will need to set __ansible_become_password__ in the head of __installsql.yml__. 

 Deploy Playbook
===================

 Requirements
------------------
Checklist:
 + have the current master of this ansible cloned
 + your local branch is up to date
 + all submodules are initialized and up to date
 + You have the current ansible installed *(at least version 2.8)*

 How to deploy
-----------------
To deploy the ansible playbooks make sure all requirements are successful.<br/>
Choose the project your working on and deploy the playbook.
E.g. If you changed something at the toolbox gateway *(router)* you probably want to execute the gateway.yml playbook. Example:
```bash
ansible-playbook gateway.yml
```

 Protipp
-----------
If you just want to Update the dhcpd role part, you can use the tag ``dhcpd``. Example:

```bash
ansible-playbook gateway.yml --tags="dhcpd"
```

## Not implemented features:

 general playbook
----------------
Currently there is no default playbook like ``site.yml`` available to run all features for all nodes.
This is an open point one the todo list.

 Deploy Host
--------------
There is currently no dedicated depoy host planed. And no part inside the playbook is checking if you have the current ansible version installed.
This could be changed... But currently everyone have to look about his own local version of the master branch.<br/>
This means, if you don't know how to deal with git and git submodules, you better not peloy these playbooks to.

 Automation
-------------
There is the idea to deploy the ansible playbooks automatically via continius integration services.

This is currentlx *(June 2019)* not implemented. All playbooks need to be executed by hand.


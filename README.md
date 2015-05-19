# elk service

This will create a mesos infrastructure and deploy 1 elk master node and 1 data node on this infrastructure.

## Installation

* Install a saltmaster. Use Michael's tool at https://repo.hovitos.engineering/mids_scaling_up/spark_cluster/blob/master/sl-saltmaster-bootstrap.py

'''shell
   ./sl-saltmaster-bootstrap.py --datacenter <datacenter> --sshkeyid <keyid> --debug <hostname> <domain>
'''

* copy the root directory to the / directory on the server

   cd <git-root>/root
   sshpass -p <password> scp -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=no -r * root@<salt-master-ip>:/

* ssh to the salt master and issue elk.init to initialize the environment

   elk.init --projectname <aName> --sluser <softlayer-userid> --slapikey <api-key> 
   optional parameters:
      --logconfig configfile - overwrite the default logging levels
      --noclean - donot cleanup on error

you should now have an elk cluster to use.

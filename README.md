# ansible-cassandra-play
Rollout Cassandra in a virtual environment using a pre-created role. Requires a Linux or Mac machine that can run Ansible. The playbook uses https://github.com/locp/ansible-role-cassandra as the underlying role.

### Features
* Deploy Cassandra on a set of AWS EC2 instances of a configured type;
* Create the instances before if there are none available. 

### Prerequisites
Make sure you have an AWS profile with broad EC2 permissions configured as a `default`, or do `export AWS_PROFILE=profile_name` before proceeding with the steps below.  
  
### How to use this repository:
1. Make sure you have ansible (at least 2.7) installed on your machine:
   1. For Debian-based systems: `apt-get install ansible`
   2. For MacOS: `brew install ansible`
2. Install the underlying role locally: `ansible-galaxy install locp.cassandra`
3. If you'd like to create the instances for Cassandra first, please configure variables on top of `playbooks/run.yml` and then run `ansible-playbook -i inventory -l cassandra run.yml`
4.  The cassandra installation. 
    1.  Configure any variables and overrides in `playbooks/cassandra.yml`. For a full list of variables, refer to the role's git repo. 
    2.  This playbook uses a dynamic inventory file, so please make sure your cassandra instances are tagged with `application:cassandra`.
    3.  Run: `ansible-playbook -i inventory/eu playbooks/tasks/cassandra.yml` to do the installation.
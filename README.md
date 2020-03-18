# ansible-cassandra-play
Rollout Cassandra in a virtual environment using a pre-created role.
Requires a Linux or Mac machine that can run ansible.

### How to use this repository:
1. Make sure you have ansible (at least 2.7) installed on your machine:
   1. For Debian-based systems: `apt-get install ansible`
   2. For MacOS: `brew install ansible`
2. Install the underlying role locally: `ansible-galaxy install locp.cassandra`
3. Run the ansible playbook, considering the 'Run parameters' section below.

### Run parameters
Using this playbook it's possible to either create the docker images for running the cluster, or use existing machines. If you already have machines you would like to use,
then add an inventory file in the `playbooks/` folder with your hosts:
```
[cassandra]
app01.example.com
app02.example.com
```
Then change directory to `playbooks/` and run:
`ansible-playbook -i inventory -l cassandra run.yml`

If you'd like to create resources for your installation, then run:
`ansible-playbook play.yml`
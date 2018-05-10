# ssh-auto
Creates some VMs, then gives access

# Packages Needed
Ansible, vagrant, virtualbox

# Walkthrough
1. run `vagrant up`. Will take a few minutes. This will create 4 virtual machines, assigned to the ips `192.168.73.1[0-3]`
2. Observe that you cannot ssh into one of them: `ssh -i keys/person person@192.168.73.11`
3. Run ansible stuff `ANSIBLE_HOST_KEY_CHECKING=False ANSIBLE_HOSTS=hosts ansible-playbook ssh_add.yml`.
4. Observe that you can now ssh into one of them: `ssh -i keys/person person@192.168.73.11`

# How it works
In the ssh_add playbook file, there is a variable for the list of usernames. Ansible knows about the machines because of the hosts file. There is a task to create a user account for each of these usernames on each machine. And another task to add their key so that they can ssh in. The keys are stored here, ansible only needs the public one. The private one is checked into the repo so that you test it out.

# Troubleshooting
You may have issues with iptables/firewall. Disable if needed. May need to clear your `known_hosts` file. On my machine while making this, sometimes the ansible provisioner needed a bit more time after vagrant spun up the boxes. Just wait a minute and run again.

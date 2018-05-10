# ssh-auto
Creates some VMs, then gives access

# Packages Needed
Ansible, vagrant, virtualbox

# Walkthrough
1. run `vagrant up`. Will take a few minutes. This will create 4 virtual machines, assigned to the ips `192.168.73.1[0-3]`
2. Observe that you cannot ssh into one of them: `ssh -i keys/person person@192.168.73.11`
3. Run ansible stuff `ANSIBLE_HOST_KEY_CHECKING=False ANSIBLE_HOSTS=hosts ansible-playbook ssh_add.yml`
4. Observe that you can now ssh into one of them: `ssh -i keys/person person@192.168.73.11`

# Troubleshooting
You may have issues with iptables/firewall. Disable if needed. May need to clear your `known_hosts` file.

# ssh-auto
Creates some VMs, then gives access

# Packages Needed
Vagrant, ansible

# Walkthrough
1. run `vagrant up`. Will take a few minutes. This will create 4 virtual machines, assigned to the ips `192.168.73.[0-3]`
2. Observe that you cannot ssh into one of them: `ssh demo@192.168.73.1`
3. Run ansible stuff `ANSIBLE_HOST_KEY_CHECKING=False ANSIBLE_HOSTS=hosts ansible-playbook ssh_add.yml`
4. Observe that you can now ssh into one of them: `ssh demo@192.168.73.1`
$script = <<-SCRIPT
sudo apt -y install python2.7
SCRIPT


Vagrant.configure("2") do |config|

  4.times do |i|
    config.vm.define i.to_s do |machine|
      machine.vm.box = "ubuntu/bionic64"
      config.vm.network "private_network", ip: "192.168.73.1" + i.to_s
      config.vm.provision "shell", inline: $script
      config.ssh.insert_key = false
    end
  end

end

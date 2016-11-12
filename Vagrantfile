Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"
  config.vm.define "aws-credentials"

  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 2
  end
  
  config.vm.synced_folder ".", "/home/vagrant/sync", disabled: true
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

  config.vm.provision :shell, inline: "sudo yum install epel-release -y; sudo yum install ansible -y"
  config.vm.provision :shell, inline: "cp /vagrant/ansible.cfg ~/.ansible.cfg"
  config.vm.provision :shell, inline: "cd /vagrant; ansible-playbook -i localhost, site.yml"
end

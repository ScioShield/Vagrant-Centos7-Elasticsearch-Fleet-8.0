Vagrant.configure("2") do |config|
  config.vm.define "Elastic" do |elastic|
    elastic.vm.box = "bento/centos-7"
    elastic.vm.hostname = 'elastic-8'
    elastic.vm.box_url = "bento/centos-7"
    elastic.vm.provision :shell, path: "ESBootstrap.sh"
    elastic.vm.network :private_network, ip:"10.0.2.15"
    elastic.vm.network "forwarded_port", guest: 5601, host: 5601, host_ip:"127.0.0.1"
    elastic.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--cpus", 4]
      v.customize ["modifyvm", :id, "--memory", 8192]
      v.customize ["modifyvm", :id, "--name", "elastic-8"]
    end
  end
  config.vm.define "Agent" do |agent|
    agent.vm.box = "bento/centos-7"
    agent.vm.hostname = 'agent-8'
    agent.vm.box_url = "bento/centos-7"
    agent.vm.network :private_network, ip: "10.0.2.20"
    agent.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--cpus", 1]
      v.customize ["modifyvm", :id, "--memory", 1024]
      v.customize ["modifyvm", :id, "--name", "agent-8"]
    end
  end
end
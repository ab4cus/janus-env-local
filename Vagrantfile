Vagrant::Config.run do |config|

  config.vm.define :web do |web_config|
    web_config.vm.box = "web"
    web_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.8_chef-provisionerless.box"
    web_config.vm.network :hostonly, "192.168.14.110"
	config.vm.network "public_network", ip: "192.168.0.17"
    web_config.vm.forward_port 80, 8080

    web_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "janus_web_vm_1"
      chef.add_role "base"
    end
  end


  config.vm.define :im do |im_config|
    im_config.vm.box = "im"
    im_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.8_chef-provisionerless.box"
    im_config.vm.network :hostonly, "192.168.14.120"
#	im_config.vm.network :private_network, ip: "192.168.3.10"
#	im_config.vm.host_name = "sso.e4cash.net"
#	im_config.hostsupdater.aliases = ["alias.e4cash.net", "ldap.e4cash.net"]

    im_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "janus_im_vm_1"
      chef.add_role "base"
    end
  end  
  
  end

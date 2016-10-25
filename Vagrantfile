# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.define :web do |web_config|
    web_config.vm.box = "web"
    web_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.2_chef-provisionerless.box"
    web_config.vm.network :hostonly, "192.168.14.110"
    web_config.vm.forward_port 80, 8080

    web_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "ab4cus_web_vm_01"
      chef.add_role "base"
      chef.add_role "application"
    end
  end

  config.vm.define :as do |as_config|
    as_config.vm.box = "as-local"
    as_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.2_chef-provisionerless.box"
    as_config.vm.network :hostonly, "192.168.14.120"
    as_config.vm.forward_port 7777, 7001

    as_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "ab4cus_as_vm_01"
      chef.add_role "base"
      chef.add_role "application"
    end
  end

  config.vm.define :im do |im_config|
    im_config.vm.box = "im-local"
    im_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.2_chef-provisionerless.box"
    im_config.vm.network :hostonly, "192.168.14.130"
    im_config.vm.forward_port 363, 636

    mongo_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "ab4cus_im_vm_01"
      chef.add_role "base"
      chef.add_role "application"
    end
  end
    
  
  config.vm.define :db do |db_config|
    db_config.vm.box = "db-local"
    db_config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.2_chef-provisionerless.box"
    db_config.vm.network :hostonly, "192.168.14.140"
    db_config.vm.forward_port 1521, 27017, 27018

    mongo_config.vm.provision :chef_client do |chef|
      chef.chef_server_url = "https://api.opscode.com/organizations/ab4cus"
      chef.validation_key_path = "./.chef/ab4cusdev-validator.pem"
      chef.validation_client_name = "ab4cus-validator"
      chef.node_name = "ab4cus_db_vm_01"
      chef.add_role "base"
      chef.add_role "mongodb"
    end
  end
end

Vagrant.configure("2") do |config|

    config.vm.provider :virtualbox do |v|
        v.name = "magento2"
        v.customize ['modifyvm', :id, '--natdnshostresolver1', "on"]
        v.customize ['modifyvm', :id, '--memory', "4048"]
        v.customize ['modifyvm', :id, '--cpus', "4"]
    end

    config.vm.box = "ubuntu/trusty64"
    config.vm.network :private_network, ip: "192.168.33.99"
    config.ssh.forward_agent = true

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
    end

    config.vm.synced_folder "./src", "/var/www",
        id: "site",
        mount_options: ['dmode=776', 'fmode=664'],
        owner: "www-data",
        group: "www-data"
end

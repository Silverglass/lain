# vim: ft=ruby:

Vagrant.configure(2) do |config|

  (1..3).each do |i|
    nodename = "node#{i}"

    config.vm.define nodename, primary: i == 1, autostart: i == 1 do |node|

      node.vm.box = "laincloud/centos-lain"
      node.vm.hostname = nodename

      node.vm.provider "virtualbox" do |v|
        v.memory = i == 1 ? 1536 : 512
      end
      
      node.vm.provision "shell",
        inline: i == 1 ? "sudo /vagrant/bootstrap -m https://l2ohopf9.mirror.aliyuncs.com -r docker.io/laincloud --vip=192.168.77.201" : ""     

      node.vm.network "private_network", ip: "192.168.77.2#{i}"

    end

  end

end


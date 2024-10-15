Vagrant.configure("2") do |config|
  config.vm.box = "jammy"
  config.vm.provider :virtualbox do |v|
    v.memory = 3100
    v.cpus = 2
  end


  boxes = [
    { :name => "web",
      :ip => "192.168.56.11",
    },
    { :name => "log",
      :ip => "192.168.56.15",
    },
    { :name => "elk",
      :ip => "192.168.56.16",
    }
  ]

  
  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network "private_network", ip: opts[:ip]

      if opts[:name] == boxes.last[:name]
        config.vm.provision "ansible" do |ansible|
          ansible.playbook = "ansible/provision.yml"
          ansible.inventory_path = "ansible/hosts"
          ansible.host_key_checking = "false"
          ansible.limit = "all"
       end
      end
    end
  end
end

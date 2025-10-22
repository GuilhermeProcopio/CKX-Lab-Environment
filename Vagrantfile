Vagrant.configure("2") do |config| 
    config.vm.box = "generic/ubuntu2204"
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # for HA 2 control-plane, but its a lab environment, 
    # so 1 control-plane and 2 data-plane
  NODES = {
    "control-plane" => { :memory => 3072, :cpus => 2, :ip => "192.168.56.10" },
    "worker1"       => { :memory => 2048, :cpus => 2, :ip => "192.168.56.11" },
    "worker2"       => { :memory => 2048, :cpus => 2, :ip => "192.168.56.12" }
  }

  NODES.each do |name, opts|
    config.vm.define name do |node|
      node.vm.hostname = name
      node.vm.provider :libvirt do |v|
        v.memory = opts[:memory]
        v.cpus = opts[:cpus]
        v.nested = true
      end
      node.vm.network "private_network", ip: opts[:ip]
    end
  end
end
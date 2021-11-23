Vagrant.configure("2") do |config|

# galactica
  config.vm.define "galactica" do |cfg|
    cfg.vm.box = "generic/debian11"
    cfg.vm.hostname = "galactica"
    # change the bridged adapter to fit your systems available NIC
    cfg.vm.network "public_network", type: "dhcp", bridge: 'enp1s0', mac: "0020911E000E"
    cfg.vm.provision :file, source: './configfiles', destination: "/tmp/configfiles"
    cfg.vm.provision :shell, path: "bootstrap.sh"

    cfg.vm.provider "virtualbox" do |vb, override|
      vb.gui = false
      vb.name = "galactica"
      vb.customize ["modifyvm", :id, "--memory", 4096]
      vb.customize ["modifyvm", :id, "--cpus", 4]
      vb.customize ["modifyvm", :id, "--vram", "4"]
      vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
      vb.customize ["setextradata", "global", "GUI/SuppressMessages", "all" ]
    end
  end

end

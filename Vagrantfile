Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  # config.vm.network "private_network", ip: "192.168.56.10"
  config.vm.network "public_network", type: "dhcp"

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |vbox|
    vbox.gui = true
    vbox.cpus = 4
    vbox.memory = 8192
    vbox.customize [
      "modifyvm", :id,
      "--vram", "256",                  # for full screen mode
      "--clipboard", "bidirectional",   # for clipboard share
      "--draganddrop", "bidirectional", # for drag and drop
      "--ioapic", "on",                 # for activating I/O APIC
      "--nested-hw-virt", "on",         # for Nested Virtualization
      "--accelerate3d", "on",
      "--hwvirtex", "on",
      "--nestedpaging", "on",
      "--largepages", "on",
      "--pae", "on",
      "--paravirtprovider", "kvm",
    ]
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade
    apt-get install -y ubuntu-desktop

    reboot
  SHELL
end

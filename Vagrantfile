# export VAGRANT_DEFAULT_PROVIDER=virtualbox

Vagrant.configure(2) do |config|

  config.vm.box = "boxcutter/ol67"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
    vb.gui = false
    vb.linked_clone = true
  end

  config.vm.provider "parallels" do |prl|
    prl.memory = "2048"
    prl.linked_clone = true
    prl.update_guest_tools = false
    prl.check_guest_tools = false
    prl.customize ["set", :id, "--sh-app-guest-to-host", "off"]
    prl.customize ["set", :id, "--shared-cloud", "off"]
    prl.customize ["set", :id, "--shared-profile", "off"]
    prl.customize ["set", :id, "--time-sync", "on"]
  end

  config.vm.hostname = "jenkins"
  #config.vm.synced_folder "/Users/vad/dev/files", "/mnt/files"
  config.vm.network :forwarded_port, guest: 8080, host: 8080 # jenkins web
  config.vm.network "private_network", ip: "10.0.2.15"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "test.yml"
  end
end

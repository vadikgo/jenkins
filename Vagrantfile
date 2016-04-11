# export VAGRANT_DEFAULT_PROVIDER=virtualbox

Vagrant.configure(2) do |config|

  config.vm.box = "boxcutter/ol67"

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "4096"
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

  config.vm.hostname = "ovp1"
  #config.vm.synced_folder "/Users/vad/dev/files", "/mnt/files"
  config.vm.network :forwarded_port, guest: 9060, host: 9060 # was
  config.vm.network :forwarded_port, guest: 9043, host: 9043 # was ssl
  config.vm.network :forwarded_port, guest: 1414, host: 1414 # mq
  config.vm.network :forwarded_port, guest: 1521, host: 1521 # oracle
  config.vm.network :forwarded_port, guest: 8080, host: 8080 # storm
  config.vm.network "private_network", ip: "10.0.2.15"
#  config.vm.provision "shell", inline: <<-SHELL
#     sudo yum update -y
#  SHELL

#  config.vm.provision "ansible" do |ansible|
#    ansible.verbose = "v"
#    ansible.groups = {
#      "mq" => [config.vm.hostname, 'ansible_host'],
#      "was" => [config.vm.hostname],
#    }
#    if ENV['VAGRANT_DEFAULT_PROVIDER']
#        #ansible.playbook = "oracle-prl.yml"
#    else
#        #ansible.playbook = "xhyve-playbook.yml"
#    end
#  end
end

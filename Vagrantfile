Vagrant.require_version ">= 1.4.3"
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  (1..3).each do |i|
    config.vm.define "node#{i}" do |node|
      node.vm.box = "origin"
      node.vm.box_url = "http://files.brianbirkinbine.com/vagrant-centos-65-i386-minimal.box"
      node.vm.provider "virtualbox" do |v|
        v.name = "node#{i}"
        v.customize ["modifyvm", :id, "--memory", "1536"]
      end
      node.vm.network :private_network, ip: "11.11.11.10#{i}"
      node.vm.hostname = "node#{i}"
    end
  end
  config.vm.define "haproxy" do |node|
    node.vm.box = "origin"
    node.vm.provider "virtualbox" do |v|
      v.name = "haproxy"
      v.customize ["modifyvm", :id, "--memory", "1024"]
    end
    node.vm.network :private_network, ip: "11.11.11.104"
    node.vm.hostname = "haproxy"
  end
end

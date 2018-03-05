Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
    v.memory = "2048"
  end
  config.vm.define "winAD01" do |winAD01|
    winAD01.vm.box = "mwrock/Windows2012R2"
    winAD01.vm.hostname = "winAD01"
    winAD01.vm.network "private_network", ip: "192.168.60.151"
  end
end

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    v.memory = "2048"
  end
  config.vm.define "winAD2012R2" do |winAD01|
    winAD01.vm.box = "mwrock/Windows2012R2"
#   winAD01.vm.box = "mwrock/Windows2016"
    winAD01.vm.hostname = "winAD2012R2"
    winAD01.vm.network "private_network", ip: "192.168.60.151"
  end
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    v.memory = "2048"
  end
  config.vm.define "winAD2016" do |winAD16|
#   winAD16.vm.box = "mwrock/Windows2012R2"
    winAD16.vm.box = "mwrock/Windows2016"
    winAD16.vm.hostname = "winAD2016"
    winAD16.vm.network "private_network", ip: "192.168.60.152"
  end
end

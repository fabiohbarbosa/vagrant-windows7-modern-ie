Vagrant.configure(2) do |config|
  config.vm.box = "windows7"
  config.vm.box_url = "https://modernievirt.blob.core.windows.net/vhd/VMBuild_20140627/Vagrant/IE8.Win7.For.Vagrant.box"

  # @see
  # http://blog.syntaxc4.net/post/2014/09/03/windows-boxes-for-vagrant-courtesy-of-modern-ie.aspx

  config.windows.halt_timeout = 30

  config.vm.communicator = "winrm"

  config.vm.guest = :windows

  config.vm.synced_folder "/home/fabio/Downloads", "/vagrant", :nfs => { :mount_options => ["dmode=777","fmode=777"] }

  config.vm.define "windows7" do |windows7|
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = "2048"
  end

  # Port forward WinRM and RDP (changed values to NOT conflict with host)
  config.vm.network :forwarded_port, guest: 3389, host: 3391
  config.vm.network :forwarded_port, guest: 5985, host: 5987, id: "winrm", auto_correct: true

end

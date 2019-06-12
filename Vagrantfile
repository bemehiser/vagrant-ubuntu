Vagrant.configure('2') do |config|
  # set the version of Ubuntu
  config.vm.box = 'ubuntu/bionic64'

  # Mount local folders to virtual machine path
  config.vm.synced_folder '.', '/vagrant'
  config.vm.synced_folder '~/Projects', '/Projects' # , type: 'nfs' # nfs gives errors on arm

  # Create virtual network interface and give this machine a static ipv4 address.
  # Note: This must not conflict with the existing address of your router
  config.vm.network 'private_network', ip: '172.0.0.2'
  # config.vm.network 'private_network', ip: '192.0.0.2'
  # config.vm.network 'private_network', ip: '10.0.0.2'

  # Allocate resources for your virtual machine.
  config.vm.provider 'virtualbox' do |vb|
    vb.linked_clone = true
    vb.memory = 4096
    vb.cpus = 4
  end

  config.vm.provision 'shell', path: 'provision.sh'
end

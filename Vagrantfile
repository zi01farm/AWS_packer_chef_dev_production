required_plugins = %w( vagrant-hostsupdater vagrant-berkshelf )
required_plugins.each do |plugin|
  exec "vagrant plugin install #{plugin};vagrant #{ARGV.join(" ")}" unless Vagrant.has_plugin? plugin || ARGV[0] == 'plugin'
end
Vagrant.configure("2") do |config|
    config.omnibus.chef_version = :latest
    config.vm.define "app" do |app|
      app.vm.box = "ubuntu/xenial64"
      app.vm.network "private_network", ip: "192.168.10.100"
      app.hostsupdater.aliases = ["development.local"]
      app.vm.synced_folder "py_app", "/home/ubuntu/app"

      app.vm.provision "chef_solo" do |chef|
        chef.arguments = "--chef-license accept"
        chef.cookbooks_path = ["cookbooks"]
        chef.add_recipe "python_cookbook::default"
      end
    end
end

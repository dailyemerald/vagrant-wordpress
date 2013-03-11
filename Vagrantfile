#!/usr/bin/env ruby

Vagrant::Config.run do |config|
  config.vm.box = "base"
  
  config.vm.forward_port 80, 8080, :auto => true
  config.vm.forward_port 3306, 3306, :auto => true

  config.vm.share_folder "wp-themes", "/var/www/wordpress/wp-content/themes", "./themes"
  config.vm.share_folder "wp-root", "/var/www/wordpress", "./wp-root"

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe("apt")
    chef.add_recipe("build-essential")
    chef.add_recipe("wordpress")

    chef.json.merge!(
      "mysql" => {
        "allow_remote_root"    => true,
        "server_root_password" => "helloworld",
        "server_debian_password" => "helloworld", 
        "server_repl_password" => "helloworld"
      },

      "wordpress" => {
        "db" => {
          "database" => "wordpress",
          "user"     => "wordpress",
          "password" => "wordpress"
        }
      }
    )

  end
end
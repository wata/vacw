# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box  = 'chef/centos-6.6'
  config.ssh.forward_agent = true
  config.vm.box_check_update = true
  config.vm.network 'private_network', ip: '192.168.33.10'
  config.vm.hostname = 'wordpress.local'
  config.vm.synced_folder '.', '/vagrant', :mount_options => ['dmode=755', 'fmode=644']
  config.vm.synced_folder 'srv/wordpress', '/srv/wordpress', :create => 'true', :mount_options => ['dmode=755', 'fmode=644']

  if Vagrant.has_plugin?('vagrant-multiplug')
    config.plugin.add_dependency 'vagrant-hostsupdater'
    config.plugin.add_dependency 'vagrant-vbguest'
  end

  if Vagrant.has_plugin?('vagrant-hostsupdater')
    config.hostsupdater.remove_on_suspend = true
  end

  if Vagrant.has_plugin?('vagrant-vbguest')
    config.vbguest.auto_update = false
  end

  config.vm.provider :virtualbox do |vb|
    vb.memory = 512
    vb.cpus = 1
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'provisioning/site.yml'
    ansible.extra_vars = {
      # ntp
      ntp_server: 'ntp.nict.jp',

      # wordpress
      wp_version: '4.2.2-ja',
      wp_user: 'vagrant',
      wp_db_name: 'wordpress',
      wp_db_user: 'wordpress',
      wp_db_password: 'wordpress',
      wp_db_prefix: 'local',
      auto_up_disable: 'false',
      core_update_level: 'false',

      # nginx
      nginx_server_name: 'wordpress.local',
      nginx_htpasswd_name: 'admin',
      nginx_htpasswd_password: 'password',

      # mysql
      mysql_port: 3306,

      rbenv: {
        env: 'system',
        version: 'v0.4.0',
        ruby_version: '2.2.2'
      }
    }
  end
end

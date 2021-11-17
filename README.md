# my bootstraps

<p align="center">
  <img src="lib/logo.jpeg" width="240" height="120" />
</p>


Setting up new systems takes time. Here are my bootstraps and ansible playbooks to speed things up.

---

## Set-up
1. ```git clone git@github.com:shaungarwood/my_bootstraps.git```
2. ```cd my_bootstraps && bash bin/initial_bootstrap.sh```
3. ```ansible-playbook tasks/zsh.yml tasks/vim.yml``` Run any playbooks necessary, or ```all.yml```

## Full Vagrant Demo
```
Vagrant.configure("2") do |config|
  $script = <<-SCRIPT
  wget shaungarwood.com/bs.sh
  bash bs.sh
  ansible-playbook ~/my_bootstraps/tasks/basic.yml
  SCRIPT

  config.vm.provision "shell", inline: $script, privileged: false

  config.vm.define "centos" do |centos|
    centos.vm.box = "bento/centos-7.2"
    centos.vm.hostname = "centos"
  end

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "bento/ubuntu-18.04"
    ubuntu.vm.hostname = "ubuntu"
  end
end
```

test
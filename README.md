# my bootstraps

<p align="center">
  <img src="lib/logo.jpeg" width="240" height="120" />
</p>


Setting up new systems takes time. Here are my bootstraps and ansible playbooks to speed things up.

---

## Set-up
1. ```git clone git@github.com:shaungarwood/my_bootstraps.git```
2. ```bash my_bootstraps/bin/initial_bootstrap.sh```
3. ```ansible-playbook tasks/zsh.yml tasks/vim.yml``` Run any playbooks necessary, or ```*.yml```

## Full Vagrant Demo
```
Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "wget https://raw.githubusercontent.com/shaungarwood/my_bootstraps/master/bin/initial-bootstrap.sh"
  config.vm.provision "shell", inline: "bash initial-bootstrap.sh"
  config.vm.provision "shell", inline: "ansible-playbook ~/my_bootstraps/tasks/*.yml"


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

## to-do
```
- pyenv
  > get latest stable?
- zsh
  > plugins:
    - vim prompt
    - mkvenv
    - pyenv
- personal bin dir (PATH in bash/zsh?)
- ruby/rvm/pry setup

https://github.com/pyenv/pyenv/wiki/common-build-problems
^ use this for pre-reqs for pyenv

thoughts:
- i think ansible can detect if it's a virtual env. could use to customize zsh prompt.
- customize zsh prompt based on username (csw/sgarwood/vagrant)
```

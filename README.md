# my bootstraps

<p align="center">
  <img src="lib/logo.jpeg" width="240" height="120" />
</p>


Setting up new systems takes time. Here are my bootstraps and ansible playbooks to speed things up.

---

## Set-up
1. ```git clone git@github.com:shaungarwood/my_bootstraps.git```
2. ```bash my_bootstraps/bin/initial_bootstrap.sh```
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

## to-do
```
- zsh
  > plugins:
    - mkvenv
    - pyenv
- personal bin dir (PATH in bash/zsh?)
- customize pyenv role

https://github.com/pyenv/pyenv/wiki/common-build-problems
^ use this for pre-reqs for pyenv

https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html
^ break apart some of my playbooks into roles
use a top-level playbook like "coding" or "work" to apply all the roles to whatever machine

lots of things going on:
- install zsh plugin manager (antibody or antigen) to get plugins going
  - this would mean getting mkvenv going
  - https://getantibody.github.io/    # <-- try this out in VM first
- i really want to check out vim plugins, that site was sweet
- re-org things into roles, so i can run a single playbook for "coding" or "work"
- customize the pyenv role

thoughts:
- i think ansible can detect if it's a virtual env. could use to customize zsh prompt.
- customize zsh prompt based on username (csw/sgarwood/vagrant)
```

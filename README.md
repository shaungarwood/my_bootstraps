# my bootstraps

<p align="center">
  <img src="lib/logo.jpeg" width="240" height="120" />
</p>


Setting up new systems takes time. Here are my bootstraps and ansible playbooks to speed things up.

---

## Set-up
1. ```git clone git@github.com:shaungarwood/my_bootstraps.git```
2. ```bash my_bootstraps/bin/initial_bootstrap.sh```
3. ```ansible-playbook common_cli.yml zsh.yml vim.yml``` Run any playbooks necessary, or ```*.yml```

## to-do
```
- pyenv
  > get latest stable?
- zsh
  > plugins:
    - vim prompt
    - mkvenv
    - pyenv
- aliases
- personal bin dir (PATH in bash/zsh?)
- add extract function below (zsh?)
- fix zsh on centos, still not taking new shell
```

```
extract () {
   if [ -f $1 ] ; then
       case $1 in
           *.tar.bz2)   tar xvjf $1;;
           *.tar.gz)    tar xvzf $1;;
           *.bz2)       bunzip2 $1 ;;
           *.rar)       unrar x $1 ;;
           *.gz)        gunzip $1  ;;
           *.tar)       tar xvf $1 ;;
           *.tbz2)      tar xvjf $1;;
           *.tgz)       tar xvzf $1;;
           *.zip)       unzip $1   ;;
           *.Z)         uncompress $1  ;;
           *.7z)        7z x $1;;
           *) echo "don't know how to extract '$1'..." ;;
       esac
   else
       echo "'$1' is not a valid file!"
   fi
}
```

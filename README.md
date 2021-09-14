# Installation VPS avec Ansible

L'utilisation d'Ansible va permettre automatiquement de :
- mettre à jour les paquets
- créer un user (sudo) avec le username / password passés en extra vars
- installer vim, git, rsync, fail2ban, make, docker
- configurer le firewall

## Prérequis
Mettre à jour le fichier *hosts* du projet avec la liste des ip des serveurs à installer
```
[web]
ip_server_1
ip_server_2
```

L'utilisateur **root** doit pouvoir se connecter en SSH sur le VPS.   
Si ce n'est pas le cas:
- décommenter la ligne **PermitRootLogin yes** dans */etc/ssh/sshd_config*
- mettre à jour le mode de passe **root** avec `sudo passwd root`

## Installation

```
export ANSIBLE_HOST_KEY_CHECKING=False

ansible-playbook install.yml -i hosts --user root --ask-pass --extra-vars "username=XXX password=XXX"
```
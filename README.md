# Setup Local Environment with Ansible

Configure ssh. Before execute ansible, put result of `vagrant ssh-config` to `~/.ssh/config` like this.

```bash
Host hogehogecentos-6.6
  HostName 127.0.0.1
  User vagrant
  Port 2272
  UserKnownHostsFile /dev/null
  StrictHostKeyChecking no
  PasswordAuthentication no
  IdentityFile /home/takamario/hogehoge-vagrant-box-centos-6.6/.vagrant/machines/default/virtualbox/private_key
  IdentitiesOnly yes
  LogLevel FATAL
```

Install pip. (Need `sudo` when use system python)

```bash
curl https://bootstrap.pypa.io/get-pip.py | python
```

Install Ansible.  (Need `sudo` when use system python)

```bash
pip intall ansible
```

Run all roles. If you want to specify the role, `--tags` will help.

```bash
# Run all roles
ansible-playbook -i local-centos-6.6 local-centos-6.6-playbook.yml

# Run only "nginx" role with tag
ansible-playbook -i local-centos-6.6 local-centos-6.6-playbook.yml --tags nginx
```

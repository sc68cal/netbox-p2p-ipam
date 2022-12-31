### Quickstart

This repo contains a `Vagrantfile` that builds a virtual machine,
that will contain both [containerlab][cl] and [NetBox][nb].

Once the provisioning is complete, you can `vagrant ssh` into the
machine and run Ansible, by doing the following:

```shell
$ python -m venv ~/ansible-venv
$ source ~/ansible-venv/bin/activate
$ cd /vagrant
$ pip install -r requirements.txt
$ ansible-galaxy install -r requirements.yml
$ ansible-playbook site.yml
```

[cl]: https://containerlab.dev

[nb]: https://readthedocs.org/projects/netbox/

# Vantage SSH Role


> `ssh` is an [ansible](http://www.ansible.com) role which:
>
> * installs openssh (client/server)
> * configures ssh
> * adds known_hosts (Coming Soon if I need it)
> * configures ssh server

## Installation


Using `git`:

```
$ git 
```

## Dependencies

* Ansible 1.9

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```

# what ports, IPs and protocols we listen for
ssh_port: [22]
ssh_protocol: 2
ssh_listen_address: []
# authentication
ssh_permit_root_login: 'yes'
ssh_pubkey_authentication: 'yes'
ssh_password_authentication: 'yes'
# start on boot
ssh_service_enabled: yes
# current state: started, stopped
ssh_service_state: started
# system wide known hosts
ssh_known_hosts: []
```

## Handlers

These are the handlers that are defined in `handlers/main.yml`.

* `restart ssh`

## Example playbook

```
- host: all
  sudo: yes
  roles:
    - vantage-ssh
  vars:
    ssh_port:
      - 22
    ssh_permit_root_login: 'no'
    ssh_pubkey_authentication: 'yes'
    ssh_password_authentication: 'yes'
```

## Testing

```
$ git clone https://github.com/weareinteractive/ansible-ssh.git
$ cd ansible-ssh
$ vagrant up
```

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests and examples for any new or changed functionality.

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License
Copyright (c) We Are Interactive under the MIT license.

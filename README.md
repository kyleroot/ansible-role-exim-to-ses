# exim-to-ses

Installs and configures Exim to act as an SMTP relay to an [AWS SES](http://docs.aws.amazon.com/ses/latest/DeveloperGuide/smtp-connect.html) SMTP endpoint for RHEL 6 compatible hosts.

## Requirements

None.

## Role Variables

Available variables are listed below.

* `aws_region`
* `aws_ses_username` 
* `aws_ses_password` 
* `relay_from_hosts` 

`aws_region` and `relay_from_hosts` will both receive default values if they are left undefined. `aws_ses_username` and `aws_ses_password` must have values explicitly defined.

### relay_from_hosts

`relay_from_hosts` should contain the value you want the Exim `relay_from_hosts` configuration directive to ultimately have. Below is a one-line snippet from an `exim.conf` showing the Exim `relay_from_hosts` configuration directive. In this example the Ansible variable `relay_from_hosts` had been set to `localhost : 192.168.1.0/24` when the role was run.

    hostlist   relay_from_hosts = localhost : 192.168.1.0/24

If the Ansible variable `relay_from_hosts` is left unset, the role will use the CIDR representation of the subnet of the default network interface.

### aws_region

`aws_region` Has a default value of `us-east-1`.

## Dependencies

`goozbach.EPEL` [GitHub](https://github.com/goozbach-ansible/role-epel) or [Ansible Galaxy](https://galaxy.ansible.com/detail#/role/35)

Example Playbook
----------------

    - hosts: servers
      become: yes
      roles:
         - { role: kyleroot.exim-to-ses, aws_ses_username: AKIA..., aws_ses_password:  AnpZ...}

## License

MIT

## Author Information

[Kyle Root](https://www.kylert.com).

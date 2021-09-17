# Ansible Role: base_nettime

Installs [Chrony](https://chrony.tuxfamily.org/) for NTP time synchronization with servers and peers.
Uses keys for peer authentication.

## Requirements/Cautions
Centos 7+8 and/or Debian 10.

**NOTE**: firewalld or ufw will be installed if not present.

## Dependencies

Ansible, no role dependencies, not python dependencies.

## Role variables
`ntp_zone: .nl`
Best results are attained when using a local zone. NTP is served by a pool of
servers. `ntp_zone` is used in defaults/main.yml only.


[https://www.ntppool.org/zone/europe](https://www.ntppool.org/zone/europe)

### NTP time servers that you want to subscribe to:
`ntp_servers:`

### NTP time peers that you want to sync:
`ntp_peers:`

### Allow access from these subnets:
```
net_allow:
  - '192.168.0.0/16'
```
### deny access from these subnets:
net_deny: []

### unique integer to lookup key for peer authentication:
nettime_keyid: 123


## Example playbook

```yaml
---
- hosts: all
  roles:
    - role: base_nettime
```

## License

MIT

## Reference:
  - [https://chrony.tuxfamily.org/](https://chrony.tuxfamily.org/)

## Author information

This role was created by Bas Meijer

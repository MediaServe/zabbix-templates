# LVM Zabbix thin provisioned pool and volume discovery

## Rationale

With this Zabbix template you can use auto discovery and monitoring of LVM volume groups, volumes and thin provisioning pools. By default
Zabbix will monitor only mounted file-systems and in case of thin provisioning you will not detect the pool lacking free disk space.

## Installation

1. On the LVM host make sure that lvm2 and jq are installed and the commands lvs and vgs are executable.
1. Import the file zbx_zlvm_template.xml as template in the Zabbix server.
1. Add the file userparameter_lvm.conf to the Zabbix agent on the LVM host.
1. Add sudo rules in accordance with the file sudoers-zabbix on the LVM host.
1. Safe the file zlvm to /usr/local/bin/ on the LVM host and make sure that it is executable.
1. Restart any services if necessary, then add the template to the host in the Zabbix configuration.

## Notes

LVS does not give an exact usage in bytes on a thin provisioned pool. Instead it gives us a percentage that the template will use to
calculate the usage, based on the total pool size.

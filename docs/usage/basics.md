# SRL Basics

## Default Configuration

SR Linux stores configuration in `/etc/opt/srlinux/config.json`

If there is no configuration file present at boot, a basic configuration file is auto-generated with the following contents:

* Creation of a mgmt network instance
* Mgmt interface is added to the mgmt network instance
* DHCP v4/v6 is enabled on mgmt interface
* A set of default of logs are created, most in memory – one catch all in a file called messages
* SSH server is enabled


## Configuration Modes

SR Linux has three configuration modes:

1. `running`
2. `candidate`
3. `state`

To move between modes use the keyword `enter` before the desired mode.


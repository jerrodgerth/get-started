# Setup BGP

This page will provide cut-and-paste commands to configure iBGP between two SR Linux nodes.

Connect to the SR Linux instances via `docker exec` or `ssh admin@<IPv4 Address>`

### Configure BGP on `clab-srl02-srl1`

```
# enter candidate datastore
enter candidate

# configure BGP
set / network-instance default protocols bgp admin-state enable
set / network-instance default protocols bgp router-id 10.0.0.1
set / network-instance default protocols bgp autonomous-system 65001
set / network-instance default protocols bgp group ibgp ipv4-unicast admin-state enable
set / network-instance default protocols bgp group ibgp export-policy export-lo
set / network-instance default protocols bgp neighbor 192.168.0.1 admin-state enable
set / network-instance default protocols bgp neighbor 192.168.0.1 peer-group ibgp
set / network-instance default protocols bgp neighbor 192.168.0.1 peer-as 65001

# create export policy
set / routing-policy policy export-lo statement 10 match protocol local
set / routing-policy policy export-lo statement 10 action accept

# commit config
commit now
```

### Configure BGP on `clab-srl02-srl2`

```
# enter candidate datastore
enter candidate

# configure BGP
set / network-instance default protocols bgp admin-state enable
set / network-instance default protocols bgp router-id 10.0.0.2
set / network-instance default protocols bgp autonomous-system 65001
set / network-instance default protocols bgp group ibgp ipv4-unicast admin-state enable
set / network-instance default protocols bgp group ibgp export-policy export-lo
set / network-instance default protocols bgp neighbor 192.168.0.0 admin-state enable
set / network-instance default protocols bgp neighbor 192.168.0.0 peer-group ibgp
set / network-instance default protocols bgp neighbor 192.168.0.0 peer-as 65001

# create export policy
set / routing-policy policy export-lo statement 10 match protocol local
set / routing-policy policy export-lo statement 10 action accept

# commit config
commit now
```

### Verify BGP Session

```
A:srl2# show network-instance default protocols bgp neighbor 192.168.0.0
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
BGP neighbor summary for network-instance "default"
Flags: S static, D dynamic, L discovered by LLDP, B BFD enabled, - disabled, * slow
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+---------------------+------------------------------+---------------------+-------+-----------+-----------------+-----------------+---------------+------------------------------+
|      Net-Inst       |             Peer             |        Group        | Flags |  Peer-AS  |      State      |     Uptime      |   AFI/SAFI    |        [Rx/Active/Tx]        |
+=====================+==============================+=====================+=======+===========+=================+=================+===============+==============================+
| default             | 192.168.0.0                  | ibgp                | S     | 65001     | established     | 0d:0h:9m:13s    | ipv4-unicast  | [1/0/1]                      |
+---------------------+------------------------------+---------------------+-------+-----------+-----------------+-----------------+---------------+------------------------------+
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Summary:
1 configured neighbors, 1 configured sessions are established,0 disabled peers
0 dynamic peers
```

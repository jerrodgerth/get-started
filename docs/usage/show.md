# SR Linux `show` commands

#### show version

```
A:srlinux-dut1# show version
----------------------------------------------------------------------
Hostname          : srlinux-dut1
Chassis Type      : 7220 IXR-D3
Part Number       : Sim Part No.
Serial Number     : Sim Serial No.
System MAC Address: 02:34:0B:FF:00:00
Software Version  : v21.3.1
Build Number      : 410-g75939dc880
Architecture      : x86_64
Last Booted       : 2021-05-19T23:46:19.399Z
Total Memory      : 7980972 kB
Free Memory       : 4250925 kB
----------------------------------------------------------------------
```

#### show platform environment

```
A:srlinux-dut1# show platform environment
  +--------------+----+-------------+-------------------+------------------------------+-------------+
  | Module Type  | ID | Admin State | Operational State |            Model             | Temperature |
  +==============+====+=============+===================+==============================+=============+
  | control      | A  | N/A         | up                | imm2-10g-sfpp+32-100g-qsfp28 | 50          |
  | linecard     | 1  | N/A         | empty             |                              | 0           |
  | fan-tray     | 1  | N/A         | empty             |                              | 0           |
  | fan-tray     | 2  | N/A         | empty             |                              | 0           |
  | fan-tray     | 3  | N/A         | empty             |                              | 0           |
  | fan-tray     | 4  | N/A         | empty             |                              | 0           |
  | fan-tray     | 5  | N/A         | empty             |                              | 0           |
  | power-supply | 1  | N/A         | empty             |                              |             |
  | power-supply | 2  | N/A         | empty             |                              |             |
  +--------------+----+-------------+-------------------+------------------------------+-------------+
```

#### show system applications

```
A:srlinux-dut1# show system application
  +-------------------+------+--------------------+------------------------------------+--------------------------+
  |       Name        | PID  |       State        |              Version               |       Last Change        |
  +===================+======+====================+====================================+==========================+
  | aaa_mgr           | 952  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.066Z |
  | acl_mgr           | 961  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.066Z |
  | app_mgr           | 901  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.310Z |
  | arp_nd_mgr        | 970  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.067Z |
  | bfd_mgr           |      | waiting-for-config |                                    |                          |
  | bgp_mgr           |      | waiting-for-config |                                    |                          |
  | chassis_mgr       | 979  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.067Z |
  | dev_mgr           | 925  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:14.236Z |
  | dhcp_client_mgr   | 988  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.068Z |
  | dhcp_relay_mgr    |      | waiting-for-config |                                    |                          |
  | evpn_mgr          | 1000 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:15.010Z |
  | fib_mgr           | 1010 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.068Z |
  | gnmi_server       | 1240 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:18.173Z |
  | idb_server        | 943  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:14.563Z |
  | isis_mgr          |      | waiting-for-config |                                    |                          |
  | json_rpc          | 1241 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:18.162Z |
  | l2_mac_learn_mgr  | 1021 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.069Z |
  | l2_mac_mgr        | 1032 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.070Z |
  | l2_static_mac_mgr |      | waiting-for-config |                                    |                          |
  | label_mgr         |      | waiting-for-config |                                    |                          |
  | lag_mgr           | 1046 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.070Z |
  | ldp_mgr           |      | waiting-for-config |                                    |                          |
  | linux_mgr         | 1055 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.071Z |
  | lldp_mgr          |      | waiting-for-config |                                    |                          |
  | log_mgr           | 1064 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.072Z |
  | mcid_mgr          | 1073 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.072Z |
  | mgmt_server       | 1082 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.073Z |
  | mpls_mgr          |      | waiting-for-config |                                    |                          |
  | net_inst_mgr      | 1092 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.074Z |
  | oam_mgr           |      | waiting-for-config |                                    |                          |
  | ospf_mgr          |      | waiting-for-config |                                    |                          |
  | plcy_mgr          |      | waiting-for-config |                                    |                          |
  | qos_mgr           | 1237 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:18.026Z |
  | sdk_mgr           | 1102 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.075Z |
  | sflow_sample_mgr  | 1115 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:15.807Z |
  | sshd-mgmt         | 1388 | running            | OpenSSH_7.4p1, OpenSSL 1.0.2k-fips | 2021-05-19T23:17:23.923Z |
  | static_route_mgr  |      | waiting-for-config |                                    |                          |
  | supportd          | 910  | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:13.900Z |
  | vrrp_mgr          |      | waiting-for-config |                                    |                          |
  | vxlan_mgr         |      | waiting-for-config |                                    |                          |
  | xdp_cpm           | 1131 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.076Z |
  | xdp_lc_1          | 1142 | running            | v21.3.1-410-g75939dc880            | 2021-05-19T23:17:16.077Z |
  +-------------------+------+--------------------+------------------------------------+--------------------------+
```

#### show interface brief

```
A:srlinux-dut1# show interface brief
+---------------------+-----------------------------------+-----------------------------------+-----------------------------------+-----------------------------------+
|        Port         |            Admin State            |            Oper State             |               Speed               |               Type                |
+=====================+===================================+===================================+===================================+===================================+
| ethernet-1/1        | disable                           | down                              | 10G                               |                                   |
| ethernet-1/2        | disable                           | down                              | 10G                               |                                   |
| ethernet-1/3        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/4        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/5        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/6        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/7        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/8        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/9        | disable                           | down                              | 100G                              |                                   |
| ethernet-1/10       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/11       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/12       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/13       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/14       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/15       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/16       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/17       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/18       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/19       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/20       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/21       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/22       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/23       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/24       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/25       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/26       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/27       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/28       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/29       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/30       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/31       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/32       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/33       | disable                           | down                              | 100G                              |                                   |
| ethernet-1/34       | disable                           | down                              | 100G                              |                                   |
| mgmt0               | enable                            | up                                | 1G                                |                                   |
+---------------------+-----------------------------------+-----------------------------------+-----------------------------------+-----------------------------------+
```

#### show interface mgmt0

```
A:srlinux-dut1# show interface mgmt0
======================================================================
mgmt0 is up, speed 1G, type None
  mgmt0.0 is up
    Network-instance: mgmt
    Encapsulation   : null
    Type            : None
    IPv4 addr    : 172.22.0.2/16 (dhcp, preferred)
    IPv6 addr    : fe80::42:acff:fe16:2/64 (link-layer, preferred)
----------------------------------------------------------------------
======================================================================
```

#### show network-instance mgmt summary

```
A:srlinux-dut1# show network-instance mgmt summary
+---------------------------------+-----------------+-----------------+-----------------+---------------------------------+-----------------------------------------+
|              Name               |      Type       |   Admin state   |   Oper state    |            Router id            |               Description               |
+=================================+=================+=================+=================+=================================+=========================================+
| mgmt                            | ip-vrf          | enable          | up              |                                 | Management network instance             |
+---------------------------------+-----------------+-----------------+-----------------+---------------------------------+-----------------------------------------+
```

#### show network-instance mgmt route-table all

```
A:srlinux-dut1# show network-instance mgmt route-table all
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
IPv4 Unicast route table of network instance mgmt
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
+----------------------------------+-------+------------+-----------------+---------+-------+----------------------------------------------+---------------------+
|              Prefix              |  ID   |   Active   |      Owner      | Metric  | Pref  |               Next-hop (Type)                | Next-hop Interface  |
+==================================+=======+============+=================+=========+=======+==============================================+=====================+
| 0.0.0.0/0                        | 0     | true       | dhcp            | 0       | 5     | 172.22.0.1 (direct)                          | mgmt0.0             |
| 172.22.0.0/16                    | 0     | true       | local           | 0       | 0     | 172.22.0.2 (direct)                          | mgmt0.0             |
| 172.22.0.0/16                    | 1     | false      | linux           | 0       | 5     | 172.22.0.0 (direct)                          | mgmt0.0             |
| 172.22.0.2/32                    | 0     | true       | host            | 0       | 0     | None (extract)                               | None                |
| 172.22.255.255/32                | 0     | true       | host            | 0       | 0     | None (broadcast)                             | None                |
+----------------------------------+-------+------------+-----------------+---------+-------+----------------------------------------------+---------------------+
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
5 IPv4 routes total
4 IPv4 prefixes with active routes
0 IPv4 prefixes with active ECMP routes
-------------------------------------------------------------------------------------------------------------------------------------------------------------------
```

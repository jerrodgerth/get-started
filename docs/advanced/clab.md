# Using Containerlab

For any serious testing of SR Linux, more than one instance will be required.
[ContainerLab](https://containerlab.srlinux.dev/) is a multi-vendor tool developed to make building networking labs using Docker containers simple and fast.
This example will use Containerlab to two SR Linux nodes connected back-to-back.
The [next section](bgp.md) will provide the steps necessary to configure BGP for this network.

## Install Containerlab

Containerlab has the same basic requirements described in the [Overview](../index.md).

The easiest way to install Containerlab is by downloading and executing the installation script.
If you require other installation methods, consult the Containerlab [Install](https://containerlab.srlinux.dev/install/) page.


=== "curl"
    ```
    bash -c "$(curl -sL https://get-clab.srlinux.dev)"
    ```
=== "wget"
    ```
    bash -c "$(wget -qO - https://get-clab.srlinux.dev)"
    ```

## Setup 2-node topology

For this example, the [Two SR Linux Nodes](https://containerlab.srlinux.dev/lab-examples/two-srls/) topology will be used.
Visit the Containerlab site for detailed information about this topology and to view other example labs.

Begin by creating a working directory

```shell
mkdir -p my-clabs && cd my-clabs
```

Copy the topology file to this directory

```shell
cp -a /etc/containerlab/lab-examples/srl02/* .
```

Change the `image` name in `srl02.clab.yml` to match the SR Linux image in the local repository

```yaml
# topology documentation: http://containerlab.srlinux.dev/lab-examples/two-srls/
name: srl02

topology:
  kinds:
    srl:
      type: ixr6
      image: srlinux:21.3.1-410
      license: license.key
  nodes:
    srl1:
      kind: srl
      config: srl1.cfg.json
    srl2:
      kind: srl
      config: srl2.cfg.json

  links:
    - endpoints: ["srl1:e1-1", "srl2:e1-1"]
```

!!! note
    For Containerlab v0.14.1 it is still necessary to have the license file in the same directory as the topology file.
    This requirement will be lifted in a future release.


## Deploy topology

Deploy the topology using `sudo` if you are not logged in as `root`.

```shell
sudo clab deploy -t srl02.clab.yml
```

Output if successful:

```shell
INFO[0000] Parsing & checking topology file: srl02.clab.yml
INFO[0000] Creating lab directory: /home/jgerth/srl-labs/clab-srl02
INFO[0000] Creating root CA
INFO[0000] Creating container: srl1
INFO[0001] Creating container: srl2
INFO[0002] Creating virtual wire: srl1:e1-1 <--> srl2:e1-1
INFO[0002] Writing /etc/hosts file
+---+-----------------+--------------+--------------------+------+-------+---------+----------------+----------------------+
| # |      Name       | Container ID |       Image        | Kind | Group |  State  |  IPv4 Address  |     IPv6 Address     |
+---+-----------------+--------------+--------------------+------+-------+---------+----------------+----------------------+
| 1 | clab-srl02-srl1 | b7fbad707e11 | srlinux:21.3.1-410 | srl  |       | running | 172.20.20.7/24 | 2001:172:20:20::7/64 |
| 2 | clab-srl02-srl2 | b2598a632eca | srlinux:21.3.1-410 | srl  |       | running | 172.20.20.8/24 | 2001:172:20:20::8/64 |
+---+-----------------+--------------+--------------------+------+-------+---------+----------------+----------------------+
```

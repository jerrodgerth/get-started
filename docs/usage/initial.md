# Initial Configuration

Here are a few initial configuration tasks.
This is not an exhaustive list but meant as examples suitable for getting to know SR Linux on a single instance.

Configuration steps:

* Begin configuration with `enter candidate`
* Use `commit stay` or `commit now` to save the changes
* Use `diff` to view changes since last commit


### Set host-name & domain-name

```
set / system name host-name srlinux-dut1
set / system name domain-name example.com
```

### Define a DNS server

```
set / system dns network-instance mgmt server-list [ 1.1.1.1 1.1.1.3 ]
```

### Set timezone

```
set / system clock timezone UTC
```

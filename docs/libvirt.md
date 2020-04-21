Create a storage pool. Sample configuration:
```xml
<pool type='dir'>
  <name>default</name>
  <target>
    <path>/var/lib/libvirt/images</path>
  </target>
</pool>
```

```
$ virsh pool-create pool.xml
```

Here is a sample libvirt network configuration. It instructs libvirt to not provide DNS and DHCP servers for this network. Instead, DNS and DHCP servers for this network will be provided by *openshift-auto-upi*.

```xml
<network>
  <name>default</name>
  <forward mode='nat'>
    <nat>
      <port start='1024' end='65535'/>
    </nat>
  </forward>
  <bridge name='default' stp='on' delay='0'/>
  <dns enable='no'/>
  <ip address='192.168.150.1' netmask='255.255.255.0'>
  </ip>
</network>
```
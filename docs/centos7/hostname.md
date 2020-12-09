# centos 7 hostname

## 3 types hostnames

* static hostname

```bash
cat /etc/hostname

    kk101.kk
```

* pretty hostname

```bash
cat /etc/machine-info
```

* transient hostname

```bash
  # in Linux kernel
  # dynamic, will be lost after a reboot
```

## change hostname

* check existing hostname

```bash
hostnamectl

  Static hostname: localhost.localdomain
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 9394751b492444bba926a140aa200688
           Boot ID: 6e6731bfe85a45ebb7360e56fb7b59fe
  Operating System: CentOS Linux 7 (Core)
       CPE OS Name: cpe:/o:centos:centos:7
            Kernel: Linux 3.10.0-1062.el7.x86_64
      Architecture: x86-64
```

* set a new static hostname

```base
hostnamectl set-hostname kk101.kk
```

* check hostname again

```bash
hostnamectl

   Static hostname: kk101.kk
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: 9394751b492444bba926a140aa200688
           Boot ID: 6e6731bfe85a45ebb7360e56fb7b59fe
  Operating System: CentOS Linux 7 (Core)
       CPE OS Name: cpe:/o:centos:centos:7
            Kernel: Linux 3.10.0-1062.el7.x86_64
      Architecture: x86-64
```

## reference

* <https://phoenixnap.com/kb/how-to-set-or-change-a-hostname-in-centos-7>

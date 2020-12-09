# samba in centos 7

## start

```doc
组成Samba运行的有两个服务，一个是SMB，另一个是NMB；SMB是Samba 的核心启动服务，主要负责建立 Linux Samba服务器与Samba客户机之间的对话， 验证用户身份并提供对文件和打印系统的访问，只有SMB服务启动，才能实现文件的共享，监听139 TCP端口；而NMB服务是负责解析用的，类似与DNS实现的功能，NMB可以把Linux系统共享的工作组名称与其IP对应起来，如果NMB服务没有启动，就只能通过IP来访问共享文件，监听137和138 UDP端口。
```

## install samba in centos

```bash
sudo yum install samba samba-client
```

## start smb and nmb

```bash
sudo systemctl start smb
sudo systemctl start nmb

sudo systemctl enable smb
sudo systemctl enable nmb
```

## Configuring Firewall

```bash
firewall-cmd --permanent --zone=public --add-service=samba
firewall-cmd --zone=public --add-service=samba
```

## Creating Samba Users and Directory Structure

```bash
sudo mkdir /home/samba

#Create a new group named sambashare
sudo groupadd sambashare

#Set the /samba directory group ownership to sambashare
sudo chgrp sambashare /home/samba

```

## Creating Samba Users

```bash
sudo useradd -M -d /home/samba/kksmb -s /usr/sbin/nologin -G sambashare kksmb

# The useradd options have the following meanings:

#     -M -do not create the user’s home directory. We’ll manually create this directory.
#     -d /samba/josh - set the user’s home directory to /samba/josh.
#     -s /usr/sbin/nologin - disable shell access for this user.
#     -G sambashare - add the user to the sambashare group.

sudo mkdir /home/samba/kksmb
sudo chown kksmb:sambashare /home/samba/kksmb

sudo chmod 2770 /home/samba/kksmb

sudo smbpasswd -a kksmb

sudo smbpasswd -e kksmb

```

## create a user and group sadmin

```bash
sudo useradd -M -d /home/samba/users -s /usr/sbin/nologin -G sambashare sadmin

sudo smbpasswd -a sadmin
sudo smbpasswd -e sadmin

sudo mkdir /home/samba/users

sudo chown sadmin:sambashare /home/samba/users
sudo chmod 2770 /home/samba/users

```

## configuring samba shares

```bash
sudo vim /etc/samba/smb.conf
```

```ini
[users]
    path = /home/samba/users
    browseable = yes
    read only = no
    force create mode = 0660
    force directory mode = 2770
    valid users = @sambashare @sadmin

[kksmb]
    path = /home/samba/kksmb
    browseable = no
    read only = no
    force create mode = 0660
    force directory mode = 2770
    valid users = kksmb @sadmin
```

## restart smb nmb

```bash
sudo systemctl restart smb.service
sudo systemctl restart nmb.service
```

## reference

* <https://linuxize.com/post/how-to-install-and-configure-samba-on-centos-7/>

# ubuntu user

```bash
# add user
useradd ubuntu

mkdir /home/ubuntu

chown -R ubuntu:ubuntu

#sudoer

vi /etc/sudoer

#加到最后，否则可能不生效
username     ALL=(ALL) NOPASSWD:ALL

#修改默认终端

cat /etc/shells

chsh
```

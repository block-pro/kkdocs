# iptables in action

## close centos 7 firewalld

```bash
sudo systemctl stop firewalld
sudo systemctl disable firewalld
```

## start centos 7 iptables service

```bash
sudo yum install iptables-service
sudo systemctl start iptables.service
sudo systemctl enable iptables.service
```

## clear centos 7 iptables default rules

```bash
sudo iptables -nvL
sudo iptables -F
sudo service iptables save
```

## table

* nat
* filter
* mangle

## Chains Policy

```bash
iptables -t nat -nvL

iptables --policy INPUT ACCEPT
```

## dnat

```bash
iptables -t nat -A vserver -p tcp -m tcp --dport 10022 -j DNAT --to-destination 192.168.123.101:22
```

## firewalld

* status firewalld

```bash
sudo systemctl status firewalld
```

* list-all

```bash
sudo firewall-cmd --list-all
```

* add-service

```bash
sudo firewall-cmd --add-service http
```

## reference

* <https://www.howtogeek.com/177621/the-beginners-guide-to-iptables-the-linux-firewall/>

# iptables

## new clash


```bash

dest=1.1.1.1

iptables -t nat -N CLASH # 新建一个名为 CLASH 的链
  
iptables -t nat -A CLASH -d $dest -j RETURN # 

iptables -t nat -A CLASH -d 0.0.0.0/8 -j RETURN
iptables -t nat -A CLASH -d 10.0.0.0/8 -j RETURN
iptables -t nat -A CLASH -d 127.0.0.0/8 -j RETURN
iptables -t nat -A CLASH -d 169.254.0.0/16 -j RETURN
iptables -t nat -A CLASH -d 172.16.0.0/12 -j RETURN
iptables -t nat -A CLASH -d 192.168.0.0/16 -j RETURN
iptables -t nat -A CLASH -d 224.0.0.0/4 -j RETURN
iptables -t nat -A CLASH -d 240.0.0.0/4 -j RETURN


#iptables -t nat -A CLASH -p tcp -j RETURN -m mark --mark 0xff # 直连 SO_MARK 为 0xff 的流量(0xff 是 16 进制数，数值上等同与上面配置的 255)，此规则目的是避免代理本机(网关)流量出现回环问题
iptables -t nat -A CLASH -p tcp -j REDIRECT --to-ports 7892 # 其余流量转发到 12345 端口（即 V2Ray）
iptables -t nat -A PREROUTING -p tcp -s 192.168.5.101 -j CLASH # 对局域网其他设备进行透明代理
#iptables -t nat -A OUTPUT -p tcp -j CLASH # 对本机进行透明代理

```

## clean

```bash
iptables -t nat -D PREROUTING -p tcp -s 192.168.5.101 -j CLASH

#iptables -t nat -D PREROUTING -p tcp -j CLASH # 对局域网其他设备进行透明代理
#iptables -t nat -D OUTPUT -p tcp -j CLASH # 对本机进行透明代理
iptables -t nat -F CLASH
iptables -t nat -X CLASH

```

## show iptables

```bash
iptables -t nat  --line -nvL CLASH
iptables -t nat --line -nvL PREROUTING

```

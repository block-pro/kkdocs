# 单臂路由

## AP设置

* AP wan口不要插网线
* 所有网线都插到lan口
* dhcp关闭

## N1设置

### lan口

* 开启dhcp
* 物理网卡去掉桥接模式
* 防火墙修改提示

```bash
# This file is interpreted as shell script.
# Put your custom iptables rules here, they will
# be executed with each firewall (re-)start.

# Internal uci firewall chains are flushed and recreated on reload, so
# put custom rules into the root chains e.g. INPUT or FORWARD or into the
# special user chains, e.g. input_wan_rule or postrouting_lan_rule.

#如果你是用来做旁路 ，用的是 桥接模式 请把 br-lan 这条规则最前面的 # 号注释掉
#反之如果 不是桥接模式 请把 eth0 这条规则最前面的 # 号注释掉 
#如果你是用来做 主路由 则无需理会！注意：修改后 点 重启防火墙 立即生效
iptables -t nat -A PREROUTING -p udp --dport 53 -j REDIRECT --to-ports 53
iptables -t nat -A PREROUTING -p tcp --dport 53 -j REDIRECT --to-ports 53
iptables -t nat -I POSTROUTING -o eth0 -j MASQUERADE
#iptables -t nat -I POSTROUTING -o  br-lan  -j MASQUERADE
```

### wan口

* 走pppoe协议,配置账号和密码
* 物理设置，走eth0
* 如果无反应，记得点击连接

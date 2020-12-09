# install java

## on centos 7

### openjdk8

```bash
sudo yum search openjdk
sudo yum install java-1.8.0-openjdk-devel

ll /usr/bin/java
lrwxrwxrwx 1 root root 22 Aug  6 04:54 /usr/bin/java -> /etc/alternatives/java

/etc/alternatives/java
lrwxrwxrwx 1 root root 73 Aug  6 04:54 /etc/alternatives/java -> /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64/jre/bin/java

export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.252.b09-2.el7_8.x86_64
export PATH=$JAVA_HOME/bin:$PATH

```

### @edit on 200806

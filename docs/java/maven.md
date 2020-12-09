# maven help

## install maven on centos7

```bash

wget https://mirror-hk.koddos.net/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
export PATH=/usr/local/apache-maven-3.6.3/bin:$PATH
```

## maven install with socks5 proxy

```bash
mvn clean install -DsocksProxyHost='127.0.0.1' -DsocksProxyPort=10808
```

## maven download package source

```bash
mvn dependency:sources
```

## maven dependency tree

```bash
mvn dependency:tree
```

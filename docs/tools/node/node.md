# nodejs

## res

* download
    * https://nodejs.org/en/download/

## install

```shell

wget https://nodejs.org/dist/v14.18.0/node-v14.18.0-linux-x64.tar.xz
xz -d node-v14.18.0-linux-x64.tar.xz
tar xvf node-v14.18.0-linux-x64.tar
ln -snf node-v14.18.0-linux-x64 node

vi ~/.bashrc

export NODE_HOME=/home/kkqiao/servers/bin/node/node
export PATH=$NODE_HOME/bin:$PATH
```

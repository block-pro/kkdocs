# syncthing

## resources

### url

* github download
    * <https://github.com/syncthing/syncthing/releases>
* docs
    * <https://docs.syncthing.net/users/syncthing.html>

## linux install & start

* install

```shell
cd servers/bin/syncthing
wget https://github.com/syncthing/syncthing/releases/download/v1.18.3/syncthing-linux-amd64-v1.18.3.tar.gz
tar zxvf syncthing-linux-amd64-v1.18.3.tar.gz
ln -snf syncthing-linux-amd64-v1.18.3 syncthing
```

* start

```shell
cd ~/servers/bin/syncthing/syncthing
export HOME=/home/kkqiao
nohup $HOME/servers/bin/syncthing/syncthing/syncthing \
  -gui-address=0.0.0.0:8384 \
  -home=$HOME/servers/data/syncthing \
  -no-browser \
  > $HOME/servers/bin/syncthing/syncthing/syncthing.log 2>&1 &

```

## mac install

* install

```shell
cd servers/bin/syncthing
wget https://github.com/syncthing/syncthing/releases/download/v1.18.3/syncthing-linux-amd64-v1.18.3.tar.gz
tar zxvf syncthing-linux-amd64-v1.18.3.tar.gz
ln -snf syncthing-linux-amd64-v1.18.3 syncthing
```

* start

```shell
export HOME=/Users/user
nohup $HOME/servers/bin/syncthing/syncthing/syncthing \
  -gui-address=0.0.0.0:8384 \
  -home=$HOME/servers/data/syncthing \
  > $HOME/servers/bin/syncthing/syncthing/syncthing.log 2>&1 &

```

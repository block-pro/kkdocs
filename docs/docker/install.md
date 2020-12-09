# docker install on centos7 or ubuntu

## Uninstall old versions

```bash
sudo yum remove docker \
        docker-client \
        docker-client-latest \
        docker-common \
        docker-latest \
        docker-latest-logrotate \
        docker-logrotate \
        docker-engine
```

## install methods

* set up docker's repositories, recommended
* download rpm
* scripts

## install using repository

* set up the repositories

```bash
# yum-utils.noarch : Utilities based around the yum package manager
sudo yum install -y yum-utils
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

## install docker engine

* install latest version

```bash
sudo yum install docker-ce docker-ce-cli containerd.io
```

* start docker

```bash
sudo systemctl start docker
```

* verify docker

```bash
sudo docker run hello-world
```

* enable docker

```bash
sudo systemctl enable docker
    Created symlink from /etc/systemd/system/multi-user.target.wants/docker.service to /usr/lib/systemd/system/docker.service.
```

## reference

* <https://docs.docker.com/engine/install/centos/>
* <https://docs.docker.com/engine/install/ubuntu/>

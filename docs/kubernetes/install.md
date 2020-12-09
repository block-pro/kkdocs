# kubernetes install and start

## install on centos 7

### remove docker

```bash
sudo yum remove docker-ce docker-ce-cli containerd.io
```

### install etcd and kubernetes

```bash
sudo yum install etcd kubernetes
```

### start all the components

```bash
sudo systemctl start etcd
sudo systemctl start docker
sudo systemctl start kube-apiserver
sudo systemctl start kube-controller-manager
sudo systemctl start kube-scheduler
sudo systemctl start kubelet
sudo systemctl start kube-proxy
```

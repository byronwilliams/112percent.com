# Docker 1.10 Image

# Etcd
/root/docker-compose.yml

10.2.76.79 = eth0

```txt
etcd:
  image: quay.io/coreos/etcd:v2.2.1
  net: host
  command: >
    -name etcd0 -advertise-client-urls http://10.2.76.79:2379,http://10.2.76.79:4001
    -listen-client-urls http://0.0.0.0:2379,http://0.0.0.0:4001
    -initial-advertise-peer-urls http://10.2.76.79:2380
    -listen-peer-urls http://0.0.0.0:2380
    -initial-cluster-token etcd-cluster-1
    -initial-cluster etcd0=http://10.2.76.79:2380
    -initial-cluster-state new
```

# Flannel
```sh
sudo apt-get install linux-libc-dev golang gcc
cd flannel
./build
```

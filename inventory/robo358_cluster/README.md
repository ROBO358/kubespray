# Setup for robo358 Cluster

## Node Configuration

### firewall


#### All Nodes

```sh
# Cilium
firewall-cmd --zone=public --add-port=4240/tcp --permanent
firewall-cmd --zone=public --add-port=4244/tcp --permanent
firewall-cmd --zone=public --add-port=4245/tcp --permanent
firewall-cmd --zone=public --add-port=8472/udp --permanent
firewall-cmd --zone=public --add-port=9962/tcp --permanent
firewall-cmd --zone=public --add-port=9963/tcp --permanent
firewall-cmd --zone=public --add-port=9964/tcp --permanent
firewall-cmd --zone=public --add-port=51871/udp --permanent
# ICMP(for cilium health check)
firewall-cmd --zone=public --add-icmp-block-inversion --permanent
```

#### Control Node

```sh
firewall-cmd --zone=public --add-port=22/tcp --permanent
firewall-cmd --zone=public --add-port=2379/tcp --permanent
firewall-cmd --zone=public --add-port=2380/tcp --permanent
firewall-cmd --zone=public --add-port=6443/tcp --permanent
firewall-cmd --zone=public --add-port=10250/tcp --permanent
firewall-cmd --zone=public --add-port=10257/tcp --permanent
firewall-cmd --zone=public --add-port=10259/tcp --permanent
```

#### Worker Node

```sh
firewall-cmd --zone=public --add-port=22/tcp --permanent
firewall-cmd --zone=public --add-port=10250/tcp --permanent
firewall-cmd --zone=public --add-port=30000-32767/tcp --permanent
```

refs
- [port-requirements.md](/docs/operations/port-requirements.md)
- [Kubernetes Docs](https://kubernetes.io/docs/reference/networking/ports-and-protocols/)

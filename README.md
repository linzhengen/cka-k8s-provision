# cka-k8s-provision

## kind
### Installation
```
brew install kind
kind create cluster --config kind-config.yaml
```

### kind Cluster configuration
```
▸ kubectl get node
NAME                  STATUS     ROLES                  AGE   VERSION
kind-control-plane    Ready      control-plane,master   98s   v1.20.2
kind-control-plane2   Ready      control-plane,master   67s   v1.20.2
kind-worker           NotReady   <none>                 20s   v1.20.2
kind-worker2          NotReady   <none>                 20s   v1.20.2
kind-worker3          NotReady   <none>                 21s   v1.20.2
```

```
▸ kubectl get pod -A -o wide
NAMESPACE            NAME                                          READY   STATUS    RESTARTS   AGE     IP           NODE                  NOMINATED NODE   READINESS GATES
kube-system          coredns-74ff55c5b-c6sqb                       1/1     Running   0          3m32s   10.244.0.3   kind-control-plane    <none>           <none>
kube-system          coredns-74ff55c5b-l4t2r                       1/1     Running   0          3m32s   10.244.0.4   kind-control-plane    <none>           <none>
kube-system          etcd-kind-control-plane                       1/1     Running   0          3m33s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          etcd-kind-control-plane2                      1/1     Running   0          2m54s   172.21.0.2   kind-control-plane2   <none>           <none>
kube-system          kindnet-5v4r8                                 1/1     Running   0          3m29s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          kindnet-hpkdj                                 1/1     Running   0          2m22s   172.21.0.5   kind-worker           <none>           <none>
kube-system          kindnet-kfzcd                                 1/1     Running   0          2m23s   172.21.0.4   kind-worker3          <none>           <none>
kube-system          kindnet-stnn4                                 1/1     Running   0          3m9s    172.21.0.2   kind-control-plane2   <none>           <none>
kube-system          kindnet-tsqxd                                 1/1     Running   0          2m22s   172.21.0.3   kind-worker2          <none>           <none>
kube-system          kube-apiserver-kind-control-plane             1/1     Running   0          3m33s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          kube-apiserver-kind-control-plane2            1/1     Running   0          2m12s   172.21.0.2   kind-control-plane2   <none>           <none>
kube-system          kube-controller-manager-kind-control-plane    1/1     Running   1          3m33s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          kube-controller-manager-kind-control-plane2   1/1     Running   0          112s    172.21.0.2   kind-control-plane2   <none>           <none>
kube-system          kube-proxy-l9f9l                              1/1     Running   0          2m23s   172.21.0.4   kind-worker3          <none>           <none>
kube-system          kube-proxy-lb5vb                              1/1     Running   0          2m22s   172.21.0.3   kind-worker2          <none>           <none>
kube-system          kube-proxy-rlklr                              1/1     Running   0          3m9s    172.21.0.2   kind-control-plane2   <none>           <none>
kube-system          kube-proxy-vm4qd                              1/1     Running   0          2m22s   172.21.0.5   kind-worker           <none>           <none>
kube-system          kube-proxy-wtvpj                              1/1     Running   0          3m32s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          kube-scheduler-kind-control-plane             1/1     Running   1          3m33s   172.21.0.6   kind-control-plane    <none>           <none>
kube-system          kube-scheduler-kind-control-plane2            1/1     Running   0          2m8s    172.21.0.2   kind-control-plane2   <none>           <none>
local-path-storage   local-path-provisioner-78776bfc44-qz8hb       1/1     Running   0          3m27s   10.244.0.2   kind-control-plane    <none>           <none>
```

```
▸ docker exec -it kind-control-plane kubeadm version -o yaml && kubectl version --short
clientVersion:
  buildDate: "2021-01-21T01:10:43Z"
  compiler: gc
  gitCommit: faecb196815e248d3ecfb03c680a4507229c2a56
  gitTreeState: clean
  gitVersion: v1.20.2
  goVersion: go1.15.5
  major: "1"
  minor: "20"
  platform: linux/amd64

Client Version: v1.20.4-dirty
Server Version: v1.20.2
```

```
▸ docker exec -it kind-worker bash -c "kubeadm version -o yaml && kubelet --version"
clientVersion:
  buildDate: "2021-01-21T01:10:43Z"
  compiler: gc
  gitCommit: faecb196815e248d3ecfb03c680a4507229c2a56
  gitTreeState: clean
  gitVersion: v1.20.2
  goVersion: go1.15.5
  major: "1"
  minor: "20"
  platform: linux/amd64

Kubernetes v1.20.2
```

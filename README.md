# k8s-cert-99year

### 动机
为k8s签证99年


### 执行

```

./kubeadm  alpha certs renew all

```

### 查看证书～

```
[root@zhc-netmis-compass-master01 ~]# ./kubeadm  alpha certs check-expiration
Command "check-expiration" is deprecated, please use the same command under "kubeadm certs"
[check-expiration] Reading configuration from the cluster...
[check-expiration] FYI: You can look at this config file with 'kubectl -n kube-system get cm kubeadm-config -o yaml'
[check-expiration] Error reading configuration from the Cluster. Falling back to default configuration

CERTIFICATE                         EXPIRES                  RESIDUAL TIME   CERTIFICATE AUTHORITY   EXTERNALLY MANAGED
admin.conf                          Oct 23, 2120 04:50 UTC   99y                                     no
apiserver                           Oct 23, 2120 04:50 UTC   99y             ca                      no
!MISSING! apiserver-etcd-client
apiserver-kubelet-client            Oct 23, 2120 04:50 UTC   99y             ca                      no
controller-manager.conf             Oct 23, 2120 04:50 UTC   99y                                     no
!MISSING! etcd-healthcheck-client
!MISSING! etcd-peer
!MISSING! etcd-server
front-proxy-client                  Oct 23, 2120 04:50 UTC   99y             front-proxy-ca          no
scheduler.conf                      Oct 23, 2120 04:50 UTC   99y                                     no

CERTIFICATE AUTHORITY   EXPIRES                  RESIDUAL TIME   EXTERNALLY MANAGED
ca                      Nov 06, 2030 09:11 UTC   9y              no
!MISSING! etcd-ca
front-proxy-ca          Nov 06, 2030 09:11 UTC   9y              no

```

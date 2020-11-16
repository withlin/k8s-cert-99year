# k8s-cert-99year

### 动机
为k8s签证99年


### 第一种方式

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




### 第二种方式


```
controllerManager:
  extraArgs:
    v: "4"
    node-cidr-mask-size: "19"
    deployment-controller-sync-period: "10s"
    # 在 kubeadm 配置文件中设置证书有效期为 10 年
    experimental-cluster-signing-duration: "86700h"
    node-monitor-grace-period: "20s"
    pod-eviction-timeout: "2m"
    terminated-pod-gc-threshold: "30"
    
//2
kubeadm alpha certs renew all --use-api

//3
kg csr -n kube-system

//4 
k certificate approve <上面的查出来的csr>



```

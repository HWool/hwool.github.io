---
layout: default
title: 2.4.4 ๐จโ๐ป ์ค์ต
nav_order: 5
parent: 2.4 Accordion ์ค์น
grand_parent: 2. Accordion v2
---

# 2.4.4 ๐จโ๐ป [์ค์ต]์์ฝ๋์ธv2 ์ธ์คํจ
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}


---


## ๐ ์ค์น ์ค๋น์ฌํญ

<details>
<summary>1. ssh key ์์ฑ, ๋ณต์ฌ, ์ ์ ํ์ธ</summary>
  
{% highlight bash %}


Ansible script ์ํ์ ์ํด ๊ฐ ๋ธ๋์์ ssh๋ก root ๋ก๊ทธ์ธ์ด ๊ฐ๋ฅํ๋๋ก ์ค์  ๋ณ๊ฒฝํฉ๋๋ค. (Master&node ์๋ฒ) 
$ vi /etc/ssh/sshd_config
โฆ
PasswordAuthentication yes
PermitRootLogin yes
โฆ
$ systemctl restart sshd

master์๋ฒ์์ ssh key๋ฅผ ์์ฑํฉ๋๋ค. (Master ์๋ฒ) (Master์๋ฒ๋ฅผ ํฌํจํ์ฌ ์ ์ฉํด์ผํฉ๋๋ค.)
$ ssh-copy-id -i /root/.ssh/id_rsa.pub [๋ธ๋IP]
The authenticity of host '10.140.0.3 (10.140.0.3)' canโt be established.
ECDSA key fingerprint is 34:b2:38:b8:be:1b:dd:f1:44:d8:ba:ec:92:d1:d6:dc.
Are you sure you want to continue connecting (yes/no)? yes
/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed โ if you are prompted now it is to install the new keys
root@10.140.0.3โs password:
Number of key(s) added: 1
Now try logging into the machine, with: "ssh '10.140.0.3'"
and check to make sure that only the key(s) you wanted were added.
(cluster์ ๊ตฌ์ฑ์๋ฒ ๋ชจ๋ ๋ฑ๋กํ  ๋๊น์ง ๋ฐ๋ณตํด์ผ ํฉ๋๋ค.)

SSH Key ์ค์ ์ด ์ ์์ ์ธ ํ์ธํฉ๋๋ค. (Master ์๋ฒ) (Master์๋ฒ๋ฅผ ํฌํจํ์ฌ ์ ์ฉํด์ผํฉ๋๋ค.)
$ ssh [๋ธ๋IP]
The authenticity of host 'acc-node1 (10.140.0.3)' canโt be established.
ECDSA key fingerprint is 34:b2:38:b8:be:1b:dd:f1:44:d8:ba:ec:92:d1:d6:dc.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'acc-node1' (ECDSA) to the list of known hosts.
Last failed login: Mon Sep 4 08:17:06 UTC 2017 from 59.49.38.210 on ssh:notty
There was 1 failed login attempt since the last successful login.
Last login: Mon Sep 4 07:18:33 2017
[root@acc-node1 ~] (ํจ์ค์๋ ์์ด ๋ก๊ทธ์ธ์ด ๊ฐ๋ฅํ๋ฉด ์ ์์๋๋ค.)

{% endhighlight %}
   
</details>


<details>
<summary>2. Ansible ์ค์น (์์ฝ๋์ธ ์ค์น ํจํค์ง์ ํฌํจ)</summary>
  
{% highlight bash %}
# ๊ฐ OS์ ๋ง๋๋ก ์ ์
$ /rpms/rpm_redhat7/0_ansible/install.sh # Redhat ๊ณ์ด 7๋ฒ์ 
$ /rpms/rpm_redhat8/0_ansible/install.sh # Redhat ๊ณ์ด 8๋ฒ์ 
$ /rpms/rpm_dpkg/0_ansible/install.sh # ubuntu 18๋ฒ์ 

{% endhighlight %}
   
</details>

<details>
<summary>3. /etc/hosts ํ์ผ ์์ </summary>
  
{% highlight bash %}

$ vi /etc/hosts
10.140.0.2
acc-master
10.140.0.3
acc-node1
10.140.0.4
acc-node2
10.140.0.5
acc-master2
10.140.0.6
acc-master3
โฆ
{% endhighlight %}
   
</details>
<details>
<summary>4. accordion-installer/hosts ์์ </summary>
hostname, ansible_host ์ ๋ณด๋ฅผ ์์ 


{% highlight bash %}

install-server  ansible_host=127.0.0.1     ansible_connection=local   node_role=infra

#########################################################################################
# host-cluster List
#########################################################################################
acc-host-master   ansible_host=10.20.200.201    ansible_connection=ssh   node_role=infra
acc-host-node1    ansible_host=10.20.200.204    ansible_connection=ssh   node_role=infra
acc-host-node2    ansible_host=10.20.200.205    ansible_connection=ssh   node_role=infra

#########################################################################################
# member-cluster List
#########################################################################################
#acc-member-master    ansible_host=10.20.200.206    ansible_connection=ssh   node_role=infra
#acc-member-node1    ansible_host=10.20.200.207    ansible_connection=ssh     node_role=infra
#acc-member-node2    ansible_host=10.20.200.208    ansible_connection=ssh     node_role=infra
#acc-member-master2   ansible_host=10.20.200.5    ansible_connection=ssh     node_role=infra
#acc-member-master3   ansible_host=10.20.200.6    ansible_connection=ssh     node_role=infra

#########################################################################################
# Group List 
#########################################################################################
[local]
install-server

#########################################################################################
# Manager Group

[host-master]
acc-master

[host-master-cluster]

[host-minions]
acc-node1
acc-node2

[host-cluster]
acc-master
acc-node1
acc-node2

{% endhighlight %}
   
</details>
<details>
<summary>5. accordion-installer/group_vars/host.yml ์์ </summary>

{% highlight bash %}

#- setup variable for cluster installation

########################################################
## Master configuation
########################################################
# master isolation ( yes / no ) 
master_isolation: "yes"
master_host_name: "acc-master" # ์ ๋ณด ์์ 
master_ip: 10.20.200.201 # ์ ๋ณด ์์ 

########################################################
# 3master mode( yes / no )
########################################################
master_mode: "no"
master2_ip: 10.20.200.202
master3_ip: 10.20.200.203
master2_hostname: "dev-accordion2"
master3_hostname: "dev-accordion3"
# L4_mode ( L4 / haproxy )
L4_mode: "haproxy"
haproxy_port: 8443
keep_vip: 10.20.200.200
keep_interface: ens192
# Set it up if you want to add the master server later
# If master_mode is "no", it will not work.
# single_option( yes / no )
single_option: "no"

########################################################
## container_name (containerd & cri-o)
########################################################
container_option: "containerd"

# container_option (containerd)
selinux_enable: "no"

# container_option (cri-o)
crio_interface: "ens192"
pid_limit: "4096"

########################################################
# storage setting
########################################################
# storage_option ( nfs / ceph )
storage_option: "nfs"

# nfs_setup ( internal / external )
nfs_setup: "internal" 
nfs_server_ip: 10.10.0.84 # master ip๋ก ์ ๋ณด ์์ 
accordion_nfs_path: "/mnt/vol1"

# nfs_version ( v3 / v4 )
nfs_version: "v3"

# ceph_option ( cephfs / rbd )
ceph_option: "cephfs"

#ceph health, ceph fsid, ceph auth get-key client.admin, ceph status
ceph_server_ip: "10.20.200.107"
ceph_server_port: "6789"
ceph_id: "admin"
ceph_key: "AQCKoqVh0eR5MxAAL4WziV7oyVsdtHC6Wz0RcQ=="
#ceph_id: "kubernetes"
#ceph_key: "AQBDpKVhFhPCIRAAf1xqSLgi558DIH+FvcCyMQ=="
ceph_fsid: "84ab6f51-d13e-4a83-9ccc-fd3b9228e728"
ceph_fsname: "cephfs"
#ceph_fsname: "cephrbd_pool"

########################################################
# etcd external option
########################################################
etcd_external: "no"

########################################################
# base registry
########################################################
# accordion_registry_option ( local / external )
base_registry_option: "local"
base_registry_address: 10.20.200.200 # master ip๋ก ์ ๋ณด ์์ 
base_registry_port: 5000
base_registry_id: accregistry
base_registry_passwd: accordionadmin

########################################################
# user registry
########################################################
# registry_option ( registry / harbor)
user_registry_option: "registry"
user_registry_address: 10.20.200.200 # master ip๋ก ์ ๋ณด ์์ 
user_registry_port: 30001

# registry_external ( yes / no )
user_registry_external: "no"

# user_registry_external: "yes"
user_registry_id: accregistry
user_registry_pw: accordionadmin

# registry information
htpasswd_option: "yes"

########################################################
# Network Setting
########################################################
# CNI (calico or weave)
network_cni: "calico"
# podman Network
podman_cidr: "172.17.0.0/16"
# Pod Network (weave)
IPALLOC_RANGE: "172.32.0.0/12"
# Pod Network (calico)
pod_network_cidr: "172.32.0.0/16"
# Calico Mode (IPIP & vxlan)
calico_backend: "vxlan" # ์ ๋ณด ์์ 
# kubernetes Service Network
service_cidr: "10.96.0.0/12"
kubelet_clusterdns: "10.96.0.10"
kubernetes_clusterip: "10.96.0.1"

########################################################
## container dir
########################################################
containers_storage_runroot: /mnt/vol1/var/run/containers # ์ ๋ณด ์์ 
containers_storage_volume: /mnt/vol1/var/lib/containers # ์ ๋ณด ์์ 

########################################################
## Kubernetes dir
########################################################
kubelet_root_dir: /mnt/vol1/var/lib # ์ ๋ณด ์์ 
kube_addon_dir: /mnt/vol1/etc/kubernetes/addon # ์ ๋ณด ์์ 
docker_rpm_dir: /mnt/vol1/tmp # ์ ๋ณด ์์  

########################################################
# If the external IP is set up on the master server, enter the IP.
########################################################
master_external_ip: "127.0.0.1" # public ip๋ก ์ ๋ณด ์์ 

########################################################
## Add node option (yes / no)
########################################################
noschedule: "no"

##########################################
## accordion GPU monitoring(yes/no)
##########################################
gpu_server: "yes"

##########################################
## external prometheus
##########################################
external_prometheus: "no"
prometheus_name: "prometheus-operator-prometheus"
prometheus_ns: "acc-system"


{% endhighlight %}
   
</details>



**์์ฝ๋์ธ ์ค์น ๋ฐ ํ์ธ**
- accordion-installer/install.sh
- accordion-installer/status.sh

**์ค์น ์ค์ **
```bash
$ accordion-installer/install.sh
```

**์ค์น ์งํ**
```bash
$ accordion-installer/install.sh
End User Software License Agreement

This is a legal agreement between Customer and Man Technology Co., LTD. ("Mantech").  YOU MUST READ AND AGREE TO THE TERMS OF THIS END USER SOFTWARE LICENSE AGREE
MENT ("AGREEMENT") BEFORE ANY SOFTWARE CAN BE DOWNLOADED OR INSTALLED OR USED.  BY CLICKING ON THE "ACCEPT" BUTTON OR TYPING THE "Y" OF THIS AGREEMENT, OR DOWNLOA
DING, INSTALLING OR USING THE SOFTWARE, YOU ARE AGREEING TO BE BOUND BY THE TERMS AND CONDITIONS OF THIS AGREEMENT.  IF YOU DO NOT AGREE WITH THE TERMS AND CONDIT
IONS OF THIS AGREEMENT, THEN YOU SHOULD NOT DOWNLOAD, INSTALL OR USE THE SOFTWARE.  BY DOING SO YOU FORGO ANY IMPLIED OR STATED RIGHTS TO DOWNLOAD OR INSTALL OR U
SE THE SOFTWARE.
...
...
16. Questions.  Should you have any questions concerning the foregoing, please contact Mantech at the following address: Man Technology Co., LTD. 12th Fl, 308-4,
Seongsudong 2ga, Seongdong-gu, Seoul, Korea.
                 Phone : +82-2-2136-6900
                 E-mail : marketing@mantech.co.kr
                 www.mantech.co.kr


DO YOU ACCEPT THE TERMS OF THIS LINCESE AGREEMENT? [y/n] : y
```

**์ค์น ํ์ธ**
```bash
$ accordion-installer/status.sh
========================================
 nodes
========================================
NAME         STATUS   ROLES                  AGE    VERSION
acc-master   Ready    control-plane,master   177m   v1.20.8
acc-node1    Ready    worker                 176m   v1.20.8
========================================
 deployments/po/svc
========================================
NAMESPACE     NAME                                           READY   UP-TO-DATE   AVAILABLE   AGE
acc-global    deployment.apps/alert-apiserver                1/1     1            1           162m
acc-global    deployment.apps/authset-manager                1/1     1            1           161m
acc-global    deployment.apps/chartmuseum-chartmuseum        1/1     1            1           163m
acc-global    deployment.apps/cloud-apiserver                1/1     1            1           161m
acc-global    deployment.apps/clusterinfo-manager            1/1     1            1           172m
acc-global    deployment.apps/console                        1/1     1            1           162m
acc-global    deployment.apps/gateway                        1/1     1            1           162m
acc-global    deployment.apps/host-log-apiserver             1/1     1            1           162m
acc-global    deployment.apps/keycloak                       1/1     1            1           163m
acc-global    deployment.apps/keycloak-db                    1/1     1            1           163m
acc-global    deployment.apps/manual-webserver               1/1     1            1           161m
acc-global    deployment.apps/monitoring-apiserver           1/1     1            1           162m
acc-global    deployment.apps/setting-manager                1/1     1            1           163m
acc-global    deployment.apps/thanos-querier                 1/1     1            1           163m
acc-system    deployment.apps/acc-grafana                    1/1     1            1           170m
acc-system    deployment.apps/acc-kube-state-metrics         1/1     1            1           170m
acc-system    deployment.apps/accordion-ingress-controller   1/1     1            1           170m
acc-system    deployment.apps/apm-agent-injector             1/1     1            1           166m
...
...

```

**์์ฝ๋์ธ ์ ์ URL**

| URL      | ID    | PW    |
|:---------|:------|:------|
| https://VIP://30000      | admin  | accordion!@# |

![acc-ins-1.png](/assets/images/accordion/acc-ins-1.png){: width="800" }


---


## ๋ผ์ด์ ์ค ๋ฑ๋ก
`๊ธ๋ก๋ฒ ์ค์ ` โก `๋ผ์ด์ ์ค` โก `๋ฑ๋ก`

![practice-1.png](/assets/images/accordion/practice-1.png)
![practice-2.png](/assets/images/accordion/practice-2.png)

---
layout: default
title: 2.4.2 📁인스톨러 구조
nav_order: 4
parent: 2.4 Accordion 설치
grand_parent: 2. Accordion v2
---

# 2-4-2 인스톨러 구조
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Ansible

![ansible.png](/assets/images/accordion/ansible.png)


---

## 📁 인스톨러(accordion-installer) 구조

<details>
<summary>📂 accordion-installer 구조</summary>
  
{% highlight bash %}
accordion-installer/
|-- roles               # 설치 태스크 디렉토리  
|-- group_vars          # 설치 공통 변수 설정 디렉토리
|-- hosts               # cluster구성할 hosts 설정
|-- install.sh          # 설치 
|-- uninstall.sh        # 삭제
|-- status.sh           # 설치 후 상태확인
|-- add-aks.sh          # aks cluster 추가
|-- add-eks.sh          # eks cluster 추가(eksctl)
|-- add-kubeconfig.sh
|-- addaks.yml
|-- addeks.yml
|-- addkubeconfig.yml
|-- addmaster.sh        # master 노드 추가
|-- addmember.sh        # member cluster 추가
|-- addmember.yml   
|-- addnode.sh          # node 추가
|-- all.retry
|-- all.yml
|-- ansible.cfg
|-- getconfig.yml
|-- kube-teardown.retry
|-- kube-teardown.yml
|-- lic.txt
|-- master.yml
|-- node.yml
|-- remove-aks.sh       # aks cluster 삭제
|-- remove-eks.sh       # eks cluster 삭제
|-- removeaks.yml
|-- removeeks.yml
|-- removemember.sh     # member cluster 삭제
|-- removemember.yml    
|-- removenode.sh       # node 삭제
|-- restore.sh          # 백업/복구 스크립트
|-- restore.yml
|-- run_role.yml
|-- THIRDPARTYLICENSE.txt
{% endhighlight %}
   
</details>

<details>
<summary>📂 group_vars 구조</summary>
  
{% highlight bash %}

group_vars/
|-- host.yml                          # 아코디언 설치 구성을 위한 변수
|-- all.yml                           # 아코디언 설치 구성을 위한 변수
|-- config.yml                        # registry, config 관련 설정            
|-- aks.yml                           # aks 클러스터 구성을 위한 변수
|-- eks.yml                           # eks 클러스터 구성을 위한 변수
|-- etcd-master-cluster-manager.yml   # host cluster의 etcd 외부 구성
|-- etcd-master-cluster-member.yml    # member cluster의 etcd 외부 구성
|-- member.yml                        # member cluster 구성
{% endhighlight %}
   
</details>


<details>
<summary>📂 roles 구조</summary>
  
{% highlight bash %}

roles/
|-- 0-rpms-install
|-- 1-add-uid-gid
|-- 2-nfs
|-- 3-kube-prerequisite
|-- 4-add-containerd
|-- 4-containerd
|-- 4-cri-o
|-- 5-kube-install
|-- 6-kube-init-join
|-- 6-kube-init-join-cluster
|-- 6-kube-init-join-cluster-single
|-- 7-node-label
|-- 8-weave-kube
|-- 9-acc-registry
|-- 10-crd
|-- 11-acc-system
|-- 12-acc-global
|-- 13-acc-global-after
|-- 14-backup
|-- add-aks
|-- add-eks
|-- add-gpu
|-- add-kubeconfig
|-- add-master
|-- add-node
|-- cloud-acc-system
|-- cloud-crd
|-- kube-teardown
|-- member-info
|-- remove-aks
|-- remove-eks
|-- remove-node
|-- restore-etcd
|-- restore-etcd-single   
{% endhighlight %}
   
</details>

---

## 아코디언 타겟노드 설정

경로 : `accordion-installer/hosts`

아코디언 hosts 설정 파일에는 아코디언을 구성할 Node들의 설정이 주로 이루어집니다. 현재 구성된 Master와 Node들의 IP주소를 수정합니다.<br>
내부 IP가 별도로 있는 경우 내부 IP로 입력하시면 됩니다. 

💡 참고 : host-cluster List와 member-cluster List에 입력하는 양식은 동일

---

**예시1. Host-cluster만 구성할 시(Master: 1대, Worker: 2대)**

|Hostname|Host IP|사용자 설정|사용자 설정|
|--|--|--|--|
|acc-master|ansible_host=10.60.100.70|ansible_connection=ssh|node_role=infra|
|acc-worker1|ansible_host=10.60.100.71|ansible_connection=ssh|node_role=infra|
|acc-worker2|ansible_host=10.60.100.72|ansible_connection=ssh|node_role=infra|

```yaml
install-server  ansible_host=127.0.0.1     ansible_connection=local   node_role=infra 

#########################################################################################
# host-cluster List
#########################################################################################
acc-master    ansible_host=10.60.100.70    ansible_connection=ssh   node_role=infra
acc-worker1   ansible_host=10.60.100.71    ansible_connection=ssh   node_role=infra
acc-worker2   ansible_host=10.60.100.72    ansible_connection=ssh   node_role=infra
```

---

**예시2. 구성하는 host-cluster와 member-cluster 같이 구성할 경우**

|Hostname|Host IP|사용자 설정|사용자 설정|
|--|--|--|--|
|acc-master|ansible_host=10.60.100.70|ansible_connection=ssh|node_role=infra|
|acc-worker1|ansible_host=10.60.100.71|ansible_connection=ssh|node_role=infra|
|acc-worker2|ansible_host=10.60.100.72|ansible_connection=ssh|node_role=infra|

|Hostname|Host IP|사용자 설정|사용자 설정|
|--|--|--|--|
|acc-member-master|ansible_host=10.60.101.70|ansible_connection=ssh|node_role=infra|
|acc-member-worker1|ansible_host=10.60.101.71|ansible_connection=ssh|node_role=infra|
|acc-member-worker2|ansible_host=10.60.101.72|ansible_connection=ssh|node_role=infra|

```yaml
install-server  ansible_host=127.0.0.1     ansible_connection=local   node_role=infra 

#########################################################################################
# host-cluster List
#########################################################################################
acc-master    ansible_host=10.60.100.70    ansible_connection=ssh   node_role=infra
acc-worker1   ansible_host=10.60.100.71    ansible_connection=ssh   node_role=infra
acc-worker2   ansible_host=10.60.100.72    ansible_connection=ssh   node_role=infra

#########################################################################################
# member-cluster List
#########################################################################################
acc-member-master  ansible_host=10.60.101.70    ansible_connection=ssh   node_role=infra
acc-member-worker1 ansible_host=10.60.101.71    ansible_connection=ssh   node_role=infra
acc-member-worker2 ansible_host=10.60.101.72    ansible_connection=ssh   node_role=infra
```

`node_role=infra`는 Pod들의 어피니티 설정을 위해 라벨을 명시합니다. 설치 후 `--show-labels` 명령을 입력하면 `node_role` 라벨을 볼 수 있습니다.


**`ansible_connection='options'`**

|Hostname|Host IP|사용자 설정|
|--|--|--|
|ssh|ansible_connection=ssh|연결을 ssh로 사용|
|local|ansible_connection=local|연결을 localhost로 사용. 이 설정을 하면 단일 호스트에서만 명령을 실행|
|paramiko_ssh|ansible_connection=paramiko_ssh|	연결을 python으로 구현한 ssh로 사용|
|winrm|ansible_connection=winrm|연결을 windows의 winrm을 사용|

💡 참고 : 다음 명령을 통해 더 많은 연결 옵션을 확인할 수 있습니다.

```bash
ansible-doc -t connection -l
```

---

**hosts파일 cluster List 이후 부분**

```yaml
#########################################################################################
# Group List
#########################################################################################
[local]
install-server

#########################################################################################
# Manager Group

[host-master] → host-cluster의 Master node의 hostname을 기입
#acc-host-master
acc-master

[host-master-cluster]
#acc-host-master2 → 3중화 구성 시 작성
#acc-host-master3 → 3중화 구성 시 작성

[host-minions] → host-cluster의 worker node 정보 기입(worker)
acc-worker1
acc-worker2
#acc-host-node1
#acc-host-node2

[host-cluster] → host-cluster의 전체 Node들의 hostname을 모두 작성(master + worker)
acc-master
acc-worker1
acc-worker2
#acc-host-master
#acc-host-node1
#acc-host-node2
#acc-host-master2
#acc-host-master3

[host-infra] → host-cluster에 infra node로 설정할 hostname을 작성

[host-etcd] → host-cluster에 etcd node로 설정할 hostname을 작성

#########################################################################################
```

---

## 공통 변수

공통변수(hosts) 에서는 아코디언 설치시 필요한 `master` 설정, 클러스터 ip 대역등 설정이 가능합니다.

경로: `group_vars/hosts.yml`

|옵션명 |입력값 | 설명 |
|:-----|:-----|:----|
|master_isolation|yes, no|Master node의 taint을 설정합니다.<br>no일 경우 master에도 Pod가 배치됩니다.<br>(default: no)|
|master_host_name|사용자 설정|마스터서버의 hostname을 입력|
|master_ip|사용자 설정|마스터서버의 IP를 입력|
|master_mode|yes<br>no|3중화 설치여부 <br>● yes: 3중화 설치 <br>● no: 단일설치default|
|master2_ip|사용자 설정|master2 서버 IP|
|master3_ip|사용자 설정|master3 서버 IP|
|master2_hostname|사용자 설정|master2 서버 hostname|
|master3_hostname|사용자 설정|master3 서버 hostname|
|L4_mode|L4<br>haproxy|L4 haproxy 사용여부<br>● L4로 설정 시 L4장비를 사용, 사전작업 필요<br>● haproxy 설정 시 haproxy pod를 띄워 구성함<br>(default: haproxy)|
|haproxy_port|사용자 설정|apiserver 6443 port로 넘겨주는 port구성<br>(default: 8443)|
|keep_vip|사용자 설정| ✋ master서버 vip설정입니다.|
|keep_interface|사용자 설정|master서버 OS의 network interface name을 입력|
|single_option|사용자 설정|master서버 1대로 설치 후 나중에 2대를 붙여 3중화를 구성할 수 있도록 설정하는 옵션 입니다.<br>(권장: 사전에 3중화 설정정보를 기입해야함)|
|container_option|containerd<br>cri-o|컨테이너 런타임을 설정합니다.<br>(default: containerd)|
|selinux_enable|no|selinux 활성화 옵션입니다.<br>(default: no)|
|crio_interface|사용자 인터페이스 입력|ifconfig 입력 후 ens 값을 넣어줍니다.|
|storage_option|nfs<br>ceph|스토리지 타입을 선택합니다<br>● nfs: nfs 사용<br>● ceph: ceph 사용|
|nfs_setup|internal external|nfs의 설치 방식을 선택합니다<br> ✋ internal: master서버에 nfs를 설치 후 사용<br> ✋ external: 외부에 마운트된 nfs를 사용|
|nfs_server_ip|사용자 설정|nfs서버의 ip를 설정합니다<br>● nfs_setup이 internal일 경우 masterIP 입력<br>● nfs_setup이 external일 경우 외부 nfs서버 IP 입력|
|accordion_nfs_path|사용자 설정|nfs_setup이 internal일 경우 원하는 nfs경로를 입력<br>nfs_setup이 external일 경우 마운트된 nfs경로를 입력<br>(default 경로: nfs/data)|
|ceph_option|cephfs rbd|Ceph type을 설정합니다<br>(default: cephfs)|
|ceph_server_ip|사용자 설정|Ceph server IP를 설정합니다|
|ceph_server_port|사용자 설정|Ceph server port를 설정합니다|
|ceph_id|사용자 설정|ceph 스토리지에 접근에 필요한 ID를 설정합니다<br>cephfs는 admin계정 rbd는 user계정이 필요합니다|
|ceph_key|사용자 설정|ceph 스토리지에 접근에 필요한 계정의 key값을 설정합니다|
|ceph_fsid|사용자 설정|ceph 클러스터 ID를 설정합니다|
|ceph_fsname|사용자 설정|ceph fsname을 설정합니다|
|etcd_external|yes<br>no|etcd서버를 외부에 구성할지의 여부를 설정합니다<br>● yes: etcd를 외부에 설정<br>● no: etcd를 포함하여구성(default)|
|base_registry_option|local external|base_registry의 설치여부를 선택합니다<br>local(default): local에 registry를 설치합니다<br>host(member-cluster 전용옵션): local에 설치하지 않고, external의 registry서버를 바라봅니다<br>(default: local)|
|base_registry_address|사용자 설정|registry서버의 address를 설정합니다. <br> ✋ internal 인경우, master vip|
|base_registry_port|사용자 설정|registry서버의 port를 지정합니다.<br>(default): 5000|
|base_registry_id|사용자 설정|registry id를 설정합니다<br>(default: accregistry)|
|base_registry_passwd|사용자 설정|registry pw를 설정합니다<br>(default: accordionadmin)|
|user_registry_option|registry<br>harbor|user registry서버 option을 설정합니다<br>registry: 기본 user registry로 구성합니다(default)<br>harbor: 기본 user registry를 harbor로 구성합니다|
|user_registry_address|사용자 설정|user_registry_external이 yes일경우 활성화되며, 외부 레지스트리의 주소를 입력합니다. <br> ✋ internal 인경우, master vip|
|user_registry_port|사용자 설정|user_registry_external이 yes일경우 활성화되며, 외부 레지스트리의 포트를 입력합니다|
|user_registry_external|yes<br>no|user_registry의 위치를 설정합니다.<br>● yes: registry가 external에 위치합니다.<br>● no: registry가 local에 위치합니다.(default)|
|user_registry_id|사용자 설정|user_registry_external이 yes일경우 활성화되며,외부 레지스트리의 계정을 입력합니다<br>(default: accregistry)|
|user_registry_pw|사용자 설정|user_registry_external이 yes일경우 활성화되며, 외부 레지스트리의 패스워드를 입력합니다<br>(default: accordionadmin)|
|htpasswd_option|yes<br>no|user registry의 인증여부를 선택합니다<br>● yes(default): user registry에서 패스워드 인증을 진행합니다<br>● no: user registry에서 패스워드 인증을 하지않고 접속합니다|
|network_cni|calico<br>weave|설치할 cni를 설정합니다<br>(default: calico)|
|podman_cidr|사용자 설정|podman의 대역을 설정합니다|
|IPALLOC_RANGE|사용자 설정|pod network의 Range를 설정합니다<br>(network_cni가 weave일때 적용)|
|pod_network_cidr|사용자 설정|pod network의 cidr를 설정합니다<br>(network_cni가 calico일때 적용)|
|calico_backend|IPIP<br>vxlan|calico backend 타입을 설정합니다|
|service_cidr|사용자 설정|service의 cidr를 설정합니다|
|kubelet_clusterdns|사용자 설정|service cidr의 시작ip로부터 10번째 ip를 입력합니다<br>(ex 10.96.0.0/12일경우 10.96.0.1이 첫번째 ip이므로 10.96.0.10을 입력)|
|kubernetes_clusterip|사용자 설정|service cidr의 시작ip를 입력합니다|
|containers_storage_runroot|사용자 설정|모든 상태 정보가 저장되는 디렉토리를 지정합니다.<br>(default: /var/run/containers)|
|containers_storage_volume|사용자 설정|컨테이너 저장소 볼륨을 지정합니다.<br>(default: /var/lib/containers)|
|kubelet_root_dir|사용자 설정|kubernetes Root 디렉토리를 지정합니다<br>(default: /var/lib)|
|kube_addon_dir|사용자 설정|배포되는 yaml들의 저장경로를 설정합니다<br>(default: /etck/kubernetes/addon)|
|docker_rpm_dir|사용자 설정|각 서버에 필요한 파일을 배포하는 경로를 설정합니다<br>(default: /tmp)|
|master_external_ip|사용자 설정|public ip를 설정합니다<br> ✋ master ip와 접근경로가 다른경우 설정 |
|noschedule|yes<br>no|노드를 추가합니다.<br>(default: no)|
|gpu_server|사용자 설정|GPU 모니터링을 사용합니다.<br>(default: no)|
|external_prometheus|yes<br>no|yes: 외부 prometheus를 사용할 경우(prometheus가 설치되지 않음)<br>no: 내부 prometheus를 사용|
|prometheus_name|사용자 설정|prometheus 이름을 지정합니다.<br>(default: prometheus-operator-prometheus)|
|prometheus_ns|사용자 설정|prometheus가 설치될 네임스페이스를 지정합니다.<br>(default: acc-system)|

---

### 💡 일반유저(sudo 권한)

`root` 유저를 사용할 수 없을 경우, `sudo` 권한을 가진 일반유저로도 설치 가능합니다.

**1. hosts 파일에 다음 설정을 변경합니다.**

```ini
[all:vars]
ansible_ssh_port=22
ansible_user=root
ansible_password_option=no
#ansible_ssh_pass=ROOT_PASSWORD
keyfile_option=no
#ansible_ssh_private_key_file=/mantech/accordion.pem
ansible_ssh_common_args=-oPubkeyAuthentication=yes
```

|기본값|변경값|
|--|--|
|ansible_user=root|ansible_user=[sudo권한 일반유저]|
|ansible_password_option=no|ansible_password_option=[yes]|
|#ansible_ssh_pass=ROOT_PASSWORD|ansible_ssh_pass=[sudo권한 일반유저 비밀번호]|

**2. ansible.cfg**

```ini
[defaults]
host_key_checking = false
deprecation_warnings = False
command_warnings = False
callback_whitelist = profile_tasks
log_path = /tmp/ansible.log
forks = 20

[privilege_escalation]
become = True
become_ask_pass = True
become_user = root
become_method = sudo
```

|기본값|변경값|
|--|--|
| log_path = /tmp/ansible.log | #log_path = /tmp/ansible.log |
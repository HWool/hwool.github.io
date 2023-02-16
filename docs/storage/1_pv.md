---
layout: default
title: 9.1 퍼시스턴트볼륨
nav_order: 1
parent: 9. 스토리지
---

# 퍼시스턴트볼륨
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Cluster
{: .label .label-blue }
</div>


## 퍼시스턴트 볼륨(Persistent-volumes)

퍼시스턴트볼륨 (PV)은 관리자가 프로비저닝하거나 스토리지 클래스를 사용하여 동적으로 프로비저닝한 클러스터의 스토리지입니다. 

노드가 클러스터 리소스인 것처럼 PV는 클러스터 리소스입니다. PV는 Volumes와 같은 볼륨 플러그인이지만, PV를 사용하는 개별 파드와는 별개의 라이프사이클을 가지고 있습니다. 

**퍼시스턴트 볼륨의 유형**
퍼시스턴트볼륨 유형은 플러그인으로 구현됩니다. 쿠버네티스는 현재 다음의 플러그인을 지원합니다.

- awsElasticBlockStore - AWS Elastic Block Store (EBS)
- azureDisk - Azure Disk
- azureFile - Azure File
- cephfs - CephFS 볼륨
- csi - 컨테이너 스토리지 인터페이스 (CSI)
- fc - Fibre Channel (FC) 스토리지
- gcePersistentDisk - GCE Persistent Disk
- glusterfs - Glusterfs 볼륨
- hostPath - HostPath 볼륨 (단일 노드 테스트 전용. 다중-노드 클러스터에서 작동하지 않음. 대신 로컬 볼륨 사용 고려)
- iscsi - iSCSI (SCSI over IP) 스토리지
- local - 노드에 마운트된 로컬 스토리지 디바이스
- nfs - 네트워크 파일 시스템 (NFS) 스토리지
- portworxVolume - Portworx 볼륨
- rbd - Rados Block Device (RBD) 볼륨
- vsphereVolume - vSphere VMDK 볼륨

**사용중단**

- cinder - Cinder (오픈스택 블록 스토리지) (v1.18에서 사용 중단)
- flexVolume - FlexVolume (v1.23에서 사용 중단)
- flocker - Flocker 스토리지 (v1.22에서 사용 중단)
- quobyte - Quobyte 볼륨 (v1.22에서 사용 중단)
- storageos - StorageOS 볼륨 (v1.22에서 사용 중단)

**사용불가**

- photonPersistentDisk - Photon 컨트롤러 퍼시스턴트 디스크. (v1.15 이후 사용 불가)
- scaleIO - ScaleIO 볼륨 (v1.21 이후 사용 불가)


**Access Mode**

- ReadWriteOnce(RWO) 
하나의 노드에서 해당 볼륨이 읽기-쓰기로 마운트 될 수 있다. ReadWriteOnce 접근 모드에서도 파드가 동일 노드에서 구동되는 경우에는 복수의 파드에서 볼륨에 접근할 수 있다.
- ReadOnlyMany(ROX)
볼륨이 다수의 노드에서 읽기 전용으로 마운트 될 수 있다.
- ReadWriteMany(RWX) 
볼륨이 다수의 노드에서 읽기-쓰기로 마운트 될 수 있다.
- ReadWriteOncePod(RWOP)
볼륨이 단일 파드에서 읽기-쓰기로 마운트될 수 있다. 전체 클러스터에서 단 하나의 파드만 해당 PVC를 읽거나 쓸 수 있어야하는 경우 ReadWriteOncePod 접근 모드를 사용한다. 이 기능은 CSI 볼륨과 쿠버네티스 버전 1.22+ 에서만 지원된다.


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}
apiVersion: v1
kind: PersistentVolume
metadata:
  name: foo-pv
spec:
  storageClassName: ""
  claimRef:
    name: foo-pvc
    namespace: foo
  ...
{% endhighlight %}
   
</details>


---

## 메뉴이동
`스토리지` ➡ `퍼시스턴트볼륨`

![storage-001.png](/assets/images/storage/storage-001.png)

---

## 화면구성
생성된 네트워크폴리시 정보를 제공합니다.

![storage-004.png](/assets/images/storage/storage-004.png){: width="800" }

---

## 퍼시스턴트볼륨 생성
`+생성`을 클릭 후 내용을 입력하여 퍼시스턴트볼륨을 생성할 수 있습니다. 퍼시스턴트볼륨은 YAML로 입력할 수 있습니다.

![storage-005.png](/assets/images/storage/storage-005.png){: width="800" }

---

## 퍼시스턴트볼륨 수정
퍼시스턴트볼륨 목록에서 특정 퍼시스턴트볼륨을 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 퍼시스턴트볼륨 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 퍼시스턴트볼륨 명 입력 후 `Delete` 버튼 클릭 시 퍼시스턴트볼륨이 삭제됩니다.

![pv-delete.png](/assets/images/storage/pv-delete.png){: width="800" }
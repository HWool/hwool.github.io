---
layout: default
title: 3.1.2 클러스터
nav_order: 3
grand_parent: 3. 대시보드
parent: 3.1 글로벌대시보드
---

# 3.1.2 클러스터
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Global
{: .label .label-purple }
</div>

## 클러스터
클러스터란 컨테이너화된 애플리케이션을 실행하기 위한 노드의 집합을 의미합니다. 컨테이너화된 애플리케이션은 개별 노드에 얽매이지 않고 클러스터에 배포됩니다.
클러스터는 Host 클러스터 및 하나 이상의 Member 클러스터를 가지며 싱글 클러스터인 경우 Host와 Member 클러스터 역할을 가집니다.

클러스터 메뉴에서는 Host Cluster는 하나만 등록이 가능하여 Member Cluster만 관리할 수 있습니다.

**호스트/멤버 클러스터의 구성 예**

- 싱글 클러스터 구성
  + 하나의 클러스터가 호스트/멤버 클러스터 역할을 모두 수행
- 관리 클러스터와 운영 클러스터 분리
  + 호스트 클러스터에서는 관리의 업무만 수행하고 별도의 멤버 클러스터에만 애플리케이션을 배포


**클러스터 목록**
![3_cluster_overview.png](/assets/images/dashboard/cluster/3_cluster_overview.png)

- 항목별 상세설명

| 항목 | 클러스터 이름 |
|:--:|--|
|Cluster Name|클러스터 이름|
|Provider|Kubernetes Cloud Provider|
|Master Nodes|마스터노드 개수|
|Worker Nodes|워커노드 개수|
|Description|클러스터 설명|
|Namespaces|클러스터에 생성되어있는 namespace 개수|
|Pods|클러스터에 생성되어있는 pods 개수|
|Version|클러스터 버전|
|Created|클러스터 생성시각|
|Phase|클러스터 상태|
|Cores|클러스터 코어 사이즈|
|Memory|클러스터 메모리 사이즈|
|Disk|클러스터 디스크 사이즈|

- Member Cluster 수정/삭제 항목 설명

|분류|설명|
|:--:|--|
|수정|등록한 Member Cluster의 정보를 수정|
|삭제|Member Cluster를 삭제|

**Member Cluster 수정**

Cluster 목록에서 등록된 Member Cluster의 [수정]]을 클릭하면 수정 화면으로 이동됩니다.

- Member Cluster 수정 항목

|분류|설명|
|:--:|--|
|Name|Cluster Name을 입력|
|Server|Cluster Server 주소|
|Provider|None,Accordion,EKS,AKS,GKE,VMWawre,Nutanix 등|
|Role|Member만 선택|
|Proxy CA certificate|Kubernetes TLS 인증을 위한 CA 인증서|
|Description|등록할 cluster에 대한 설명을 입력|


![3_cluster_member_edit.png](/assets/images/dashboard/cluster/3_cluster_member_edit.png)

**Member Cluster 삭제**

![3_cluster_member_delete.png](/assets/images/dashboard/cluster/3_cluster_member_delete.png)

Cluster 목록에서 등록된 Member Cluster의 [삭제]를 클릭하면 삭제 팝업이 나타납니다.

---
---
layout: default
title: 3.2 클러스터대시보드
nav_order: 2
parent: 3. 대시보드
---

# 3.2 클러스터대시보드
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

## 클러스터 대시보드
클러스터 대시보드는 Cluster Info/Kubernetes Object Info/사용량 Top5/Node 별 사용량에 대해서 확인할 수 있습니다.

![3_cluster-dashboard-full.png](/assets/images/dashboard/3_cluster-dashboard-full.png){: width="800" }

---

## 메뉴이동
`클러스터 대시보드`

![cd.png](/assets/images/dashboard/cd.png)

---

## Clusters Info
시간대별 클러스터의 CPU,Memory,Network 사용량을 확인할 수 있다. 차트에 마우스 커서를 올려보면 실시간으로 정보를 수집하고 있다는 것을 알 수 있습니다.

![3_cluster-dashboard-clusterinfo.png](/assets/images/dashboard/3_cluster-dashboard-clusterinfo.png){: width="800" }


|항목|설명|
|:--|:--|
|Name|Host Cluster의 이름|
|Provider|Host Cluster의 provider|
|API Server|Accordion의 API Server 주소|
|Created|Host Cluster의 생성시각 Created 시간 기준은 UTC |
|Desc|Host Cluster에 대한 설명|

## Kubernetes Object Info
kubernetes object에 대한 기본적인 정보를 확인할 수 있습니다.

![3_cluster-dashboard-k8sobjectinfo.png](/assets/images/dashboard/3_cluster-dashboard-k8sobjectinfo.png){: width="800" }

---

## Usage

![3_cluster-dashboard-footer.png](/assets/images/dashboard/3_cluster-dashboard-footer.png){: width="800" }

---

## Pod CPU Usage Top5

클러스터 내에서 Pod의 CPU 사용량을 상위 5개씩 확인할 수 있습니다.

![3_cluster-dashboard-pod-cpu-usage.png](/assets/images/dashboard/3_cluster-dashboard-pod-cpu-usage.png){: width="800" }

---

## Pod Memory Usage Top5
클러스터 내에서 Pod의 Memory 사용량을 상위 5개씩 확인할 수 있습니다.

![3_cluster-dashboard-pod-memory-usage.png](/assets/images/dashboard/3_cluster-dashboard-pod-memory-usage.png){: width="800" }

---

## Node
클러스터 내에서 노드의 정보를 확인할 수 있습니다.

![3_cluster-dashboard-node.png](/assets/images/dashboard/3_cluster-dashboard-node.png){: width="800" }

|항목|설명|
|--|--|
|이름|노드의 이름|
|상태|노드의 현재 상태(Ready, NotReady)|
|롤|노드의 현재 롤|
|파드|노드의 현재 Pod 사용률(사용 중인 갯수/최대 사용가능 갯수)|
|CPU|노드의 현재 CPU 사용률(현재 사용 크기/최대 사용가능 크기)|
|메모리|노드의 현재 Memory 사용률(현재 메모리 사용량/최대 사용가능 메모리)|

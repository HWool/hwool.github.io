---
layout: default
title: 6. 워크로드
nav_order: 6
has_children: true
permalink: /docs/workload
---

# 6. 워크로드

워크로드는 쿠버네티스에서 구동되는 애플리케이션입니다. 워크로드가 단일 컴포넌트이거나 함께 작동하는 여러 컴포넌트이든 관계없이, 쿠버네티스에서는 워크로드를 일련의 `Pod` 내에서 실행합니다. 쿠버네티스에서 `Pod` 는 클러스터에서 실행 중인 컨테이너 집합입니다.

## Kubernetes Pod Life Cycle
예를 들어, 일단 Pod가 클러스터에서 실행되고 나서 해당 Pod가 동작 중인 노드에 심각한 오류가 발생하면 해당 노드의 모든 Pod가 실패합니다. 쿠버네티스는 이 수준의 실패를 `final` 으로 취급한다. 사용자는 향후 노드가 복구되는 것과 상관 없이 Pod 를 새로 생성해야 합니다.

쿠버네티스에서는 각 Pod 를 직접 관리할 필요는 없도록 만들었습니다. 대신, 사용자를 대신하여 파드 집합을 관리하는 워크로드 리소스를 사용할 수 있습니다. 이러한 리소스는 지정한 상태와 일치하도록 올바른 수의 올바른 파드 유형이 실행되고 있는지 확인하는 컨트롤러를 구성합니다.

![](https://clouddayscom.files.wordpress.com/2020/11/k8s-exposed-pod-1.png?w=1024&h=571){: width="800" }

**워크로드 종류**

- `Deployment` 및 `ReplicaSet` (레거시 리소스 레플리케이션컨트롤러(ReplicationController)를 대체). Deployment 는 Deployment 의 모든 Pod 가 필요 시 교체 또는 상호 교체 가능한 경우, 클러스터의 스테이트리스 애플리케이션 워크로드를 관리하기에 적합합니다.

- `StatefulSet`는 어떻게든 스테이트(state)를 추적하는 하나 이상의 파드를 동작하게 해준다. 예를 들면, 워크로드가 데이터를 지속적으로 기록하는 경우, 사용자는 Pod 와 PersistentVolume을 연계하는 StatefulSet 을 실행할 수 있다. 전체적인 회복력 향상을 위해서, StatefulSet 의 Pods 에서 동작 중인 코드는 동일한 StatefulSet 의 다른 Pods 로 데이터를 복제할 수 있습니다.

- `DaemonSet`은 노드-로컬 기능(node-local facilities)을 제공하는 Pods 를 정의한다. 이러한 기능들은 클러스터를 운용하는 데 기본적인 것일 것이다. 예를 들면, 네트워킹 지원 도구 또는 add-on 등이 있다. DaemonSet 의 명세에 맞는 노드를 클러스터에 추가할 때마다, 컨트롤 플레인은 해당 신규 노드에 DaemonSet 을 위한 Pod 를 스케줄합니다.

- `Job` 및 `CronJob`은 실행 완료 후 중단되는 작업을 정의한다. CronJobs 이 스케줄에 따라 반복되는 반면, 잡은 단 한 번의 작업을 나타냅니다.

---
layout: default
title: 11.1 시스템
nav_order: 1
parent: 11. 모니터링&알림
---

# 시스템
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Cluster
{: .label .label-blue }

Namespace
{: .label .label-green }
</div>

---

## 시스템

Cluster에서는 Overview/Pods/Nodes/Namespaces/Deployments/Statefulsets/GPU 모니터링 지표를 제공합니다.


## 메뉴이동
`모니터링` ➡ `시스템`

![sys.png](/assets/images/monitoring/sys.png)

---

**차트 이미지 다운로드**

차트 우측 상단 햄버거 버튼을 클릭하면 SVG, PNG, CSV파일로 차트를 다운 받을수 있습니다.

![download.png](/assets/images/monitoring/download.png)

**새로고침 주기**

- 새로고침 주기는 초단위(5,10,30) 분단위(1,5,15,30) 시단위(1,2) 일단위(1)로 설정할 수 있으며 원하는 주기를 선택하면 새로고침 주기가 적용됩니다.
- 새로고침 주기 설정 좌측 버튼을 클릭하면 즉시 새로고침 됩니다.

![reload.png](/assets/images/monitoring/reload.png)


---

## Overview

CPU/Memory/Network 사용량 차트와 네임스페이스별 CPU/Memory/Network 사용량을 테이블로 보여줍니다.

![system_overview.png](/assets/images/monitoring/system_overview.png){: width="800" }


| 항목  | 설명 |
|---|---|
| NAMESPACE   | Namespace 명 |
| CPU USAGE   | CPU 사용량 |
| CPU REQUEST   | CPU Quota Request 용량 |
| CPU LIMITS   | CPU Quota Limits 용량 |
| MEMORY USAGE  | Memory 사용량 |
| MEMORY REQUEST   | Memory Quota Request 용량 |
| MEMORY LIMITS   | Memory Quota Limits 용량 |
| NETWORK IN  | Network Inbound 속도  |
| NETWORK OUT   | Network Outbound 속도 |


---

## Pods

Node/Namespace 를 선택하여 Node/Namespace 별로 Pod 정보를 확인할 수 있습니다.

![system_pods.png](/assets/images/monitoring/system_pods.png){: width="800" }


| 항목  | 설명 |
|---|---|
| 네임스페이스 | 네임스페이스 명   |
| 이름   | 파드 명  |
| 상태  | 포드 상태  |
| 노드  | 포드가 배포된 노드명  |
| 파드 IP  | 파드 고유 IP  |
| 컨테이너  | 파드의 Running 및 전체 컨테이너 갯수  |
| 리소스 할당량 R/L(CPU)  | 파드의 CPU 리소스 Requests/Limits 할당량입니다. 파드의 전체 컨테이너가 CPU 리소스 양을 지정한 경우 표시됩니다. 그외의 경우 "-"로 표시  |
| 리소스 할당량 R/L(MEMORY)  | 파드의 Memory 리소스 Requests/Limits 할당량입니다. 파드의 전체 컨테이너가 Memory 리소소 양을 지정한 경우 표시됩니다. 그외의 경우 "-"로 표시   |
| CPU 사용량 | 파드의 CPU 사용량이며 CPU 리소스 할당량을 제한한 경우 Limits 기준으로 파드의 CPU 사용률을 표시합니다. 그외의 경우 파드가 배포된 노드의 CPU 리소스 기준으로 CPU 사용률을 표시  |
| MEMORY 사용량 | 파드의 Memory 사용량이며 Memory 리소스 할당량을 제한한 경우 Limits 기준으로 파드의 Memory 사용률을 표시합니다. 그외의 경우 파드가 배포된 노드의 Memory 리소스 기준으로 Memory 사용률을 표시  |
| NETWORK RX | 파드의 Network Received 속도 |
| NETWORK TX | 파드의 Network Transmitted 속도 |
| 재시작 | 파드의 재시작 횟수  |
| AGE | 파드의 실행된 시간 |

---

## Nodes

Node를 다중 선택하여 검색 가능하며 선택된 Node 목록의 CPU/Memory/Disk/Network Received/Network Transmitted 모니터링 차트를 제공합니다.

![system_nodes.png](/assets/images/monitoring/system_nodes.png){: width="800" }

---

## Namespaces 

Namespace 를 선택하여 Namespace 별로 CPU 사용량과 상세 정보 및 Memory 사용량과 상세 정보를 확인할 수 있습니다.

- CPU

| 항목  | 설명 |
|---|---|
| Namespaces   | Namespace 명  |
| CPU Usage   | CPU 사용량  |
| CPU Request   | CPU Quota Request 용량  |
| CPU Request(%)   | CPU Quota Request 비율  |
| CPU Limits   | CPU Quota Limits 용량   |
| CPU Limits(%)  | CPU Quota Limits 비율  |

- Memory

| 항목  | 설명 |
|---|---|
| Namespaces | Namespace 명 |
| Memory Usage | Memory 사용량 |
| Memory Request | Memory Quota Request 용량 |
| Memory Request(%) | Memory Quota Request 비율  |
| Memory Limits | Memory Quota Limits 용량 |
| Memory Limits(%) | Memory Quota Limits 비율 |

---

## Deployments

Namespace/Deployment를 선택하여 Namespace/Deployment의 Pod들을 시스템 모니터링 정보를 확인할 수 있습니다.

- CPU
- Memory
- Network Tx
- Network Rx

특정 파드 선택시 특정 파드의 모니터링 정보만 확인할 수도 있습니다.

![system_deployments.png](/assets/images/monitoring/system_deployments.png){: width="800" }

---

## StatefulSets

Namespace/Statefulset를 선택하여 Namespace/Statefulset의 Pod들을 시스템 모니터링 정보를 확인할 수 있습니다.

- CPU
- Memory
- Network Tx
- Network Rx

특정 파드 선택시 특정 파드의 모니터링 정보만 확인할 수도 있습니다.

![system_statefulsets.png](/assets/images/monitoring/system_statefulsets.png){: width="800" }

---

## GPU

GPU 노드가 존재할 경우 GPU 노드를 선택하여 GPU 모니터링 정보를 확인할 수 있습니다.

- GPU Memory Usage
- GPU Utillization
- GPU Power Usage
- GPU Mem Cppy Utillization
- GPU Temperature
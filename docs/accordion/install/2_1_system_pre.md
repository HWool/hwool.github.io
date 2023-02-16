---
layout: default
title: 2.4.1 💻시스템 요구사항
nav_order: 4
parent: 2.4 Accordion 설치
grand_parent: 2. Accordion v2
---

# 2-4-1 시스템 요구사항
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 💻시스템 요구사항
- Accordion 서버는 가상 시스템 또는 물리 시스템 준비
- Accordion 서버를 설치하기 위해서는 Master 서버 3대와 서비스를 수행 할 Node 서버 2대 이상 있어야 합니다.
- Master, Node 서버 간에는 네트워크 사전작업 준비
- Master 서버와 Node 서버 간에 ssh 접근이 가능해야 합니다. (root 접속필요)
- Master/Node 서버 시간은 동일해야 합니다.


**OS 운영체제**
- CentOS : 7.4 이상 (CentOS 8 미지원)
- RHEL : 7.4 또는 8.4 이상
- Ubuntu: 18.04 이상
- OracleLinux: 7.4 또는 8.4 이상
- RHCK 커널 지원, UEK 커널 미지원

**노드별 시스템 요구사항**

| 구분        | CPU | MEMORY | DISK |
|:-------------|:------------------|:------|:------|:------|
| Master       | 최소 8core | 최소 16GB  | 최소 500GB |
| Node(s)      | 최소 8core   | 최소 16GB | 최소 300GB |

---

## 📡 아코디언 방화벽(calico v2)

**마스터노드**

| Protocol	| Direction | 	Port Range |	Source	| Destination | Purpose |
|:----------|:----------|:-------------|:-----------|:------------|:--------|
| TCP	| Inbound	| 6443	| 워커노드	| 마스터노드	| Kubernetes API server |
| TCP	| Inbound	| 2379-2380	| 워커노드	| 마스터노드	| etcd server client API |
| TCP	| Inbound	| 10250	| 워커노드	| 마스터노드	| Kubelet API |
| TCP	| Inbound	| 10251	| 워커노드	| 마스터노드	| kube-scheduler |
| TCP	| Inbound	| 10252	| 워커노드	| 마스터노드	| kube-controller-manager |
| TCP	| Inbound	| 10255	| 워커노드	| 마스터노드	| worker node kubelet healthcheck read only |
| TCP	| Inbound	| 30000-32767	| 클라이언트	| 마스터노드	| NodePort Services |
| TCP	| Inbound	| 179	| 모든서버	| 모든서버	| Calico networking (BGP) |
| UDP	| Inbound	| 4789	| 모든서버	| 모든서버	| Calico networking with VXLAN enabled |
| Protocol	| Inbound	| 4	| 모든서버	| 모든서버	| Calico networking IP in IP (encapsulation) |
| TCP	| Inbound	| 5473	| 모든서버	| 모든서버	| Calico networking with Typha enabled |
| TCP	| Inbound	| 9100	| 모든서버	| 모든서버	| node exporter |
| TCP	| Inbound	| 8443	| 워커노드	| 마스터노드	| Kubernetes API server(마스터노드 3중화) |
| TCP	| Inbound	| 5000	| 워커노드	| 마스터노드	| Accordion local Infra-registry |
					
**워커노드**

| Protocol	| Direction | 	Port Range |	Source	| Destination | Purpose |
|:----------|:----------|:-------------|:-----------|:------------|:--------|
| TCP	| Inbound	| 10250	| 마스터노드	| 워커노드 | Kubelet API | 
| TCP	| Inbound	| 10255	| 마스터노드	| 워커노드	| worker node kubelet healthcheck read only | 
| TCP	| Inbound	| 30000-32767	| 클라이언트	| 워커노드	| NodePort Services | 
| TCP	| Inbound	| 179	| 모든서버	| 모든서버	| Calico networking (BGP) | 
| Protocol	| Inbound	| 4	| 모든서버	| 모든서버	| Calico networking IP in IP (encapsulation) | 
| UDP	| Inbound	| 4789	| 모든서버	| 모든서버	| Calico networking with VXLAN enabled | 
| TCP	| Inbound	| 5473	| 모든서버	| 모든서버	| Calico networking with Typha enabled | 
| TCP	| Inbound	| 9100	| 모든서버	| 모든서버	| node exporter | 
| TCP	| Inbound	| 80	| 클라이언트	| 워커노드	| App service(nginx-ingress Hostport) | 
| TCP	| Inbound	| 443	| 클라이언트	| 워커노드	| App service(nginx-ingress Hostport ) | 
					
**아코디언에서 사용하는 NodePort 리스트**					

| Protocol	| Direction | 	Port Range | Purpose |
|:----------|:----------|:-------------|:--------|
| TCP	| Inbound	| 30000			| Accordion console |
| TCP	| Inbound	| 30001			| user-registry |
| TCP	| Inbound	| 30002			| thanos-store-gateway | 
| TCP	| Inbound	| 30003			| thanos-sidecar | 
| TCP	| Inbound	| 30443			| member-agent | 


---
layout: default
title: 2.2 Accordion 아키텍쳐
nav_order: 2
parent: 2. Accordion v2
---

# 2.2 📖 아코디언v2 아키텍쳐
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## 📖 아코디언v2 아키텍쳐

아코디언은 마스터 노드 3대, 인프라 노드(권고), 워커노드로 구성되어 있습니다.

![acc-5.png](/assets/images/accordion/acc-5.png)

Master Node : Kuberentes 를 제어하는 노드
Infra Node : 클러스터를 관리를 위한 CI/CD, Logging, Monitoring, Alarm 기능을 위한 노드
Worker Node : 애플리케이션 서비스 노드


---

## 멀티클러스터 통합 관리
개발, 테스트, 운영, 외부 클라우드, 분리된 네트워크 망 등에 분산 구성된 클러스터를 단일 콘솔로 관리할 수 있고 Host Cluster를 통해 K8S 클러스터를 매우 쉽게 배포할 수 있습니다.

![acc-7.png](/assets/images/accordion/acc-7.png)


**클러스터별 역할**

- Host Cluster : 멀티클러스터를 관리용 클러스터로 Cluster간 앱 배포, 통합 권한 설정 및 모니터링 기능을 제공합니다.
- Member Cluster : 서비스 클러스터로 클러스터마다 설치된 에이전트를 통해 Host Cluster의 명령을 받게 됩니다.


---

## CI/CD pipeline
내장된 CI/CD pipeline을 통해 멀티 클라우드 환경에서 컨테이너를 쉽게 배포할 수 있습니다.

![acc-10.png](/assets/images/accordion/acc-10.png)

---

## 아코디언 솔루션 구성

아코디언은 인증, CI/CD, 컨테이너 관리, 모니터링 모듈로 구성되어 있습니다.

![acc-6.png](/assets/images/accordion/acc-6.png)

**Identity Module**

사용자 관리 인증/인가 접근제어 SSO

- Keycloak
- Accordion Gateway

**CI/CD Automation Module**

- Argo CI/CD
- Docker Registry / Harbor

**Container Orchestration**

- Kubernetes
- Calcio/Weave
- Accordion console
- Catalog & Helm
- Istio & Kiali

**Observability Module**

- Thanos & Prometheus
- FileBeat & Opensearch
- Scouter APM
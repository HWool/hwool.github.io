---
layout: default
title: 5.1 Helm
nav_order: 1
has_children: true
parent: 5. 애플리케이션
---

# Helm
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

## Helm 이란?
Helm은 Kubernetes 애플리케이션 관리를 지원합니다. 
Helm 차트는 가장 복잡한 Kubernetes 애플리케이션을 정의, 설치 및 업그레이드하는 데 도움이 됩니다.

![helm-1.png](/assets/images/application/helm/helm-1.png)


[https://helm.sh/](https://helm.sh/)

**복잡성 관리**

차트는 가장 복잡한 앱도 설명하고 반복 가능한 애플리케이션 설치를 제공하며 단일 권한 지점 역할을 합니다.

**쉬운 업데이트**

인플레이스(in-place) 업그레이드 및 사용자 지정 후크를 사용하여 업데이트의 고통을 덜어줍니다.

**간단한 공유**

차트는 공용 또는 개인 서버에서 쉽게 버전을 지정하고 공유하고 호스팅할 수 있습니다.

**롤백**

helm rollback이전 버전의 릴리스로 쉽게 롤백하는 데 사용 합니다.


---

## 아코디언 Helm
Kubernetes 환경에서 Helm을 사용하기 위해서는 `helm cli`을 설치하고 차트를 관리해야합니다.
아코디언은 이러한 준비 과정을 단축시켜 사용자가 바로 앱을 배포할 수 있도록 제공합니다.

![helm-2.png](/assets/images/application/helm/helm-2.png)

- Helm 3.5.1 지원
- 아코디언에서 간편하게 차트 배포
- 효율적인 차트 관리
- 안전한 비공개 저장소

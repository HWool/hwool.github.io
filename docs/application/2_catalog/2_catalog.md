---
layout: default
title: 5.2 카탈로그
nav_order: 2
has_children: true
parent: 5. 애플리케이션
---

# 카탈로그 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Namespace
{: .label .label-green }
</div>

## 카탈로그 

카탈로그는 아코디언의 가장 중요한 구성 요소 중 하나입니다. 카탈로그는 서비스를 패키징하고 배포 및 관리하는 데 최적화된 방법입니다. 


![catalog-1.png](/assets/images/application/catalog-1.png){: width="800" }

- 간편하게 애플리케이션 배포
- CI CD 파이프라인 연계
- 앱 라이프사이클 관리	
- 멀티 클러스터 배포


---

## 카탈로그 특징

| 특징        |  설명  |
|:------------|:-------|
| 다양한 쿠버네티스 리소스 배포 | 디플로이먼트, 스테이트풀셋 등 코어 리소스를 포함하여 커스텀 리소스 배포 가능 |
| 지속적인 배포 | 카탈로그로 배포한 리소스 집합에 대해 업그레이드 배포 등 라이플사이클을 관리 |
| 배포 이력 관리 | 배포를 수행한 시점의 스펙과 수행을 요청한 사용자 등의 이력을 관리 |
| 재배포와 롤백 | 기존에 성공적으로 배포된 이력에 대해 재배포와 롤백의 기능을 제공 |
| 다양한 배포 정책 | 단일 카탈로그를 구성하는 리소스들에 대해서도 리소스 각자의 배포 정책 적용 |
| 멀티클러스터 배포 지원 | 아코디언에서 관리되는 클러스터에 대해 서로 다른 네임스페이스와 클러스터에 동일한 배포와 라이플사이클을 적용 |
| 파이프라인 연계 | 소스에서 컨테이너 이미지를 만들거나, 승인을 포함한 배포 등 다양한 파이프라인 연계를 통해서 배포 가능 |

---

## Helm vs Catalog

![helm_catalog.png](/assets/images/application/helm/helm_catalog.png){: width="800" }

카탈로그와 카탈로그 템플릿의 관계는 헬름 릴리즈와 헬름 차트의 관계와 유사합니다. 카탈로그 템플릿은 배포에 필요한 쿠버네티스 리소스 정보와 변수 정보같은 카탈로그 스펙을 가지고 있습니다. 사용자가 카탈로그 템플릿으로 카탈로그를 생성하면 시스템이 카탈로그 정보를 이용해 애플리케이션을 배포합니다.

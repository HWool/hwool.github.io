---
layout: default
title: 5.1.2 헬름
nav_order: 3
has_children: true
grand_parent: 5. 애플리케이션
parent: 5.1 Helm
---

# 헬름
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


## Helm Chart

---
## 메뉴이동
`애플리케이션` ➡ `헬름`

![helm_menu.png](/assets/images/application/helm/helm_menu_02.png)

---

## 화면구성
헬름 설치를 진행할 수 있으며 배포된 워크로드 정보를 보여주며 헬름 업그레이드이 가능합니다.

![helmchart-01.png](/assets/images/application/helm/helmchart-01.png){: width="800" }


**Resources**

`Resources`에서는 헬름으로 배포된 워크로드 정보를 제공합니다.
![helmchart-02.png](/assets/images/application/helm/helmchart-02.png){: width="800" }


**Status**

`Status`에서는 헬름의 상태와 `Value.yaml` 편집을 통해 헬름 업그레이드가 가능합니다.
![helmchart-03.png](/assets/images/application/helm/helmchart-03.png){: width="800" }

**History**

`History`에서는 배포 이력 정보를 제공하고 특정 버전으로 `롤백`을 지원합니다.
![helmchart-04.png](/assets/images/application/helm/helmchart-04.png){: width="800" }


---


## 헬름 런치

`런치` 를 클릭하면 헬름 저장소에 등록된 차트를 배포할 수 있습니다.

![helm-3.png](/assets/images/application/helm/helm-3.png){: width="800" }

**README**

차트의 README 파일을 확인할 수 있습니다.

![helm-4.png](/assets/images/application/helm/helm-4.png){: width="800" }

**Value.yaml**

차트의 `value.yaml` 을 편집할 수 있습니다.
배포할 앱 이름을 입력하고 `런치` 를 클릭하면 앱 배포가 시작됩니다.

![helm-5.png](/assets/images/application/helm/helm-5.png){: width="800" }


**헬름 앱**

배포된 앱은 `헬름 앱`에서 확인할 수 있습니다.
네임스페이스, 상태, 차트, 앱버전 정보를 제공합니다.

![helm-6.png](/assets/images/application/helm/helm-6.png){: width="800" }

**헬름 앱 리소스**

`헬름 앱`을 클릭하면 자세한 배포 리소스 정보를 확인할 수 있습니다. 
`헬름 앱 리소스` 에서는 워크로드와 yml 내용을 제공합니다.

![helm-7.png](/assets/images/application/helm/helm-7.png){: width="800" }

---

## 연습문제

**1. 헬름 저장소에 bitnami 저장소를 등록하세요.**

```
name: bitnami
url: https://charts.bitnami.com/bitnami
```

**2. apache 헬름을 배포하세요.**

```
Value.yaml
name: apache
replicaCount: 2
service type: NodePort
```

**3. 배포된 헬름의 상태를 확인하세요.**
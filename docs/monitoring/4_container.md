---
layout: default
title: 11.4 컨테이너 로그
nav_order: 1
parent: 11. 모니터링&알림
---

# 컨테이너 로그
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

## 컨테이너 로그

Cluster 내에 있는 pod들의 container 로그와 시간별 로그 통계를 제공합니다. 범위설정에서 설정한 간격으로 통계를 나타내며 개수와 총 개수를 나타내며 Node, Namespace, Pod, Container 의 이름과 로그를 제공합니다.

---
## 메뉴이동
`모니터링` ➡ `컨테이너 로그`

![sys.png](/assets/images/monitoring/sys.png)

---

## 화면 구성

![container_log.png](/assets/images/monitoring/container_log.png){: width="800" }

로그 클릭 시 우측에 자세한 로그내용이 나옵니다.

![container_log_detail.png](/assets/images/monitoring/container_log_detail.png){: width="800" }

---

**검색조건**

검색조건은 아래와 같이 총 4가지에 해당합니다.

- namespace
- nodeName
- podName
- containerName

![container_log_condition.png](/assets/images/monitoring/container_log_condition.png)

**새로고침 주기**

- 새로고침 주기는 초단위(5,10,15)로 설정할 수 있으며 원하는 주기를 선택하면 새로고침 주기가 적용됩니다.
- 새로고침 주기 설정 좌측 버튼을 클릭하면 즉시 새로고침 됩니다.

**검색 입력 방법**

검색어에 포함되는 내용을 조회합니다.

검색어 검색 시 여러개의 조건에 맞는 검색을 할 수 있습니다.
검색조건 입력하면 검색창 하단의 검색조건이 나타납니다. 검색 조건을 선택하고 검색 조건의 검색어를 입력하여 검색합니다. 또는 검색조건과 검색어를 직접 입력하여 검색합니다.
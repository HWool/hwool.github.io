---
layout: default
title: 3.3 네임스페이스 대시보드
nav_order: 3
parent: 3. 대시보드
---

# 3.3 네임스페이스 대시보드
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


## 네임스페이스 대시보드
네임스페이스 대시보드는 네임스페이스에 대한 정보와 시스템 리소스를 확인할 수 있습니다.

![3_ns_dashboard_main.png](/assets/images/dashboard/3_ns_dashboard_main.png){: width="800" }

---

## 메뉴이동
`네임스페이스 대시보드`

![nd.png](/assets/images/dashboard/nd.png)

---

## Namespace Info
네임스페이스 대시보드는 네임스페이스에 대한 정보와 시스템 리소스를 확인할 수 있습니다.

![3_ns_info.png](/assets/images/dashboard/3_ns_info.png){: width="800" }


|항목|설명|
|:--|:--|
|Name|Namespace 이름|
|Enabled|사용중 여부 Active, Terminating 두가지가 있으며 <br> - Active : 사용 중 <br> - Terminating : 네임스페이스가 삭제되고 있는 중 |
|Created|생성된 시간|
|CPU|5분간 CPU 사용률|
|Average CPU|평균 CPU 사용률|
|Memory|5분간 Memory 사용률|
|Average Memory|평균 Memory 사용률|
|Network Usage|5분간 네트워크 사용률|
|Average Network|평균 네트워크 사용률|


---

## Namespace CPU/Memory Usage Top5
네임스페이스 내에서 CPU 사용량이 가장 많은 Pod 5개, Memory 사용량이 가장 많은 Pod 5개를 확인할 수 있습니다.

![3_ns_usage_top5.png](/assets/images/dashboard/3_ns_usage_top5.png){: width="800" }

---

## Pods
네임스페이스에 생성된 Pod들의 기본 정보들을 확인할 수 있습니다.

![3_ns_pods.png](/assets/images/dashboard/3_ns_pods.png){: width="800" }

|항목|설명|
|--|--|
|이름|Pod의 이름|
|상태|Pod의 현재 상태|
|RESTARTS|Pod의 재시도 횟수|
|POD IP|Pod의 IP|
|NODE|Pod가 배포된 Node의 이름|


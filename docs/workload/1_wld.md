---
layout: default
title: 6.1 워크로드대시보드
nav_order: 1
parent: 6. 워크로드
---

# 워크로드대시보드
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

## 워크로드
워크로드는 Kuberenetes에서 구동되는 애플리케이션을 의미합니다. 
Kuberenetes에서 워크로드는 파드의 집합에서 실행되며 파드는 실행 중인 컨테이너의 집합입니다. 

**워크로드의 종류**

- 디플로이먼트
- 스테이트풀셋
- 데몬셋
- 잡
- 크론잡
- 파드

---


## 메뉴이동
`워크로드` ➡ `워크로드 대시보드`

![wl-wld.png](/assets/images/workload/wl-wld.png)

---


## 워크로드 대시보드
워크로드 대시보드는 클러스터에 배포된 워크로드 상태 정보를 제공합니다.

**워크로드 상태 정보**

- Running, Pending, Succeeded, NotRunning, Warning

![wld-status.png](/assets/images/workload/wld-status.png)

![wl-002.png](/assets/images/workload/wl-002.png){: width="800" }

**워크로드 상세정보**

![wl-003.png](/assets/images/workload/wl-003.png){: width="800" }


차트에서 워크로드를 선택하면 해당 워크로드에 대한 상세 정보를 조회할 수 있습니다.
제공되는 정보는 다음과 같습니다.

- Kind
- Name
- Namespace
- Status
- Created Time
- Event Message


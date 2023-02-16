---
layout: default
title: 6.3 디플로이먼트
nav_order: 3
parent: 6. 워크로드
---

# 디플로이먼트
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

## 디플로이먼트(Deployment)
디플로이먼트(Deployment)는 Kuberenetes에서 주로 사용되는 오브젝트입니다. ReplicaSet을 이용하여 Pod을 업데이트 가능하며 이력을 저장하여 Rollback하거나 특정 버전 revision으로 돌아갈 수 있습니다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80


{% endhighlight %}
   
</details>

---
## 메뉴이동
`워크로드` ➡ `디플로이먼트`

![wl-deploy.png](/assets/images/workload/wl-deploy.png)

---

## 화면구성
배포된 디플로이먼트 정보를 제공합니다.

![wl-009.png](/assets/images/workload/wl-009.png){: width="800" }

---

## 디플로이먼트 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 디플로이먼트 리소스 정보를 입력하여 생성할 수 있습니다.

![wl-010.png](/assets/images/workload/wl-010.png){: width="800" }

---

## Autoscale
`Autoscale` 버튼으로 디플로이먼트에 대한 오토스케일 설정이 가능합니다. 
오토스케일은 발생 기준에 따라 `Resource(메트릭 기준의 오토스케일)`과 `Time Based(시간 기준의 오토스케일)`로 나눌 수 있습니다.

![wl-011.png](/assets/images/workload/wl-011.png){: width="800" }

---

## Time Based(시간 기준 오토스케일)
특정 시간에 대해 파드의 개수를 스케일링을 지원합니다.
- 시작 Schedule: 스케일링 시작 시간 설정
- 시작 Target Pods: 스케일링 시작 시 목표 파드 개수
- 종료 Schedule: 스케일링 종료 시간 설정
- 종료 Target Pods: 스케일링 종료 시 목표 파드 개수

![wl-013.png](/assets/images/workload/wl-013.png){: width="800" }

시간 기준 오토스케일 설정 시 아래와 같이 크론 스케줄 포맷에 의해 작성합니다.

| 시간        | 허용 가능 값         | 허용 가능 특수문자 |
|:-------------|:------------------|:------|
| 초           | 0-59      | * / , -  |
| 분           | 0-59      | * / , -  |
| 시           | 0-23      | * / , -  |
| 일자         | 1-13      | * / , - ?  |
| 달           | 1-12 or JAN-DEC      | * / , -  |
| 요일         | 0-6 or SUN-SAT      | * / , - ?  |

시간 기준 오토스케일 설정의 예는 아래와 같습니다.
```
시작 Schedule : 0 1 9 1 11 *
시작 Target Pods : 3
종료 Schedule : 0 1 9 1 12 *
종료 Target Pods : 1

= 매년 11월 1일 오전 9시 1분에 파드가 3개로 늘어났다가 매년 12월 1일 오전 9시 1분에 파드가 1개로 줄어든다.
```

---

## Resource(메트릭 기준 오토스케일)
메트릭 기준 오토스케일의 경우 기본적으로 CPU와 메모리 사용량에 따라 적용 가능합니다. 아코디언에서는 그 외에 스카우터에서 수집한 메트릭에 의한 스케일링도 가능하며 해당 메트릭은 다음과 같습니다.
- Min Pods: 최소 파드의 개수
- Max Pods: 스케일링 시 최대 파드의 개수
- 오토스케일 기준: 스케일링 기준이 되는 메트릭
- 설정값: 스케일링이 발생하는 임계치

![wl-012.png](/assets/images/workload/wl-012.png){: width="800" }

**오토스케일기준**
- CPU
- Memory
- apm_TPS
- apm_ActiveService
- apm_ElapsedTime
- apm_GcTime

![wl-014.png](/assets/images/workload/wl-014.png){: width="600" }{: .center}


| 조건        | 사용 가능한 오토스케일 기준   | 
|:-------------|:------------------|
| 파드리소스 O / APM 모니터링 O | CPU, Memory + apm_ActiveService, apm_TPS, apm_GcTime, apm_ElapsedTime |
| 파드리소스 O / APM 모니터링 X | CPU, Memory |
| 파드리소스 X / APM 모니터링 O | apm_ActiveService, apm_TPS, apm_GcTime, apm_ElapsedTime |
| 파드리소스 X / APM 모니터링 X | 메트릭 기준의 오토스케일 사용 불가 |

## 디플로이먼트 삭제
삭제하려는 디플로이먼트를 선택하고 우측의 삭제 버튼을 선택합니다.

![deployment-delete.png](/assets/images/workload/deployment-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 파드가 있습니까?**

<input />

**2. 클러스터에 몇 개의 디플로이먼트가 있습니까?**

<input />

**3. 아래 속성으로 새 디플로이먼트를 만드세요.**

```
- name: httpd-frontend; 
- replicas: 3; 
- image: httpd:2.4-alpine
```

**4. 생성한 디플로이먼트를 삭제하세요.**
---
layout: default
title: 6.7 크론잡
nav_order: 7
parent: 6. 워크로드
---

# 크론잡
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


## 크론잡(Cronjobs)
크론잡은 반복 일정에 따라 잡을 생성합니다.
하나의 크론잡 오브젝트는 크론탭 (크론 테이블) 파일의 한 줄과 같습니다. 크론잡은 잡을 크론 형식으로 쓰여진 주어진 일정에 따라 주기적으로 동작시킵니다.

각 작업은 무기한 반복되도록 구성해야 합니다.(예: 1일/1주/1달마다 1회). 
작업을 시작해야 하는 해당 간격 내 특정 시점을 정의할 수 있습니다.

**크론잡 대표적인 용도**

- 백업
- 리포트 생성등 정기적 작업


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: batch/v1
kind: CronJob
metadata:
  name: hello
spec:
  schedule: "*/1 * * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: hello
            image: busybox
            imagePullPolicy: IfNotPresent
            command:
            - /bin/sh
            - -c
            - date; echo Hello from the Kubernetes cluster
          restartPolicy: OnFailure


    
{% endhighlight %}
   
</details>

---

## 메뉴이동
`워크로드` ➡ `크론잡`

![wl-cj.png](/assets/images/workload/wl-cj.png)

---

## 화면구성
배포된 크론잡 정보를 제공합니다.

![wl-021.png](/assets/images/workload/wl-021.png){: width="800" }

---

## 크론잡 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 크론잡 리소스 정보를 입력하여 생성할 수 있습니다.
크론잡은 `FORM`과 `YAML` 형식으로 생성 가능합니다.

**일반 설정**

크론잡 이름, 네임스페이스를 지정하고 원하는 스케쥴과 재시작 정책을 설정할 수 있습니다.

- 크론잡 이름
- 네임스페이스 
- 스케쥴
- 재시작 정책(restartPolicy)
  + OnFailure
  + Never

![wl-022.png](/assets/images/workload/wl-022.png){: width="800" }


**크론 스케줄 문법**
```
# ┌───────────── 분 (0 - 59)
# │ ┌───────────── 시 (0 - 23)
# │ │ ┌───────────── 일 (1 - 31)
# │ │ │ ┌───────────── 월 (1 - 12)
# │ │ │ │ ┌───────────── 요일 (0 - 6) (일요일부터 토요일까지;
# │ │ │ │ │                                   특정 시스템에서는 7도 일요일)
# │ │ │ │ │
# │ │ │ │ │
# * * * * *
```


**컨테이너 설정**

실행되는 파드의 컨테이너 설정하면 크론잡 생성이 가능합니다.

- 컨테이너 이름
- 이미지
- arg 또는 command

![wl-023.png](/assets/images/workload/wl-023.png){: width="800" }

---
## 크론잡 수정
수정하려는 크론잡을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영한다.

---

## 크론잡 삭제
삭제하려는 크론잡을 선택하고 우측의 삭제 버튼을 선택합니다.
모달에서 네임스페이스와 크론잡 이름을 입력하여 삭제합니다.

![cronjob-delete.png](/assets/images/workload/cronjob-delete.png){: width="800" }


---
## 연습문제

**1. 클러스터에 몇 개의 크론잡이 있습니까?**
<input />

**2. 아래 속성으로 새 크론잡을 만드세요.**

```
- name: hello; 
- image: busybox
- schedule: "*/1 * * * *"
- command: ["/bin/sh", "-c", "date; echo Hello from the Kubernetes cluster"]
```

**3. 생성한 크론잡의 결과 값을 무엇입니까?**

<input />

**4. 생성한 크론잡잡을 삭제하세요.**
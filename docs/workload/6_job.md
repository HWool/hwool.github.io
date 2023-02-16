---
layout: default
title: 6.6 잡
nav_order: 6
parent: 6. 워크로드
---

# 잡
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

## 잡(Job)
잡에서 하나 이상의 파드를 생성하고 지정된 수의 파드가 성공적으로 종료될 때까지 계속해서 파드의 실행을 재시도합니다. 

파드가 성공적으로 완료되면, 성공적으로 완료된 잡을 추적합니다. 지정된 수의 성공 완료에 도달하면, 작업(즉, 잡)이 완료됩니다. 잡을 삭제하면 잡이 생성한 파드가 정리됩니다. 작업을 일시 중지하면 작업이 다시 재개될 때까지 활성 파드가 삭제됩니다.

간단한 사례는 잡 오브젝트를 하나 생성해서 파드 하나를 안정적으로 실행하고 완료하는 것입니다. 첫 번째 파드가 실패 또는 삭제된 경우(예로는 노드 하드웨어의 실패 또는 노드 재부팅) 잡 오브젝트는 새로운 파드를 기동시킵니다.
잡을 사용하면 여러 파드를 병렬로 실행할 수도 있습니다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: batch/v1
kind: Job
metadata:
  name: pi
spec:
  template:
    spec:
      containers:
      - name: pi
        image: perl
        command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
      restartPolicy: Never
  backoffLimit: 4

{% endhighlight %}
   
</details>


---

## 메뉴이동
`워크로드` ➡ `잡`

![wl-job.png](/assets/images/workload/wl-job.png)

---

## 화면구성

배포된 잡 정보를 제공합니다.

![wl-017.png](/assets/images/workload/wl-017.png){: width="800" }

---

## 잡 생성
`+생성`을 선택하면 나타나는 모달에서 쿠버네티스 잡 리소스 정보를 입력하여 생성할 수 있습니다.

![wl-018.png](/assets/images/workload/wl-018.png){: width="800" }


**잡 실행이력**

잡이 생성되면 우측 영역에 `파드` 탭의 `Pod History`에 생성된 잡 파드를 확인할 수 있습니다.

![wl-019.png](/assets/images/workload/wl-019.png){: width="800" }

잡 실행이력에서는 다음 정보를 제공합니다.

- 파드 이름
- 파드 상태
- 파드 시작시간
- 파드 로그

`삭제` 버튼을 클릭하면 파드 삭제가 가능합니다.

---

## 잡 수정
수정하려는 잡을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.

---

## 잡 삭제
삭제하려는 잡을 선택하고 우측의 삭제 버튼을 선택합니다.
모달에서 네임스페이스와 잡 이름을 입력하여 삭제합니다.

![job-delete.png](/assets/images/workload/job-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 잡이 있습니까?**

<input />

**2. 아래 속성으로 새 잡을 만드세요.**

```
- name: pi
- image: perl
- command: ["perl",  "-Mbignum=bpi", "-wle", "print bpi(2000)"]
```

**3. 생성한 잡의 결과 값을 무엇입니까?**

<input />

**4. 생성한 잡을 삭제하세요.**
---
layout: default
title: 6.2 파드
nav_order: 2
parent: 6. 워크로드
---

# 파드
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

## 파드(Pod)
파드(Pod)는 Kubernetes에서 관리하는 가장 작은 배포 단위입니다.
Kubernetes와 Pod는 한 개 또는 여러 개의 컨테이너를 포함합니다.
파드는 하나 이상의 컨테이너의 그룹이며 스토리지 및 네트워크를 공유하고, 해당 컨테이너를 구동하는 방식에 대한 명세를 갖습니다. 


![](https://d33wubrfki0l68.cloudfront.net/aecab1f649bc640ebef1f05581bfcc91a48038c4/728d6/images/docs/pod.svg){: width="600" }

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: v1
kind: Pod
metadata:
  name: nginx
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
`워크로드` ➡ `파드`

![wl-pod.png](/assets/images/workload/wl-pod.png)

---
## 화면구성
배포된 파드 정보를 제공합니다.
탭을 이용해 파드에 대한 쿠버네티스 리소스 정보, 컨테이너 로그 조회 및 터미널 접속이 가능합니다. 
컨테이너 로그 조회와 터미널 접속은 파드의 컨테이너 별로 가능합니다.

![wl-004.png](/assets/images/workload/wl-004.png){: width="800" }

**파드 터미널**

탭영역에서 파드 선택 후, `TERMINAL` 탭을 선택하면 파드 터미널 접근 가능합니다.

![wl-006.png](/assets/images/workload/wl-006.png){: width="800" }

우측상단 `새창열기` 버튼을 클릭하면 터미널 새창이 열리게 됩니다.

![wl-007.png](/assets/images/workload/wl-007.png){: width="800" }

**파드 로그**

탭영역에서 파드 선택 후, `LOG` 탭을 선택하면 파드 로그를 확인할 수 있습니다.

![wl-005.png](/assets/images/workload/wl-005.png){: width="800" }


---

## 파드 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 파드 리소스 정보를 입력하여 생성할 수 있습니다.

![wl-008.png](/assets/images/workload/wl-008.png){: width="800" }

---
## 파드 수정
수정하려는 파드를 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.

---
## 파드 삭제
삭제하려는 파드를 선택하고 우측의 삭제 버튼을 선택합니다.
모달에서 네임스페이스와 파드 이름을 입력하여 삭제합니다.

![pod-delete.png](/assets/images/workload/pod-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 파드가 있습니까?**

<input />

**2. 아래 속성으로 새 파드를 만드세요. 생성한 파드의 상태와 로그를 확인하세요.**

```
- image: nginx
```

**3. 파드가 어떤 노드에 위치했는지 확인하세요.**

<input />

**4. 생성한 파드를 삭제하세요.**
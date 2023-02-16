---
layout: default
title: 6.4 스테이트풀셋
nav_order: 4
parent: 6. 워크로드
---

# 스테이트풀셋
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

## 스테이트풀셋(Statefulset)
스테이트풀셋은 애플리케이션의 스테이트풀을 관리하는데 사용하는 워크로드 오브젝트입니다.
파드 집합의 디플로이먼트와 스케일링을 관리하며, 파드들의 순서 및 고유성을 보장합니다.

**스테이트풀셋의 일부 대표적인 용도**

- 안정 & 고유한 네트워크 식별자.
- 안정 & 지속성을 갖는 스토리지.
- 순차적인 정상 배포(graceful deployment)와 스케일링.
- 순차적인 자동 롤링 업데이트.


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: web
spec:
  selector:
    matchLabels:
      app: nginx # .spec.template.metadata.labels 와 일치해야 한다
  serviceName: "nginx"
  replicas: 3 # 기본값은 1
  minReadySeconds: 10 # 기본값은 0
  template:
    metadata:
      labels:
        app: nginx # .spec.selector.matchLabels 와 일치해야 한다
    spec:
      terminationGracePeriodSeconds: 10
      containers:
      - name: nginx
        image: k8s.gcr.io/nginx-slim:0.8
        ports:
        - containerPort: 80
          name: web
        volumeMounts:
        - name: www
          mountPath: /usr/share/nginx/html
  volumeClaimTemplates:
  - metadata:
      name: www
    spec:
      accessModes: [ "ReadWriteOnce" ]
      storageClassName: "my-storage-class"
      resources:
        requests:
          storage: 1Gi

    
{% endhighlight %}
   
</details>

---

## 메뉴이동
`워크로드` ➡ `스테이트풀셋`

![wl-sts.png](/assets/images/workload/wl-sts.png)

---

## 화면구성
배포된 스테이트풀셋 정보를 제공합니다.

![wl-015.png](/assets/images/workload/wl-015.png){: width="800" }

---

## 스테이트풀셋 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 스테이트풀셋 리소스 정보를 입력하여 생성할 수 있습니다.
![statefulset-create.png](/assets/images/workload/statefulset-create.png){: width="800" }

---

## 스테이트풀셋 수정
수정하려는 스테이트풀셋을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.
스테이트풀셋도 디플로이먼트와 동일하게 오토스케일 설정이 가능합니다.

---

## 스테이트풀셋 삭제

삭제하려는 스테이트풀셋을 선택하고 우측의 삭제 버튼을 선택합니다.

![statefulset-delete.png](/assets/images/workload/statefulset-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 스테이트풀셋이 있습니까?**

<input />

**2. 아래 속성으로 새 스테이트풀셋을 만드세요.**

```
- name: mysql; 
- replicas: 1; 
- image: mysql:5.7.37
```

**3. 생성한 스테이트풀셋을 삭제하세요.**
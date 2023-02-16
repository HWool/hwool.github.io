---
layout: default
title: 6.5 데몬셋
nav_order: 5
parent: 6. 워크로드
---

# 데몬셋
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

## 데몬셋(Daemonset)

데몬셋은 모든(또는 일부) 노드가 파드의 사본을 실행하도록 합니다. 노드가 클러스터에 추가되면 파드도 추가합니다.
노드가 클러스터에서 제거되면 해당 파드는 가비지(garbage)로 수집됩니다. 데몬셋을 삭제하면 데몬셋이 생성한 파드들이 정리됩니다.

**데몬셋의 일부 대표적인 용도**

- 모든 노드에서 클러스터 스토리지 데몬 실행
- 모든 노드에서 로그 수집 데몬 실행
- 모든 노드에서 노드 모니터링 데몬 실행

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: fluentd-elasticsearch
  namespace: kube-system
  labels:
    k8s-app: fluentd-logging
spec:
  selector:
    matchLabels:
      name: fluentd-elasticsearch
  template:
    metadata:
      labels:
        name: fluentd-elasticsearch
    spec:
      tolerations:
      # this toleration is to have the daemonset runnable on master nodes
      # remove it if your masters can't run pods
      - key: node-role.kubernetes.io/master
        operator: Exists
        effect: NoSchedule
      containers:
      - name: fluentd-elasticsearch
        image: quay.io/fluentd_elasticsearch/fluentd:v2.5.2
        resources:
          limits:
            memory: 200Mi
          requests:
            cpu: 100m
            memory: 200Mi
        volumeMounts:
        - name: varlog
          mountPath: /var/log
        - name: varlibdockercontainers
          mountPath: /var/lib/docker/containers
          readOnly: true
      terminationGracePeriodSeconds: 30
      volumes:
      - name: varlog
        hostPath:
          path: /var/log
      - name: varlibdockercontainers
        hostPath:
          path: /var/lib/docker/containers

    
{% endhighlight %}
   
</details>

---

## 메뉴이동
`워크로드` ➡ `데몬셋`

![wl-ds.png](/assets/images/workload/wl-ds.png)

---

## 화면구성
배포된 데몬셋 정보를 제공합니다.

![wl-016.png](/assets/images/workload/wl-016.png){: width="800" }


## 데몬셋 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 데몬셋 리소스 정보를 입력하여 생성할 수 있습니다.

![daemonset-create.png](/assets/images/workload/daemonset-create.png){: width="800" }

---


## 데몬셋 수정
수정하려는 데몬셋을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.

---


## 데몬셋 삭제
삭제하려는 데몬셋을 선택하고 우측의 삭제 버튼을 선택한다.모달에서 네임스페이스와 데몬셋 이름을 입력하여 삭제합니다.

![daemonset-delete.png](/assets/images/workload/daemonset-delete.png){: width="800" }


---
## 연습문제

**1. 클러스터에 몇 개의 데몬셋이 있습니까?**

<input />

**2. 아래 속성으로 새 데몬셋을 만드세요.**

```
- Name: elasticsearch
- Namespace: demo
- Image: k8s.gcr.io/fluentd-elasticsearch:1.20
```

**3. 새롭게 생성한 데몬셋의 포드가 어떤 노드에 위치해있습니까?**

<input />


**4. 생성한 데몬셋을 삭제하세요.**


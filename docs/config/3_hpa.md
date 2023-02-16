---
layout: default
title: 7.3. HPA
nav_order: 3
parent: 7. 구성
---

# HPA
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

## HPA(HorizontalPodAutoscaler)
Kuberenetes에서, HorizontalPodAutoscaler 는 워크로드 리소스(예: 디플로이먼트 또는 스테이트풀셋)를 자동으로 업데이트하며, 워크로드의 크기를 수요에 맞게 자동으로 스케일링하는 것을 목표로 합니다.

수평 스케일링은 부하 증가에 대해 파드를 더 배치하는 것을 뜻합니다. 이는 수직 스케일링(Kuberenetes에서는, 해당 워크로드를 위해 이미 실행 중인 파드에 더 많은 자원(예: 메모리 또는 CPU)를 할당하는 것)과는 다릅니다.

부하량이 줄어들고, 파드의 수가 최소 설정값 이상인 경우, HorizontalPodAutoscaler는 워크로드 리소스(디플로이먼트, 스테이트풀셋, 또는 다른 비슷한 리소스)에게 스케일 다운을 지시합니다.

Horizontal Pod Autoscaling은 크기 조절이 불가능한 오브젝트(예: 데몬셋)에는 적용할 수 없습니다.

![](https://d33wubrfki0l68.cloudfront.net/4fe1ef7265a93f5f564bd3fbb0269ebd10b73b4e/1775d/images/docs/horizontal-pod-autoscaler.svg){: width="600" }

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: php-apache
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: php-apache
  minReplicas: 1
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
{% endhighlight %}
   
</details>

---

## 메뉴이동
`구성` ➡ `HPA`

![config-003.png](/assets/images/config/config-003.png)

---

## 화면구성
배포된 HPA 정보를 제공합니다.

![config-007.png](/assets/images/config/config-007.png){: width="800" }

---

## HPA 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 HPA 리소스 정보를 입력하여 생성할 수 있습니다.

![config-008.png](/assets/images/config/config-008.png){: width="800" }

---

## HPA 수정
수정하려는 HPA을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.

---

## HPA 삭제

삭제하려는 HPA을 선택하고 우측의 삭제 버튼을 선택합니다.

![hpa-delete.png](/assets/images/config/hpa-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 HPA가 있습니까?**

<input />

**2. 아래 속성으로 HPA와 디플로이먼트를 생성하세요.**

```
- HPA Name: php-apache
- Resource Utilization: CPU
- averageUtilization: 50
---
- Deployment name: php-apache
- Image name: k8s.gcr.io/hpa-example
- resources: limits(cpu: 500m), requests(cpu: 200m)
```


**4. 생성한 HPA와 디플로이먼트를 삭제하세요.**
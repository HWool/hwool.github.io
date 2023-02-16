---
layout: default
title: 10.6 파드시큐리티폴리시
nav_order: 6
parent: 10. 접근제어
---

# 파드시큐리티폴리시
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Cluster
{: .label .label-blue }
</div>

## 파드시큐리티폴리시(Pod Security Policies)
파드시큐리티폴리시는 포드 사양의 보안에 민감한 측면을 제어하는 ​​클러스터 수준 리소스입니다. PodSecurityPolicy 개체 는 관련 필드에 대한 기본값뿐만 아니라 시스템에 수락되기 위해 포드가 실행되어야 하는 조건 집합을 정의합니다. 

**PodSecurityPolicy는 Kubernetes v1.21부터 더 이상 사용되지 않으며 v1.25 에서 제거됩니다 .**
**Pod Security Admission 또는 타사 승인 플러그인으로 마이그레이션하는 것이 좋습니다.**

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: policy/v1beta1
kind: PodSecurityPolicy
metadata:
  name: example
spec:
  privileged: false  # Don't allow privileged pods!
  # The rest fills in some required fields.
  seLinux:
    rule: RunAsAny
  supplementalGroups:
    rule: RunAsAny
  runAsUser:
    rule: RunAsAny
  fsGroup:
    rule: RunAsAny
  volumes:
  - '*'
{% endhighlight %}
   
</details>
---

## 메뉴이동
`접근제어` ➡ `파드시큐리티폴리시`

![ac-006.png](/assets/images/ac/ac-006.png)

---
## 화면구성
생성된 클러스터롤바인딩 정보를 제공합니다.

![ac-017.png](/assets/images/ac/ac-017.png){: width="800" }

---

## 파드시큐리티폴리시 생성
`+생성`을 클릭 후 내용을 입력하여 파드시큐리티폴리시를 생성할 수 있다. 파드시큐리티폴리시는 YAML로 입력할 수 있다.

![ac-018.png](/assets/images/ac/ac-018.png){: width="800" }

---

## 파드시큐리티폴리시 수정
파드시큐리티폴리시 목록에서 특정 파드시큐리티폴리시를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있다.

---

## 파드시큐리티폴리시 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 파드시큐리티폴리시 명 입력 후 `Delete` 버튼 클릭 시 파드시큐리티폴리시가 삭제된다.

![podsecuritypolicy-delete.png](/assets/images/ac/podsecuritypolicy-delete.png){: width="800" }
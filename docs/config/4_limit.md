---
layout: default
title: 7.4. 리밋레인지
nav_order: 4
parent: 7. 구성
---

# 리밋레인지
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

## 리밋 레인지(Limit Range)

기본적으로 컨테이너는 쿠버네티스 클러스터에서 무제한 컴퓨팅 리소스로 실행됩니다.
리소스 쿼터을 사용하면 클러스터 관리자는 네임스페이스별로 리소스 사용과 생성을 제한할 수 있습니다. 네임스페이스 내에서 파드나 컨테이너는 네임스페이스의 리소스 쿼터에 정의된 만큼의 CPU와 메모리를 사용할 수 있습니다. 
하나의 파드 또는 컨테이너가 사용 가능한 모든 리소스를 독점할 수 있다는 우려를 리밋레인지는 네임스페이스에서 리소스 할당(파드 또는 컨테이너)을 제한하는 정책입니다.

**리밋레인지 제약 조건**

- 네임스페이스에서 파드 또는 컨테이너별 최소 및 최대 컴퓨팅 리소스 사용량을 지정
- 네임스페이스에서 스토리지클래스별 최소 및 최대 스토리지 요청을 지정
- 네임스페이스에서 리소스에 대한 요청과 제한 사이의 비율을 지정
- 네임스페이스에서 컴퓨팅 리소스에 대한 기본 요청/제한을 설정하고 런타임에 있는 컨테이너에 자동으로 설정

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: v1
kind: LimitRange
metadata:
  name: mem-limit-range
spec:
  limits:
  - default:
      memory: 512Mi
    defaultRequest:
      memory: 256Mi
    type: Container

{% endhighlight %}
   
</details>

---

## 메뉴이동
`구성` ➡ `리밋레인지`

![config-004.png](/assets/images/config/config-004.png)

---
## 화면구성
생성된 리밋레인지 정보를 제공합니다.

![config-009.png](/assets/images/config/config-009.png){: width="800" }

---

## 리밋레인지 생성
`+생성`을 클릭 후 내용을 입력하여 리밋레인지을 생성할 수 있습니다.

![limit-create.png](/assets/images/config/limit-create.png){: width="800" }

---

## 리밋레인지 수정
리밋레인지 목록에서 특정 리밋레인지을 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

![config-010.png](/assets/images/config/config-010.png){: width="800" }

---

## 리밋레인지 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/리밋레인지 명 입력 후 `Delete` 버튼 클릭 시 리밋레인지이 삭제됩니다.

![limit-delete.png](/assets/images/config/limit-delete.png){: width="800" }


---
## 연습문제

**1. 클러스터에 몇 개의 리밋레인지이 있습니까?**

<input />

**2. 아래 속성으로 리밋레인지과 파드를 생성하세요.**

```
- LimitRange Name:  mem-limit-range
- default memory : 512Mi
- defaultRequest memory: 256Mi
---
- Pod name: nginx
- Image name: nginx
```


**4. 생성한 리밋레인지과 파드를 삭제하세요.**
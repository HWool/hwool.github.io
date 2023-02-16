---
layout: default
title: 10.5 서비스어카운트
nav_order: 5
parent: 10. 접근제어
---

# 서비스어카운트
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

## 서비스어카운트
서비스어카운트는 쿠버네티스 API 접근 시 파드의 권한을 식별하기 위한 리소스입니다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: v1
kind: ServiceAccount
metadata:
  # ...
secrets:
- name: jenkins-token-1yvwg

{% endhighlight %}
   
</details>


---
## 메뉴이동
`접근제어` ➡ `서비스어카운트`

![ac-005.png](/assets/images/ac/ac-005.png)

---
## 화면구성
생성된 서비스어카운트 정보를 제공합니다.
![ac-015.png](/assets/images/ac/ac-015.png){: width="800" }

---

## 서비스어카운트 생성
`+생성`을 클릭 후 내용을 입력하여 서비스어카운트를 생성할 수 있다. 서비스어카운트는 YAML로 입력할 수 있다.

![ac-016.png](/assets/images/ac/ac-016.png){: width="800" }

---
## 서비스어카운트 수정
서비스어카운트 목록에서 특정 서비스어카운트를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있다.

---

## 서비스어카운트 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/서비스어카운트 명 입력 후 `Delete` 버튼 클릭 시 서비스어카운트가 삭제된다.

![serviceaccount-delete.png](/assets/images/ac/serviceaccount-delete.png){: width="800" }
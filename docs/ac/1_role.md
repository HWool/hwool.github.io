---
layout: default
title: 10.1 롤
nav_order: 1
parent: 10. 접근제어
---

# 롤
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

## 롤(Role)
RBAC Role 은 권한 집합을 나타내는 규칙이 포함되어 있습니다. 권한은 순전히 부가적입니다.
롤은 항상 특정 내에서 권한을 설정합니다. 네임스페이스 롤을 생성할 때 롤이 속한 네임스페이스를 지정해야 합니다.


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  namespace: default
  name: pod-reader
rules:
- apiGroups: [""] # "" indicates the core API group
  resources: ["pods"]
  verbs: ["get", "watch", "list"]

{% endhighlight %}
   
</details>

---

## 메뉴이동
`접근제어` ➡ `롤`

![ac-001.png](/assets/images/ac/ac-001.png)

---

## 화면구성
생성된 롤 정보를 제공합니다.

![ac-007.png](/assets/images/ac/ac-007.png){: width="800" }

---

## 롤 생성
`+생성`을 클릭 후 내용을 입력하여 롤을 생성할 수 있습니다.

![ac-008.png](/assets/images/ac/ac-008.png){: width="800" }

---

## 롤 수정
롤 목록에서 특정 롤을 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 롤 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/롤 이름을 입력 후 `Delete` 버튼 클릭 시 롤이 삭제됩니다.

![role-delete.png](/assets/images/ac/role-delete.png){: width="800" }
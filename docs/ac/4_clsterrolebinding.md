---
layout: default
title: 10.4 클러스터롤바인딩
nav_order: 4
parent: 10. 접근제어
---

# 클러스터롤바인딩
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

## 클러스터롤바인딩(ClusterRoleBinding)

클러스터롤바인딩은 롤에 정의된 권한을 사용자 또는 사용자 집합에 부여합니다. 여기에는 `subject` (`user`,`group` 또는 `serviceaccount`) 목록과 부여되는 롤에 대한 참조가 포함됩니다. ClusterRoleBinding은 클러스터 전체에 액세스 권한을 부여합니다.

ClusterRole을 클러스터의 모든 네임스페이스에 바인딩하려면 ClusterRoleBinding을 사용합니다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: rbac.authorization.k8s.io/v1
# This cluster role binding allows anyone in the "manager" group to read secrets in any namespace.
kind: ClusterRoleBinding
metadata:
  name: read-secrets-global
subjects:
- kind: Group
  name: manager # Name is case sensitive
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: ClusterRole
  name: secret-reader
  apiGroup: rbac.authorization.k8s.io

{% endhighlight %}
   
</details>

---

## 메뉴이동
`접근제어` ➡ `클러스터롤바인딩`

![ac-004.png](/assets/images/ac/ac-004.png)

---
## 화면구성
생성된 클러스터롤바인딩 정보를 제공합니다.

![ac-013.png](/assets/images/ac/ac-013.png){: width="800" }

---

## 클러스터롤바인딩 생성
`+생성`을 클릭 후 내용을 입력하여 클러스터롤바인딩을 생성할 수 있습니다.

![ac-014.png](/assets/images/ac/ac-014.png){: width="800" }

---
## 클러스터롤바인딩 수정
클러스터롤바인딩 목록에서 특정 클러스터롤바인딩을 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 클러스터롤바인딩 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 클러스터롤바인딩 이름을 입력 후 `Delete` 버튼 클릭 시 클러스터롤바인딩이 삭제됩니다.

![clusterrolebinding-delete.png](/assets/images/ac/clusterrolebinding-delete.png){: width="800" }
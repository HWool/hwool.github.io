---
layout: default
title: 10.3 클러스터롤
nav_order: 3
parent: 10. 접근제어
---

# 클러스터롤
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

## 클러스터롤(Clusterrole)
ClusterRole 에는 권한 집합을 나타내는 규칙이 포함되어 있습니다. 권한은 순전히 부가적입니다.
ClusterRole은 네임스페이스가 없는 리소스입니다. Kubernetes 객체는 항상 네임스페이스가 지정되거나 네임스페이스가 지정되지 않아야 하기 때문에 리소스의 이름(Role 및 ClusterRole)이 다릅니다.

**ClusterRoles 용도**

- 네임스페이스 리소스에 대한 권한을 정의하고 개별 네임스페이스 내에서 부여
- 네임스페이스 리소스에 대한 권한을 정의하고 모든 네임스페이스에 대해 부여
- 클러스터 범위 리소스에 대한 권한 정의
- 네임스페이스 내에서 역할을 정의하려면 역할을 사용하십시오. 클러스터 전체에 역할을 정의

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  # "namespace" omitted since ClusterRoles are not namespaced
  name: secret-reader
rules:
- apiGroups: [""]
  #
  # at the HTTP level, the name of the resource for accessing Secret
  # objects is "secrets"
  resources: ["secrets"]
  verbs: ["get", "watch", "list"]

{% endhighlight %}
   
</details>

---
## 메뉴이동
`접근제어` ➡ `클러스터롤`

![ac-003.png](/assets/images/ac/ac-003.png)

---

## 화면구성
생성된 클러스터롤 정보를 제공합니다.
![ac-011.png](/assets/images/ac/ac-011.png){: width="800" }

---
## 클러스터롤 생성
`+생성`을 클릭 후 내용을 입력하여 클러스터롤을 생성할 수 있습니다.

![ac-012.png](/assets/images/ac/ac-012.png){: width="800" }

---

## 클러스터롤 수정
클러스터롤 목록에서 특정 클러스터롤을 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 클러스터롤 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 클러스터롤 이름을 입력 후 `Delete` 버튼 클릭 시 클러스터롤이 삭제됩니다.

![clusterrole-delete.png](/assets/images/ac/clusterrole-delete.png){: width="800" }
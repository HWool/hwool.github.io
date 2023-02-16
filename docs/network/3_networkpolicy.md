---
layout: default
title: 8.3 네트워크폴리시
nav_order: 3
parent: 8. 네트워크
---

# 네트워크폴리시
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

## 네트워크폴리시(Network Policies)

IP 주소 또는 포트 수준(OSI 계층 3 또는 4)에서 트래픽 흐름을 제어하려는 경우, 클러스터의 특정 애플리케이션에 대해 `Kubernetes NetworkPolicy` 사용을 고려 가능합니다.

네트워크폴리시는 파드가 네트워크 상의 다양한 네트워크 `entities`(여기서는 `entity`를 사용하여 Kubernetes에서 특별한 의미로 사용되는 `endpoints` 및 `services`와 같은 일반적인 용어가 중의적으로 표현되는 것을 방지함)와 통신할 수 있도록 허용하는 방법을 지정할 수 있는 애플리케이션 중심 구조입니다.

**파드가 통신할 수 있는 entities 조합**

- 허용되는 다른 파드(예외: 파드는 자신에 대한 접근을 차단할 수 없음)
- 허용되는 네임스페이스
- IP 블록(예외: 파드 또는 노드의 IP 주소와 관계없이 파드가 실행 중인 노드와의 트래픽은 항상 허용됨)
pod- 또는 namespace- 기반의 네트워크폴리시를 정의할 때, 셀렉터를 사용하여 셀렉터와 일치하는 파드와 주고받는 트래픽을 지정한다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: test-network-policy
  namespace: default
spec:
  podSelector:
    matchLabels:
      role: db
  policyTypes:
  - Ingress
  - Egress
  ingress:
  - from:
    - ipBlock:
        cidr: 172.17.0.0/16
        except:
        - 172.17.1.0/24
    - namespaceSelector:
        matchLabels:
          project: myproject
    - podSelector:
        matchLabels:
          role: frontend
    ports:
    - protocol: TCP
      port: 6379
  egress:
  - to:
    - ipBlock:
        cidr: 10.0.0.0/24
    ports:
    - protocol: TCP
      port: 5978
{% endhighlight %}
   
</details>




---

## 메뉴이동
`네트워크` ➡ `네트워크폴리시`

![network-003.png](/assets/images/network/network-003.png)

---

## 화면구성
생성된 네트워크폴리시 정보를 제공합니다.

![network-008.png](/assets/images/network/network-008.png){: width="800" }

---

## 네트워크폴리시 생성
`+생성`을 클릭 후 내용을 입력하여 네트워크폴리시를 생성할 수 있습니다. 네트워크폴리시는 YAML로 입력할 수 있습니다.

![network-009.png](/assets/images/network/network-009.png){: width="800" }

---

## 네트워크폴리시 수정
네트워크폴리시 목록에서 특정 네트워크폴리시를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 네트워크폴리시 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/네트워크폴리시 명 입력 후 `Delete` 버튼 클릭 시 네트워크폴리시가 삭제됩니다.

![networkpolicy-delete.png](/assets/images/network/networkpolicy-delete.png){: width="800" }

---
## 연습문제

**1. 예제 yaml을 사용하여 네트워크폴리시를 생성하세요.**

**2. 생성한 네트워크폴리시를 확인하고 삭제하세요.**
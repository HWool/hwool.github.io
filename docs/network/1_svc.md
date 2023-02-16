---
layout: default
title: 8.1 서비스
nav_order: 1
parent: 8. 네트워크
---

# 서비스
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

## 서비스(Service)
파드 집합에서 실행중인 애플리케이션을 네트워크 서비스로 노출하는 추상화 방법입니다.

Kubernetes를 사용하면 익숙하지 않은 서비스 디스커버리 메커니즘을 사용하기 위해 애플리케이션을 수정할 필요가 없습니다. Kubernetes를는 파드에게 고유한 IP 주소와 파드 집합에 대한 단일 DNS 명을 부여하고, 그것들 간에 로드밸런스를 수행할 수 있습니다.

<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: MyApp
  ports:
    - protocol: TCP
      port: 80
      targetPort: 9376

{% endhighlight %}
   
</details>

---

## 메뉴이동
`네트워크` ➡ `서비스`

![network-001.png](/assets/images/network/network-001.png)

---

## 화면구성
생성된 서비스 정보를 제공합니다.

![network-004.png](/assets/images/network/network-004.png){: width="800" }

---

## 서비스 생성
`+생성`을 클릭 후 내용을 입력하여 서비스를 생성할 수 있습니다. 서비스는 FORM/YAML로 입력할 수 있습니다.

![network-005.png](/assets/images/network/network-005.png){: width="800" }

**서비스 필수 요구값**

- Name
- Namespace
- Selector(key,value)
- ServiceType
  + ClusterIP
  + NodePort
  + LoadBalancer
- ClusterIP
  + PortName
  + Port
  + Protocotol(TCP,UDP)
  + Target Port

---

## 서비스 수정
서비스 목록에서 특정 서비스를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있다.

---

## 서비스 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/서비스 명 입력 후 `Delete` 버튼 클릭 시 서비스가 삭제된다.

![service-delete.png](/assets/images/network/service-delete.png){: width="800" }

---
## 연습문제

**1. 예제 yaml을 사용하여 서비스를 생성하세요.**

**2. 생성한 서비스를 확인하고 삭제하세요.**
---
layout: default
title: 8.2 인그레스
nav_order: 2
parent: 8. 네트워크
---

# 인그레스
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

## 인그레스(Ingress)
인그레스는 클러스터 외부에서 클러스터 내부 서비스로 HTTP와 HTTPS 경로를 노출합니다. 트래픽 라우팅은 인그레스 리소스에 정의된 규칙에 의해 컨트롤됩니다.

**인그레스가 모든 트래픽을 하나의 서비스로 보내는 간단한 예시**

![ingress.png](/assets/images/network/ingress.png){: width="800" }

<details>
<summary>예제 Yaml</summary>

{% highlight yaml %}
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: minimal-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
spec:
  ingressClassName: nginx-example
  rules:
  - http:
      paths:
      - path: /testpath
        pathType: Prefix
        backend:
          service:
            name: test
            port:
              number: 80
              
{% endhighlight %}
   
</details>


---

## 메뉴이동
`네트워크` ➡ `인그레스`

![network-002.png](/assets/images/network/network-002.png)

---

## 화면구성
생성된 인그레스 정보를 제공합니다.

![network-006.png](/assets/images/network/network-006.png){: width="800" }

---

## 인그레스 생성
`+생성`을 클릭 후 내용을 입력하여 인그레스를 생성할 수 있다. 인그레스는 YAML로 입력할 수 있습니다.


![network-007.png](/assets/images/network/network-007.png){: width="800" }

---
## 인그레스 수정
인그레스 목록에서 특정 인그레스를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.


---

## 인그레스 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/인그레스 명 입력 후 `Delete` 버튼 클릭 시 인그레스가 삭제됩니다.

![ingress-delete.png](/assets/images/network/ingress-delete.png){: width="800" }

---
## 연습문제

**1. 예제 yaml을 사용하여 인그레스를 생성하세요.**

**2. 생성한 인그레스를 확인하고 삭제하세요.**
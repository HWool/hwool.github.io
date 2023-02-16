---
layout: default
title: 12.1 알림 정책
nav_order: 1
parent: 12. 설정
---

# 알림 정책
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Cluster
{: .label .label-blue }

Namespace
{: .label .label-green }
</div>

## 알림 정책

알림 정책은 시스템 성능에 대한 알림의 기준을 설정합니다. 사용자가 정한 알림의 기준을 벗어나는 상황이 발생하게 되는경우 사용자가 빠르게 대처할 수 있도록 알림을 발송합니다. 클러스터 알림 정책에서는 노드와 관련된 알림을 설정할 수 있고 네임스페이스 알림 정책에서는 워크로드와 관련된 알림을 설정할 수 있습니다.

> 💡 참고 : 알림 정책의 기준은 사용자가 임의로 정의하여 설정할 수 있습니다.

![alertpolicy-list.png](/assets/images/setting/alertpolicy-list.png)

---


## 알림 정책 생성

`+생성` 을 선택하면 알림을 설정할 수 있는 폼이 나타납니다. 폼에서 설정 정보를 입력하고 `완료` 를 선택하면 알림 정책이 생성됩니다. 하나의 알림 정책은 다수의 알림 규칙들을 가질 수 있으며 알림 규칙 각각의 알림 시간 또는 알림 시간 제한이나 활성화 여부 등을 설정 할 수 있습니다.
![alertpolicy-create.png](/assets/images/setting/alertpolicy-create.png)

설정 정보에 대한 설명은 다음과 같습니다.

**알림 정책(표)**

![alertpolicy-table1.png](/assets/images/setting/alertpolicy-table1.png)

**알림 규칙**

- 알림 규칙명 : 알림 규칙 이름
- 알림 규칙 설명 : 알림 규칙에 대한 설명
- 타입 : 클러스터 알림 규칙은 `Node, Node Selector, Expression` 3가지 타입의 알림 규칙을 설정 할 수 있습니다.

![node-alert-rule.png](/assets/images/setting/node-alert-rule.png)

**Node**

- Node 선택 : 클러스터의 Node 목록 중 알림 규칙을 설정할 Node를 선택합니다.
- Is : Node의 알림을 트리거할 이벤트를 선택합니다.(`CPU/Memory/Disk`)
- Over : 알림 규칙의 임계치이다. 임계치를 넘어 갈 경우 알람이 발송됩니다.
![node-selector-alert-rule.png](/assets/images/setting/node-selector-alert-rule.png)

**Node Selector**

Node Label Selector 기준이며 Label Selector할 Label들을 입력합니다. [Selector 추가] 버튼 클릭 시 Key - Value를 입력하며 Label Selector는 여러개 등록 할 수 있습니다.
    
- Key: Label Selector 할 Label 명
- Value: Label Selector할 Label 값
- Is : Node의 알림을 트리거할 이벤트를 선택합니다.(`CPU/Memory/Disk`)
- Over : 알림 규칙의 임계치이다. 임계치를 넘어 갈 경우 알람이 발송됩니다.
![node-expression-alert-rule.png](/assets/images/setting/node-expression-alert-rule.png)

**Expression**

`Node/Node Selector` 알림 중 지원하지 않는 알람을 사용자가 직접 Promethues Query를 입력하여 알람을 설정 할 수 있습니다.

- Expression : 알람을 트리거할 Prometheus Query를 입력합니다.
- Is : Expression 값과 임계치와의 비교 연산자를 의미합니다.
- Value : 알림 규칙의 임계치이다. 임계치를 넘어 갈 경우 알람이 발송됩니다.


**알림 수준**

알림 경보 수준

**알림 정책 고급 옵션**

알림 정책 고급 옵션의 활성화 여부를 선택합니다. Enabled 선택 시 알림 정책 고급 옵션을 따르며 Disabled 선택 시 알림 규칙 고급 옵션을 설정합니다.

---
## 알림 정책 수정

수정하려는 알림 정책을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 `수정` 버튼을 선택하여 반영합니다.

---

## 알림 정책 삭제

삭제하려는 알림 정책을 선택하고 우측의 `삭제` 버튼을 선택합니다.

![alertpolicy-delete.png](/assets/images/setting/alertpolicy-delete.png)

모달에서 알림 정책 이름을 입력하여 삭제합니다.

---
layout: default
title: 5.3.2 승인
nav_order: 3
grand_parent: 5. 애플리케이션
parent: 5.3 빌드
---

# 승인
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


---

## 승인

승인 태스크는 로그 정보가 제공되는 것이 아니라 승인 목록이 나타나고 사용자가 승인자 목록에 포함되어 있으면 승인 또는 거절이 가능합니다.
승인의 경우 모든 승인자가 승인해야 다음 태스크로 넘어가며 한명의 승인자라도 거절하면 파이프라인은 중지됩니다.

![build-approval.png](/assets/images/application/pipeline/build-approval.png){: width="800" }

---

**승인 성공**

![build-approval-allow.png](/assets/images/application/pipeline/build-approval-allow.png){: width="800" }


**승인 실패**

![build-approval-deny.png](/assets/images/application/pipeline/build-approval-deny.png){: width="800" }


---


## 태스크 연관관계

태스크에 대한 스펙을 작성할때에는 이름과 다른 태스크와의 연관관계를 설정하고 상세정보는 태스크 템플릿을 기반으로 작성합니다.
태스크의 이름은 쿠버네티스 이름 정책에 맞춰 작성하고 태스크의 연관관계는 해당 태스크을 수행하는 조건에 대한 정보를 입력합니다.
이는 `{이름}.{상태}` 의 형식으로 입력할 수 있다. 상태에 입력할 수 있는 값은 다음과 같습니다.


![build-create-task.png](/assets/images/application/pipeline/build-create-task.png){: width="800" }


| 상태        |  설명  |
|:------------|:-------|
| Succeeded | 성공 |
| Failed |  실패 |
| Skipped | 생략 | 
| Error | 에러발생 |


**예시**
연관관계 작성의 예

- parent 태스크 후 child 와 child-2 태스크를 수행한다.
- child 태스크가 성공하고 child-2 태스크가 실패하면 child-3 태스크를 수행한다.


![build-depends.png](/assets/images/application/pipeline/build-depends.png){: width="800" }


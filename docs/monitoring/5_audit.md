---
layout: default
title: 11.5 감사 로그
nav_order: 1
parent: 11. 모니터링&알림
---

# 감사 로그
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

---

## 감사로그

클러스터의 감사로그를 제공합니다. 범위설정에서 설정한 간격으로 통계를 나타내며 개수와 총 개수를 나타내며 Node, Namespace, Pod, Container 의 이름과 로그를 제공합니다.

---
## 메뉴이동
`모니터링` ➡ `감사 로그`

![audit.png](/assets/images/monitoring/audit.png)

---
## 화면 구성

![audit_log.png](/assets/images/monitoring/audit_log.png){: width="800" }


| 항목  | 설명 |
|---|---|
| Time   | 날짜 (yyyy-mm-dd HH:mm:ss) |
| Namespace   | Namespace의 이름 |
| Verb   | get, list, create, update, patch, watch, delete 와 같은 리소스 요청에 사용하는 API 동사 |
| Status   | 작업상태를 의미하고 Success, Failure 둘중 한가지만 올수 있습니다. |
| Code   | HTTP 상태코드 |
| Pod Ip  | 요청이 시작된 소스 IP 및 중간 프록시 |
| User Name   | impersonatedUser의 이름 |
| Message   | 감사로그의 상세 설명 |

로그 클릭 시 우측에 자세한 로그내용이 나옵니다.

![audit_log_detail.png](/assets/images/monitoring/audit_log_detail.png){: width="800" }


---

## 검색 조건


![audit_log_condition.png](/assets/images/monitoring/audit_log_detail.png){: width="800" }

- namespace : namespace 이름
- resourceType : resource 타입
- resourceName : resource 이름
- userName : impersonatedUser의 이름
- verb : get, list, create, update, patch, watch, delete 와 같은 리소스 요청에 사용하는 API 동사
- statusCode : HTTP 상태코드

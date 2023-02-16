---
layout: default
title: 11.2 애플리케이션
nav_order: 1
parent: 11. 모니터링&알림
---

# 애플리케이션
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

## 애플리케이션(APM)

애플리케이션이란, 실시간으로 모니터링 지표를 제공하여 운영 중인 어플리케이션의 문제점을 빠르게 파악할 수 있도록 합니다.

---
## 메뉴이동
`모니터링` ➡ `애플리케이션`

![app.png](/assets/images/monitoring/app.png)

---

## Overview
- 서비스 : Active Service Total EQ, Active Service EQ, TPS, 금일 TPS, 방문자수, 응답시간, XLog
- 시스템 : CPU, Memory

![2_app_overview.png](/assets/images/monitoring/2_app_overview.png){: width="800" }


**Active Service**

대시보드의 Active Service 차트에서는 개별 인스턴스 별로 현재 처리중인 Request를 Bar 형태로 표시합니다. 처리중인 Request는 단계별로 만족 (Info), 허용 (Warning), 불만 (Fatal) 을 초록색, 노란색(3초), 주황색(8초)으로 표시합니다.

- 좌측의 Total Active Services는 현재 처리중인 전체 인스턴스의 상태를 표시합니다.
- 우측의 Active Services는 현재 처리중인 개별 인스턴스 상태를 표시합니다.
처리중인 Request들이 표시될 때, BAR를 클릭하면 현재 진행중인 Request에 대한 정보를 얻기 위해 Thread 분석 페이지로 이동합니다.

![2_active_service.png](/assets/images/monitoring/2_active_service.png){: width="800" }

**Active Service Info**

Active Services에서 Bar 클릭하면 아래와 같은 뷰가 나옵니다. 상단에 Thread에 대한 메타데이터가 나오고 하단에 현재 진행중인 스택을 볼 수 있습니다. Thread가 지연되고 있다면 하단에 나온 스택에서 지연되고 있을 확률이 높기 때문에 해당 스택의 작업을 분석해 볼 필요가 있습니다.


![2_active_service_detail.png](/assets/images/monitoring/2_active_service_detail.png){: width="800" }

**TPS, Today TPS**

- TPS : 초당 처리량을 표현한 차트
- Today TPS : 당일 초당 처리량을 표현한 차트

![2_tps_todaytps.png](/assets/images/monitoring/2_tps_todaytps.png){: width="800" }

**Visitors, Response Time**

- 5분간 방문한 유니크한 방문자 수를 표현한 차트
- 애플리케이션 응답 시간 분포 그래프

![2_visitors_responsetime.png](/assets/images/monitoring/2_visitors_responsetime.png){: width="800" }

**CPU, Memory**

- CPU 사용량을 표현한 차트
- Memory 사용량을 표현한 차트

![2_cpu_memory.png](/assets/images/monitoring/2_cpu_memory.png){: width="800" }

**XLog**

시간의 흐름에 따른 응답시간의 분포를 scatter 차트형태로 표현하고, 해당 시간/응답시간 격자에 처리된 요청을 표시하는 Heatmap으로 표현한 것입니다.

HTTP Status 코드로 500 오류가 발생하면 주황색으로 표시합니다.

XLog 차트에 마우스로 드래그하여 사각형을 그리면, 해당 영역에서 처리된 Request들에 대한 상세 트랜잭션을 Profile View에서 메소드 단위로 분석할 수 있습니다.

![2_xlog_scatter.png](/assets/images/monitoring/2_xlog_scatter.png){: width="800" }

**XLog Info**

상단에는 선택한 영역에서 실행된 Request들이 출력되며, 상단에서 Row를 클릭하면 하단에 트랜잭션에 대한 상세 정보를 출력합니다. 시작시간, 수행시간, Database와 관련된 실행시간의 합, CPU 소요 시간 등의 정보를 확인할 수 있습니다.

| 항목  | 설명  |
|---|---|
| App Name  | app 의 이름  |
| Pod Name  |  pod 의 이름 |
| Elapsed Time | 서비스 소요시간  |
| IP  | Request Address  |
| Service  | 서비스 URL  |
| StartTime  | 서비스 시작시간 |
| EndTime  | 서비스 종료시간  |
| Txid  | 트랜잭션 ID  |
| Cpu  | 서비스 CpuTime  |
| Memory  | 서비스에서 사용한 memory  |
| SQL Count  | 서비스에서 SQL 수행 횟수  |
| SQL Time   | 서비스에서 소용된 SQL 시간의 합  |
| API Count  | 서비스에서 API 수행 횟수  |
| API Time  | 서비스에서 소용된 API 시간의 합  |

![2_xlog_details_info_header.png](/assets/images/monitoring/2_xlog_details_info_header.png){: width="800" }

**XLog Profile**

Profile 에서는 해당 메소드의 실행소요된 시간을 계산하여 표시합니다. 메소드들을 실행 관계를 트리형태로 표현하고 있습니다. 이전 단계와의 시작 시간 차이를 T-GAP으로 표시합니다.

![2_xlog_details_profile.png](/assets/images/monitoring/2_xlog_details_profile.png){: width="800" }

**XLog 특정한 확률의 로그**

Response time이 일정 시간 이내인 transaction의 경우 특정한 확률로 로그가 남습니다.

| response time  | 확률 |
|---|---|
| 0~1초 사이  | 3%  |
| 1~2초 사이  | 5% |
| 2~3초 사이 | 20%  |
| 3초 이상  | 100%  |


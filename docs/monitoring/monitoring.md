---
layout: default
title: 11. 모니터링&알림
nav_order: 11
has_children: true
permalink: /docs/monitoring
---

# 11. 모니터링&알림

모니터링은 클러스터 별로 모니터링을 제공합니다. 모니터링은 이벤트 로그/감사 로그/컨테이너 로그/시스템 을 제공하여 운영자가 Accordion 내의 클러스터와 어플리케이션을 다양한 관점에서 모니터링하여 안정적인 시스템 운영할 수 있도록 합나다.

---

## 모니터링 범위 검색

모니터링 지표는 시간 별로 검색이 가능하며 아래의 두가지 방법과 같습니다.

- 최근 시점부터 시간 간격을 설정하여 모니터링 데이터를 확인할 수 있다. 기간은 현재 시점부터 `분단위(5,15,30)`로 `시간단위(1,3,6,12,24)`, `일단위(2,7)`로 지정할 수 있습니다.

![range_time.png](/assets/images/monitoring/range_time.png)

- 캘린더를 선택하여 원하는 검색 날짜/시간의 정보를 확인할 수 있습니다. start 캘린더에서 시작날짜를 선택하고 end 캘린더에서 종료날짜를 선택한 후 OK를 클릭하여 원하는 검색 기간을 적용합니다.

![range_calendar.png](/assets/images/monitoring/range_calendar.png)
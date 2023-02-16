---
layout: default
title: 12.4.2 네임스페이스
nav_order: 1
parent: 12.4 실습
grand_parent: 12. 설정
---

# 네임스페이스
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

## 실습2. 네임스페이스

---

## 1) 타입 : 워크로드(Workload)

![workload1.png](/assets/images/setting/workload1.png)

1. 알림을 받고자 하는 클러스터 노드 선택
2. 알림 받기 위해 워크로드를 관리하고 있는 네임스페이스 선택
3. 설정 메뉴 선택
4. 알림 정책 선택
5. 알림 정책 생성
6. 알림 정책명: demo-alert-mem-workload 작성
7. 알림 규칙 추가
8. 알림 규칙명: demo-alert-mem-workload 작성
9. 타입을 Workload로 지정 Deployment의 demo에 대한 memory 사용률이 50% 이상일 시 알림 수준을 Warning 수준으로 메일 or 슬랙으로 알림 발송, 알림 발송 시간에 대한 설정은 알림 정책 고급옵션 비활성화로 알림 규칙에 대해 각각에 알림 설정 가능
10. 발송 받을 슬랙 및 메일 추가,설정

![workload2.png](/assets/images/setting/workload2.png)


11. 처음 알림 오기까지 30초 대기(그룹 대기 시간) 후 3분 간격으로 반복 알림(그룹 반복 시간) 후 1시간 후에 다시 알림 발송(알림 반복 시간) 설정, 알림 발송 제한은 am 02 ~ am 08 시로 설정
12. 알림 규칙 활성화
13. 알림 규칙 설정 완료

---

## 2) 타입 : 노드 셀렉터(Node Selector)

타입 Workload Selector 설정 전 사용자가 원하는 label를 설정

> 참고 : 현재 아코디언에서는 container `key=value`에 대한 list를 볼 수 없어 사용자가 직접 node, workload에 대한 `key=value` 값을 찾아서 기입

![workload3.png](/assets/images/setting/workload3.png)

1. 알림을 받고자 하는 클러스터 노드 선택
2. 알림 받기 위해 워크로드를 관리하고 있는 네임스페이스 선택
3. 설정 메뉴 선택
4. 알림 정책 선택
5. 알림 정책 생성
6. 알림 정책 명: test-type-cpu-node-selector
7. 알림 규칙 명: test-type-cpu-node-selector
8. 타입: Node Selector
9. Selector 추가
10. app=test 작성
11. app=test 설정이 있는 deploy에서 memory 사용률이 70% 이상일 시 알림 수준을 Critical 수준으로 메일 or 슬랙으로 알림 발송
12. 알림 발송 시간에 대한 설정은 알림 정책 고급옵션 비활성화로 처음 알림 오기까지 30초 대기(그룹 대기 시간) 후 3분 간격으로 반복 알림(그룹 반복 시간) 후 1시간 후에 다시 알림 발송(알림 반복 시간) 설정, 알림 발송 제한은 am 02 ~ am 08 시로 설정

![workload4.png](/assets/images/setting/workload4.png)


13. 발송 받을 슬랙 및 메일 추가,설정 후 알림 설정에 대한 활성화
14. 알림 정책 설정 완료



---

## 3) 타입 : 표현식(Expression)

![workload5.png](/assets/images/setting/workload5.png)

1. 알림을 받고자 하는 클러스터 노드 선택
2. 알림 받기 위해 워크로드를 관리하고 있는 네임스페이스 선택
3. 설정 메뉴 선택
4. 알림 정책 선택
5. 알림 정책 생성
6. 알림 정책명: demo-workload-heapused-alert 작성
7. 알림 규칙 추가
8. 알림 규칙명: demo-workload-heapused-alert 작성
9. 타입을 Expresstion으로 지정 클러스터 pod에 대한 heapused 사용량이 0 이상일 시 알림 수준을 critical 수준으로 메일 or 슬랙으로 알림 발송, 알림 발송 시간에 대한 설정은 알림 정책 고급옵션 활성화EX) apm_HeapUsed{namespace="test"}
10. 발송 받을 슬랙 및 메일 추가,설정

![workload6.png](/assets/images/setting/workload6.png)


11. 처음 알림 오기까지 30초 대기(그룹 대기 시간) 후 3분 간격으로 반복 알림(그룹 반복 시간) 후 1시간 후에 다시 알림 발송(알림 반복 시간) 설정, 알림 발송 제한은 am 02 ~ am 08 시로 설정
12. 알림 규칙 활성화
13. 알림 규칙 설정 완료


---


## 노드 관련 PromQL 리소스 메트릭


- apm_ActiveService
- apm_ElapsedTime
- apm_GcCount
- apm_GcTime
- apm_ErrorRate
- apm_HeapUsed
- apm_PermUsed
- apm_ServiceCount
- apm_TPS
- apm_RecentUser



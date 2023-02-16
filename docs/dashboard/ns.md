---
layout: default
title: 3.4 네임스페이스
nav_order: 4
parent: 3. 대시보드
---

# 3.4 네임스페이스
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

## 네임스페이스 대시보드
네임스페이스는 클러스터에서 쿠버네티스 리소스 그룹을 격리하는 역할을 수행합니다. 네임스페이스 기반의 리소스의 경우 리소스의 이름이 네임스페이스 내에서 유일해야 합니다. 이를 이용해 팀 또는 프로젝트 별로 네임스페이스를 구성하여 논리적으로 독립시킬 수 있습니다.

네임스페이스 메뉴에서는 클러스터 내 네임스페이스를 관리할 수 있습니다. 네임스페이스의 생성, 수정, 삭제가 가능하며 CPU나 메모리와 같은 시스템 리소스에 대해 사용 제한 등을 설정할 수 있으며 제공하는 정보는 다음과 같습니다.


![ns-01.png](/assets/images/dashboard/ns-01.png){: width="800" }

---

## 메뉴이동
`네임스페이스`

![ns-menu.png](/assets/images/dashboard/ns-menu.png)

---


**네임스페이스 목록**

|항목|설명|
|:--|:--|
|USER NAMESPACES |사용자가 생성한 네임스페이스로 애플리케이션을 배포|
|SYSTEM NAMESPACES | 쿠버네티스 및 아코디언 운영에 필요한 리소스가 배포된 네임스페이스 |

**일반**

|항목|	설명|
|:--|:--|
| Labels | 네임스페이스 레이블로 조회 시 레이블을 이용해 필터링 가능 |
| Annotations | 네임스페이스 어노테이션으로 네임스페이스 설정 등을 저장 |
| PodNodeSelector | 파드 배포 시 해당 레이블의 노드에 배포하도록 설정 |

---

## 자원 제한


![ns-02.png](/assets/images/dashboard/ns-02.png){: width="800" }

|항목|	설명|
|:--|:--|
| Container Default Limit & Request | 쿠버네티스의 리밋레인지를 이용해 시스템 리소스(CPU/메모리) 제한 설정 |
| Resource Quotas | 쿠버네티스의 리소스쿼터를 이용해 쿠버네티스 리소스 및 시스템 리소스(CPU/메모리) 제한 설정 |


---

## 멤버

![ns-03.png](/assets/images/dashboard/ns-03.png){: width="800" }

|항목|	설명|
|:--|:--|
| Namespace Users |  네임스페이스 사용자 할당 및 권한 설정 |
| Namespace Groups | 네임스페이스 사용자 그룹 할당 및 권한 설정 |

---

## APM

![ns-04.png](/assets/images/dashboard/ns-04.png){: width="800" }

|항목|	설명|
|:--|:--|
| APM 수집 서버 |  네임스페이스 내 스카우터 서버 배포 설정 |
| APM 수집 | 네임스페이스 내 스카우터 에이전트의 타겟 수집 서버 설정 <br> (타겟 수집 서버의 네임스페이스를 선택) |

---

## YAML

![ns-05.png](/assets/images/dashboard/ns-05.png){: width="800" }

|항목|	설명|
|:--|:--|
| 수정 | 편집기에서 수정한 내용을 반영 | 

---

## 네임스페이스 생성
좌측 상단의 `+생성` 버튼을 선택하여 네임스페이스 생성에 필요한 정보를 입력할 수 있습니다.

![ns-06.png](/assets/images/dashboard/ns-06.png){: width="800" }

네임스페이스 이름만으로도 생성할 수 있지만 고급 옵션을 이용하면 APM 관련 설정이 가능하다.

|항목|	설명|
|:--|:--|
| APM 수집 서버 | 네임스페이스 내 스카우터 서버 배포 설정 |
| APM 수집 | 네임스페이스 내 스카우터 에이전트의 타겟 수집 서버 설정 <br> (타겟 수집 서버의 네임스페이스를 선택) |

---

## 네임스페이스 수정

**일반 정보 설정**

네임스페이스 레이블, 어노테이션, 파드노드셀렉터를 변경할 수 있습니다. 항목별로 `+추가`, `수정`, `삭제` 버튼을 이용해 값을 설정하거나, 수정/삭제합니다. 각 항목에 등록 시에는 키/값 형태로 설정한다.

![ns-07.png](/assets/images/dashboard/ns-07.png){: width="800" }

---

## 자원 제한 설정
쿠버네티스의 리밋레인지와 리소스쿼터를 이용해 네임스페이스 별로 자원을 제한할 수 있습니다.

![ns-08.png](/assets/images/dashboard/ns-08.png){: width="800" }


|항목|	설명|
|:--|:--|
| CPU REQUEST | 컨테이너별 최소 CPU 요구량 |
| CPU LIMIT |  컨테이너별 최대 CPU 사용량 |
| MEMORY REQUEST |  컨테이너별 최소 메모리 요구량 |
| MEMORY LIMIT | 컨테이너별 최대 메모리 사용량 |

![ns-09.png](/assets/images/dashboard/ns-09.png){: width="800" }


|항목|	설명|
|:--|:--|
| NAME | 리소스쿼터 이름 | 
| CPU REQUEST | 네임스페이스에 배포하는 파드들에 대해 CPU 요구량의 총량을 제한 |
| CPU LIMIT | 네임스페이스에 배포하는 파드들에 대해 CPU 최대 사용량의 총량을 제한 |
| MEMORY REQUEST | 네임스페이스에 배포하는 파드들에 대해 메모리 요구량의 총량을 제한 | 
| MEMORY LIMIT |  네임스페이스에 배포하는 파드들에 대해 메모리 최대 사용량의 총량을 제한 |
| COUNT/PODS | 네임스페이스에 배포할 수 있는 파드의 총 수 |
| COUNT/DEPLOYMENTS.APPS | 네임스페이스에 배포할 수 있는 디플로이먼트의 총 수 |
| COUNT/STATEFULSETS.APPS | 네임스페이스에 배포할 수 있는 스테이트풀셋의 총 수 |
| COUNT/DAEMONSETS.APPS | 네임스페이스에 배포할 수 있는 데몬셋의 총 수 |
| COUNT/JOBS.BATCH | 네임스페이스에 배포할 수 있는 잡의 총 수 |
| COUNT/CRONJOBS.BATCH | 네임스페이스에 배포할 수 있는 크론잡의 총 수 |
| COUNT/INGRESSES.EXTENSIONS | 네임스페이스에 배포할 수 있는 인그레스의 총 수 |
| COUNT/SERVICES | 네임스페이스에 배포할 수 있는 서비스의 총 수 |
| COUNT/PERSISTENTVOLUMECLAIMS | 네임스페이스에 배포할 수 있는 퍼시스턴트볼륨클레임의 총 수 |

---

## 멤버 설정
네임스페이스를 사용할 수 있는 사용자와 그룹을 설정한다. 사용자/그룹 별로 각각 권한을 설정할 수 있습니다. `+추가` 버튼을 선택하여 사용자/그룹을 추가하거나 개별 사용자/그룹의 우측에 있는 수정, 삭제 버튼을 이용해 변경할 수 있습니다.

![ns-10.png](/assets/images/dashboard/ns-10.png){: width="800" }


**APM 설정**
APM 설정은 네임스페이스 배포 시 설정한 값을 변경할 수 없습니다.

---

## 네임스페이스 삭제
우측 상단의 `삭제` 버튼을 선택하여 해당 네임스페이스를 삭제할 수 있습니다.

![ns-11.png](/assets/images/dashboard/ns-11.png){: width="800" }


---
## 연습문제

**1. 아래 속성으로 네임스페이스를 생성하세요.**

```
- Namespace Name:  mantech
- APM 수집 서버 : On
- APM 수집 : Off

- 리밋레인지 
  + CPU Request/Limit : 4 core
  + Memory Request/Limit : 4096mi
```


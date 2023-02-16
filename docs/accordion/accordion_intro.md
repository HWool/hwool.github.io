---
layout: default
title: 2.1 Accordion 이란?
nav_order: 1
parent: 2. Accordion v2
---
# 2.1 Accordion 이란?
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 🧬 Accordion(아코디언) 출시

아코디언 1.0은 Kubernetes 1.8 버전을 기반으로 2017년 11월에 출시되었습니다. 
당시 엔터프라이즈 환경은 베어메탈과 가상머신 인프라에 플랫폼과 애플리케이션 프로비저닝을 하고 있었습니다.
시장에서 오픈소스 제품이 활성화되면서 기존 벤더락인 OS와 미들웨어는 확장에 대한 제한이 없어졌고 프로비저닝 자동화에 대한 관심이 커지던 시기였습니다. 게다가 시장에서는 퍼블릭 클라우드 공급자가 빠르게 진출하고 있었습니다.

오픈소스 활성화와 클라우드로 인해 서비스 확장 제한은 없었지만 기존 엔터프라이즈 환경에서 시장의 요구사항를 따라오기에는 기술적인 한계가 존재했습니다.

![acc-4.png](/assets/images/accordion/acc-4.png){: width="600" }

---

## 📍 애플리케이션 현대화를 위한 PaaS의 필수 요구 사항들

아코디언은 이러한 엔터프라이즈 시장의 요구 사항을 해결하기 위해서 출발했습니다.

![accordion.png](/assets/images/accordion/accordion.png){: width="800" }

**개방성**

- 오픈소스 기반의 컨테이너 플랫폼
- 오픈소스 기반의 미들웨어
- 플랫폼간 자유로운 이식
- 이기종 플랫폼간 확장
- 이기종 플랫폼간 CI/CD

**표준화**

- 표준 쿠버네티스 기반
- 표준 컨테이너 이미지로 관리
- 플랫폼간 종속성 배제
- 멀티/하이브리드 클라우드간 자유로운 이동성과 확장

**민첩성**
- 신속한 배포 및 롤백
- 신속한 애플리케이션 확장
- 다수의 클라우드로 분산 배치

**자동화**
- 자동 빌드
- 자동 배포
- 자동 확장
- 자동 부하분산
- 자동 장애 처리
- 자동 네트워킹

---

## 👍 아코디언 특징

**Kubernetes 기반 PaaS - 아코디언**

- 컨테이너 기반의 애플리케이션을 손쉽게 배포하고 자동화된 운영관리를 제공하는 엔터프라이즈급 PaaS 솔루션
- 업계 표준 쿠버네티스와 컨테이너를 기반으로 한 개방형을 지향
- 단일 콘솔로 다중의 K8S 클러스터 관리를 통한 복잡도 제거
- Kubernetes 릴리즈 라이프 사이클 동일
- CNCF, KCSP 인증

---

**멀티 클러스터 지원**

![acc-8.png](/assets/images/accordion/acc-8.png)

- 클러스터간 배포 : 개발기, 검증기, 운영기 등 서로 다른 클러스터 환경에서 앱을 자동으로 배포할 수 있습니다.
- 통합 인증 / 권한 : 다중 테넌트 관리를 위해 통합 인증을 제공합니다. Cluster, Namespace, User 별로 권한을 
상세히 설정할 수 있으며, 쿠버네티스의 RBAC와 자동 연동 설정 됩니다.

---

**다양한 앱 이미지 번들**

개발에 필요한 환경과 앱의 구성에 소요되는 시간을 단축할 수 있어 개발 생산성을 극대화 할 수 있습니다. 앱에 대한 전문 지식이 없어도 카탈로그에서 쉽게 앱을 배포합니다.

![acc-9.png](/assets/images/accordion/acc-9.png)

---

**자동 확장 지원**

- CPU, Memory 사용량에 따른 Pod 자동 확장/축소를 지원
- Thread, TPS, GCtime, Elapsed time 등 다양한 메트릭 기준으로 Auto Scale in/out 지원합니다.

---

**다양한 K8S 클러스터에 대한 통합 모니터링**

- 분리된 K8S 클러스터와 CSP별로 모니터링 콘솔을 여러 개 띄울 필요가 없습니다. K8S 클러스터, 시스템, 노드, 네임스페이스, 워크로드, 애플리케이션, 감사 로그를 단일 콘솔에서 모니터링 할 수 있습니다.

- 내장된 APM을 통해 Active service, X log, TPS, 응답시간, 쓰레드 등의 더 세밀한 앱 성능 모니터링을 제공합니다.
- 다양한 알림 기능 : 이메일, SMS, 슬랙을 통해 주요 이벤트에 대한 알람 수신을 받을 수 있습니다.

---

**CI/CD 파이프라인**

GUI를 통해 복잡한 스크립트나 개발 필요없이 쉽게 CI/CD Pipeline을 생성하고 과정을 가시화 할 수 있으며, 멀티 테넌시의 지원으로 민감한 배포 과정의 전략에 대한 보안을 유지할 수 있습니다. 

![acc-11.png](/assets/images/accordion/acc-11.png)


---

**컨테이너 환경을 위한 보안 취약성 검사**

- 아코디언은 Sonarqube와 Anchore를 통해 빌드 전 소스코드 검사, 배포전 POD에 대한 검사를 통해 보안 취약한 소스와 앱을 걸러낼 수 있으며, 3rd party 툴과의 연계 또한 가능합니다.

- 코드 및 컨테이너 보안 취약성 검사 단계를 CI/CD Pipeline의 단계에 적용함으로써 보안 정책에 위배된 앱을 배포 단계에서 원천 차단할 수 있습니다.
감사로그를 통해서 외부 침입을 추적하고, 모든 활동을 시간 별로 자동 기록합니다.



---

## 🔑 CNCF Member

쿠버네티스를 기반으로 한 클라우드 네이티브 애플리케이션 통합 관리 플랫폼 ‘아코디언(ACCORDION)’이 CNCF 재단의 쿠버네티스 적합성 인증 프로그램(Certified Kubernetes Conformance Program)에서 쿠버네티스 적합성(Certified Kubernetes, CK) 인증을 획득했습니다.


![cncf-01.png](/assets/images/accordion/cncf-01.png){: width="800" }


- Software conformance(Certified Kubernetes)
- Kubernetes Certified Service Provider(KCSP)


![cncf-02.png](/assets/images/accordion/cncf-02.png){: width="800" }

---
layout: default
title: 5.2.1 카탈로그 배포
nav_order: 2
grand_parent: 5. 애플리케이션
parent: 5.2 카탈로그
---

# 카탈로그 
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
## 메뉴이동

`클러스터` ➡ `네임스페이스`

![deploy-001.png](/assets/images/application/catalog/deploy-001.png){: width="800" }

`애플리케이션` ➡ `카탈로그`

![catalog-001.png](/assets/images/application/catalog/catalog-001.png)


---

## 카탈로그 화면

카탈로그에 대한 기본 정보와 배포 현황에 대한 정보를 제공합니다.

- 카탈로그 템플릿 요약
- 카탈로그 템플릿 설명
- 마지막 배포현황


![catalog-002.png](/assets/images/application/catalog/catalog-002.png){: width="800" }

**배포 리소스**

카탈로그로 배포한 쿠버네티스 리소스 정보를 제공합니다.

- 디플로이먼트, 스테이트풀셋, 서비스등 워크로드 정보

![catalog-003.png](/assets/images/application/catalog/catalog-003.png){: width="800" }

**이력**

카탈로그 파이프라인 실행 이력을 제공합니다.

- 카탈로그로 배포한 이력 정보 제공 및 배포 관리 
- 카탈로그 배포 과정 조회 
- 배포 중인 카탈로그의 배포 중단 
- 배포에 성공한 이력에 대해 재배포 또는 롤백 

![catalog-004.png](/assets/images/application/catalog/catalog-004.png){: width="800" }


**YAML**

카탈로그의 YAML 내용을 확인하고 수정 가능합니다.

![catalog-005.png](/assets/images/application/catalog/catalog-005.png){: width="800" }


---
## 카탈로그 생성
카탈로그 메뉴의 `+생성` 버튼을 선택하면 카탈로그 생성에 필요한 카탈로그 템플릿을 선택할 수 있습니다.

![deploy-002.png](/assets/images/application/catalog/deploy-002.png){: width="800" }

아코디언은 Tomcat, Wildfly 등에 대한 템플릿을 기본 제공하며 카탈로그 템플릿은 추가하거나 변경할 수 있습니다.

![deploy-003.png](/assets/images/application/catalog/deploy-003.png){: width="800" }

---

**일반 설정**

생성할 카탈로그에 대한 템플릿을 고르고 `다음: 일반 설정` 버튼으로 다음 과정으로 넘어갑니다.
다음 과정인 일반 설정에서는 카탈로그의 이름이나 설명, 로고 이미지와 같은 생성하려는 카탈로그에 대한 정보를 입력합니다.

![deploy-004.png](/assets/images/application/catalog/deploy-004.png){: width="800" }


**카탈로그 기본 정보**

| 항목        |  설명  |
|:------------|:-------|
| 이름 | 카탈로그 이름 | 
| 요약 | 카탈로그에 대한 간단한 설명 |
| 상세설명 | 카탈로그에 대한 상세한 설명 |
| 로고 이미지 | 카탈로그의 로고 이미지 (미설정할 경우 템플릿의 로고로 설정) |

`고급 설정`을 선택하면 기본 정보 외 배포 정책 등 상세한 설정이 가능합니다. 
`고급 설정`의 항목은 카탈로그마다 차이가 있으며 자주 사용하는 항목은 다음과 같습니다.

![deploy-005.png](/assets/images/application/catalog/deploy-005.png){: width="800" }

**배포전략 / 배포 정책 종류**

| 정책        |  설명  | 유사한 명령어 |
|:------------|:-------|:-------|
| Apply | 리소스가 존재하면 스펙 반영 | kubectl apply …​ |
| IfExistReplace | 리소스가 존재하면 스펙 대체 | kubectl replace …​ |
| IfExistSkip | 리소스가 존재하면 배포 생략 | kubectl create …​ |
| IfExistUpdate | 리소스가 존재하면 대체 우선의 업데이트 |  |

**컨테이너 이미지 정책**

카탈로그로 애플리케이션을 배포할 때 컨테이너 이미지 빌드를 수행하는 파이프라인을 수행하는 경우 이미지를 저장할 저장소와 최대 보관 개수를 설정합니다.

---

**배포 리소스 설정**

카탈로그 정보 입력이 완료되면 `다음: 배포 리소스 설정` 버튼으로 다음 과정으로 넘어갑니다. 
다음 과정인 `배포 리소스 설정`에서는 환경변수 또는 시스템 리소스 할당과 같이 카탈로그로 배포하는 쿠버네티스 리소스에 대한 정보를 입력합니다.

![deploy-006.png](/assets/images/application/catalog/deploy-006.png){: width="800" }


---

**파이프라인 설정**

배포 리소스에 대한 설정이 완료되면 `다음: 파이프라인 설정` 버튼으로 다음 과정으로 넘어갑니다. 다음 과정인 `파이프라인 설정`에서는 쿠버네티스 리소스를 배포하기 전에 수행하는 파이프라인에 대해 설정합니다. 
파이프라인은 기본 파이프라인 템플릿을 가지고 있으며 사용자는 이를 수정하여 배포하는 카탈로그마다 개별 설정할 수 있습니다.

![deploy-007.png](/assets/images/application/catalog/deploy-007.png){: width="800" }

---

**카탈로그 생성완료**

`생성` 버튼을 클릭하면 다시 카탈로그 화면으로 돌아오게 됩니다. 그리고 생성된 카탈로그를 확인할 수 있습니다.

![deploy-008.png](/assets/images/application/catalog/deploy-008.png){: width="800" }

---

## 카탈로그 배포

카탈로그를 배포하기 위해서는 화면의 일반 탭 `배포` 버튼을 클릭해야합니다.
`신규배포` 팝업에서 배포의 `요약`,`설명`을 입력하고 배포를 실행합니다.

![deploy-009.png](/assets/images/application/catalog/deploy-009.png){: width="800" }

배포 중인 카탈로그는 `이력` 탭에서 파이프라인 작업 내역을 실시간으로 확인 가능합니다.

![deploy-011.png](/assets/images/application/catalog/deploy-011.png){: width="800" }

---
## 카탈로그 수정
카탈로그를 변경하기 위해서 목록에서 카탈로그를 찾아 수정 버튼을 선택합니다. 카탈로그 수정 시 설정값은 앞에 카탈로그 생성 시 입력했던 값과 유사합니다.

![catalog_update.png](/assets/images/application/catalog/catalog_update.png){: width="800" }


---

## 카탈로그 삭제
삭제하려는 카탈로그를 선택하고 우측의 삭제 버튼을 선택합니다.
모달에서 네임스페이스와 카탈로그 이름을 입력하여 삭제합니다.

![catalog_delete.png](/assets/images/application/catalog/catalog_delete.png){: width="800" }

---

## 연습문제

**1. 카탈로그를 이용해서 Wildfly 워크로드를 생성하세요.**

일반설정
```
- name: mantech-wildfly
- 카탈로그 : acc-wildfly
- 상세설명 : 카탈로그 생성
- 고급설정 : 배포 클러스터(host-cluster), 네임스페이스(mantech) 선택
- 컨테이너 이미지 정책 : 레지스트리 user-registry, 보관개수 4
```

배포 리소스 설정
```
- 리소스그룹1.deploy.env.컨테이너변수 : JAVA_OPTS value(-Duser.timezone=GMT+09:00 -Djava.security.egd=file:/dev/./urandom -XX:+UseParallelGC -XX:+UseParallelOldGC -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=$JBOSS_HOME/standalone/log/$HOSTNAME/heapdump -Djava.net.preferIPv4Stack=true -Djboss.modules.system.pkgs=org.jboss.byteman -Xms1024m -Xmx1024m) 
- 레플리카 파드 수 : 2 
- resource.limits.cpu : 1
- serviceType : NodePort
```

파이프라인 설정
```
vcs-get : repo 입력(https://github.com/mantech-accordion/jpetstore-6.git)
```


**2. 배포된 카탈로그의 배포를 실행하세요.**


**3. 배포된 워크로드 상태를 워크로드 대시보드에서 확인하세요.**
---
layout: default
title: 5.3.1 파이프라인
nav_order: 2
grand_parent: 5. 애플리케이션
parent: 5.3 빌드
---

# 파이프라인 
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

## 파이프라인
파이프라인은 이미지 빌드 및 배포를 위해 한개 이상의 태스크를 가지고 태스크의 연관 관계(디펜던시)를 관리합니다. 파이프라인은 지속적으로 수행이 가능하며 수행에 대한 이력을 관리할 수 있습니다.

![pipeline-list.png](/assets/images/application/pipeline/pipeline-list.png){: width="800" }

![pipeline-005.png](/assets/images/application/pipeline/pipeline-005.png){: width="800" }


---

## 메뉴이동

`애플리케이션` ➡ `빌드` ➡ `파이프라인`

![pipeline-001.png](/assets/images/application/pipeline/pipeline-001.png){: width="800" }

---


## 파이프라인 생성

`+생성` 버튼을 선택하면 나타나는 모달에서 파이프라인 정보를 입력하여 생성할 수 있습니다. 
생성 시에는 `FORM` 또는 `YAML`로 입력할 수 있습니다.

![pipeline-002.png](/assets/images/application/pipeline/pipeline-002.png){: width="800" }

파이프라인 생성 시 파이프라인 템플릿에서 태스크에 대한 구성 정보를 불러와 설정할 수 있습니다. 
템플릿을 수정해서 사용하고 싶은 경우 파이프라인 생성 후 수정 화면에서 변경사항을 반영합니다.


![pipeline-003.png](/assets/images/application/pipeline/pipeline-003.png){: width="800" }

**파이프라인 입력값**

| 항목        |  설명  |
|:------------|:-------|
| 파이프라인 이름 | 생성할 파이프라인 이름 |
| 파이프라인 템플릿 선택 | 파이프라인을 구성하는 태스크에 대한 정보를 템플릿으로 선택 |
| 파이프라인 요약 | 파이프라인에 대한 한줄 요약 (파이프라인 목록에 표시) |
| 파이프라인 설명 | 파이프라인에 대한 설명을 마크다운으로 작성 |

파이프라인 생성 시 `None` 을 선택하면 태스크가 없는 파이프라인을 생성할 수 있습니다.

카탈로그 작성은 `YAML` 으로도 작성 가능합니다.

![pipeline-004.png](/assets/images/application/pipeline/pipeline-004.png){: width="800" }

---

**태스크 템플릿 불러오기**

태스크가 없는 파이프라인의 경우에는 우측에 안내 문구가 표시되며 안내 문구의 태스크 생성 버튼을 선택하면 태스크 구성을 할 수 있습니다. 파라미터까지 설정이 완료되면 저장 버튼을 선택해 작성을 완료합니다.


![pipeline-011.png](/assets/images/application/pipeline/pipeline-011.png){: width="800" }

**태스크 템플릿 종류**

| 종류        |  설명  |
|:------------|:-------|
| normal | 일반 유형 |
| vcs | Version Control System 유형 (e.g. git, svn) | 
| build | 소스빌드 유형 (e.g. maven, ant, gradle) | 
| image | 컨테이너 이미지를 만드는 유형 (e.g. kaniko) | 
| approval | 승인 태스크로 spec.tasks[].approvers 에 대해 반드시 기술하지만 container를 기술하지는 않음 |
| artifact | 파이프라인마다 설정되어 있는 S3저장소에 업로드한 데이터를 조회(spec.tasks[].buckets 을 반드시 기술하지만 container를 기술하지는 않음) |


---

## 파이프라인 수정


파이프라인을 생성할 때 태스크에 대한 정보는 파이프라인 템플릿에서 가져와 구성합니다. 파이프라인의 태스크에 대한 정보를 변경해야하는 경우 변경할 파이프라인을 찾아 파이프라인 탭의 `수정` 버튼을 선택합니다.

![pipeline-010.png](/assets/images/application/pipeline/pipeline-010.png){: width="800" }


---

## 파이프라인 실행과 중지
이력 탭에서 실행 버튼을 선택하면 파이프라인의 빌드가 실행되는 모습을 확인할 수 있습니다.

![pipeline-run.png](/assets/images/application/pipeline/pipeline-run.png){: width="800" }

상단의 `중지` 버튼 또는 우측의 멈춤 아이콘 버튼을 선택하면 진행 중인 파이프라인의 빌드를 중지시킬 수 있습니다. 그 외에 빌드 내역 중 특정 빌드로 다시 배포하고 싶은 경우 해당 빌드 내역의 우측 버튼을 이용해 다시 배포도 가능합니다. 
이 경우 다시 실행하려는 빌드가 성공으로 완료되었을 때만 가능합니다.


**파이프라인 태스크 상태**

| 이미지        |  태스크 상태  |
|:------------|:-------|
| ![build-status-run.png](/assets/images/application/pipeline/build-status-not-builted.png)        | 종료(Terminated): 사용자가 빌드를 중지 | 
| ![build-status-run.png](/assets/images/application/pipeline/build-status-successed.png)         | 성공(Successed)  | 
| ![build-status-run.png](/assets/images/application/pipeline/build-status-failed.png)          | 실패(Failed)  | 
| ![build-status-run.png](/assets/images/application/pipeline/build-status-running.png)    | 실행 중(Running) | 
| ![build-status-run.png](/assets/images/application/pipeline/build-status-pending.png) | 대기(Pending) |
| ![build-status-run.png](/assets/images/application/pipeline/build-status-unstable.png) | 경고(Warning): 태스크를 수정 중에 잘못된 데이터를 입력하는 경우 발생 |

빌드 이력을 선택하면 개별 빌드에 대한 상세 정보를 확인할 수 있습니다.

![build-history-detail.png](/assets/images/application/pipeline/build-history-detail.png){: width="800" }

개별 빌드는 하나 이상의 태스크로 구성되며 태스크를 선택하면 해당 태스크에서 발생한 로그를 확인할 수 있습니다.

![build-history-log.png](/assets/images/application/pipeline/build-history-log.png){: width="800" }


## 파이프라인 삭제

삭제하려는 파이프라인을 선택하고 우측의 삭제 버튼을 선택합니다.
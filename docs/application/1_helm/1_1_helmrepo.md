---
layout: default
title: 5.1.1 헬름 레퍼지토리
nav_order: 2
grand_parent: 5. 애플리케이션
parent: 5.1 Helm
---

# 헬름 레퍼지토리
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

## 헬름 레퍼지토리

---
## 메뉴이동
`글로벌 메뉴` ➡ `헬름`

![helm_menu.png](/assets/images/application/helm/helm_menu.png)

---

## 헬름 레퍼지토리 관리

아코디언에서는 헬름을 사용하기 위해서는 먼저 헬름 레퍼지토리를 등록해야합니다. 기존 사용중이었던 헬름 레퍼지토리도 간편하게 등록 및 관리 가능합니다.

![helm-repo-1.png](/assets/images/application/helm/helm-repo-1.png){: width="800" }

| 항목        |  설명  |
|:------------|:-------|
| NAME        | 저장소 이름 (필수) | 
| URL         | 저장소 URL (필수)  | 
| ID          | 저장소 아이디 (옵션)  | 
| PASSWORD    | 저장소 패스워드 (옵션)  | 


---

## 헬름 레퍼지토리

등록된 `헬름 레퍼지토리`에서는 헬름 차트 검색과 다운로드 가능합니다.

![helm-repo-3.png](/assets/images/application/helm/helm-repo-3.png){: width="800" }


---

## 아코디언 차트 저장소

아코디언에서 제공하고 있는 비공개 저장소는 Go(Golang)로 작성된 오픈 소스 헬름 레퍼지토리 서버입니다.

Google Cloud Storage, Amazon S3, Azure Blob Storage, Openstack Object Storage 를 포함한 클라우드 스토리지 백엔드를 지원합니다.

![helm-repo-2.png](/assets/images/application/helm/helm-repo-2.png){: width="800" }


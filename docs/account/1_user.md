---
layout: default
title: 4.1 사용자
nav_order: 4
parent: 4. 계정
---

# 4-1. 사용자
{: .no_toc }

<!-- 사용자별로 다수 그룹에 속할 수 있으며 그룹은 멤버를 통하여 여러의 권한을 가질 수 있습니다. -->
사용자는 글로벌 권한/클러스터 권한/네임스페이스 권한을 사용자에게 부여하여 글로벌/클러스터/네임스페이스별 모두 다르게 권한을 설정할 수 있습니다.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

<div class="code-example" markdown="1">
Global
{: .label .label-purple }
</div>

---

## 메뉴이동
`계정` ➡ `사용자`

![user.png](/assets/images/auth/user.png)

---

**사용자 목록**

메뉴에서 [계정] - [사용자]를 클릭하면 다음과 같이 사용자의 목록을 확인할 수 있습니다. 좌측 사용자 목록에서 사용자 아이콘은 사용자 Active 여부에 따라 녹색/빨강으로 표시됩니다.

![4_user-list.png](/assets/images/auth/4_user-list.png){: width="800" }

---

**사용자 생성**

[생성]을 클릭 후 내용을 입력하여 사용자를 생성할 수 있습니다.

![4_user-create.png](/assets/images/auth/4_user-create.png){: width="800" }

| 항목  | 설명 |
|---|---|
| ID   | 사용자 ID를 입력   |
| Active   | 사용자 활성화 (Enable, Disable)   |
| First Name   | 사용자 이름을 입력   |
| Last Name   | 사용자 성을 입력   |
| Email   | 사용자 이메일을 입력   |
| Group   | 그룹 목록 중 하나의 그룹을 선택  |
| Password   | 특수문자 1글자 이상 포함하고 8자 ~ 16자이며 영문 숫자 특수문자만 입력  |
| Confirm Password   | 사용자 비밀번호를 확인   |
| Temporary   | ON으로 설정 시 입력한 비밀번호는 임시 비밀번호로 발급됩니다. 로그인 시 입력한 비밀번호로 로그인 후 새로운 비밀번호를 설정|


**사용자 수정**

사용자 목록에서 생성한 사용자를 클릭하여 수정할 내용 입력 후 [수정]버튼을 클릭하면 수정할 수 있습니다.



![4_user-update.png](/assets/images/auth/4_user-update.png){: width="800" }

---

**사용자 삭제**

[삭제] 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 사용자 명 입력 후 [Delete] 버튼 클릭 시 사용자가 삭제됩니다.


![4_user-delete.png](/assets/images/auth/4_user-delete.png){: width="800" }

---

## 연습문제

**1. 사용자를 생성하세요.**

```
Active : Enable
Group : 미선택
```
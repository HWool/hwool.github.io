---
layout: default
title: 4.2 그룹
nav_order: 4
parent: 4. 계정
---

# 4-2. 그룹
{: .no_toc }

그룹은 사용자 집합을 의미합니다. 사용자는 특정 사용자에게 권한을 부여한다면 그룹은 사용자 집합에 권한을 부여할 수 있어서 팀이나 프로젝트 단위와 같이 다양한 경우에 간단하게 권한을 부여 할 수 있습니다.



## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 메뉴이동
`계정` ➡ `그룹`

![group.png](/assets/images/auth/group.png)

---

**그룹 생성**

그룹은 그룹별로 사용자 목록을 관리합니다.
그룹 생성 시 이름만 입력하며 아래와 같이 빈 사용자 목록을 확인 할 수 있습니다.

![4_group-create.png](/assets/images/auth/4_group-create.png){: width="800" }

---

**그룹에 사용자 추가**

그룹은 사용자 집합으로 사용자 목록을 관리합니다.
사용자 메뉴에서 그룹에 추가할 특정 사용자를 목록에서 클릭합니다.
우측의 사용자 Group 항목에서 사용자에게 추가하려는 Group을 입력하거나 선택하여 그룹에 사용자를 추가합니다.

![4_group-user-add.png](/assets/images/auth/4_group-user-add.png){: width="800" }

사용자에 그룹 추가 후 해당 그룹을 확인하면 그룹의 사용자 목록에 사용자가 추가된 것을 확인 할 수 있습니다.

![4_group-user-list.png](/assets/images/auth/4_group-user-list.png){: width="800" }

| 항목  | 설명 |
|---|---|
| Name   | 그룹명  |
| UID  | 그룹 고유한 ID  |
| 사용자 목록   | 그룹의 사용자 목록  |

---

**그룹에 글로벌 권한 부여**

권한 부여는 멤버를 통해서만 권한을 부여할 수 있습니다.
권한과 멤버는 각각 글로벌/클러스터/네임스페이스가 존재합니다.

글로벌 권한을 부여하려면 글로벌 권한에서 부여하려는 권한을 생성합니다.

<!-- 상위 디렉토리로 연결이 안됨 -->
[글로벌 권한 생성] 참고

글로벌 권한을 생성한 후 글로벌 멤버의 Group 항목에서 [추가] 버튼을 클릭합니다.
그리고 그룹과 그룹에 부여하려는 권한을 가진 글로벌 권한을 선택하여 글로벌 멤버로 설정합니다.
클러스터/네임스페이스도 글로벌 권한 부여와 동일한 방식으로 권한 부여합니다.

![4_group-global-member.png](/assets/images/auth/4_group-global-member.png){: width="800" }

---

**그룹 삭제**

[삭제] 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 그룹 명 입력 후 [Delete] 버튼 클릭 시 그룹이 삭제됩니다.

![4_group-delete.png](/assets/images/auth/4_group-delete.png){: width="800" }


---

## 연습문제

**1. 그룹을 생성하세요.**
```
그룹 이름 : mantech
```

**2. 사용자 메뉴에서 방금 생성한 그룹(mantech)으로 지정하세요.**

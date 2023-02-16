---
layout: default
title: 4.3.3 네임스페이스 권한
nav_order: 4
grand_parent: 4. 계정
parent: 4.3 권한
---

# 네임스페이스 권한
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

## 네임스페이스 권한
네임스페이스 권한은 네임스페이스 메뉴에 대한 권한을 설정 할 수 있습니다.

---

## 메뉴이동
`계정` ➡ `네임스페이스 권한`

![ns.png](/assets/images/auth/ns.png)

---

**네임스페이스 권한 목록**

메뉴에서 [계정] - [네임스페이스 권한]을 클릭하면 다음과 같이 네임스페이스의 목록을 확인할 수 있습니다.

![4_account-auth-namespace.png](/assets/images/auth/4_account-auth-namespace.png){: width="800" }

---

**네임스페이스 권한 생성**

[생성]을 클릭 후 내용을 입력하여 네임스페이스 권한을 생성할 수 있습니다. [추가]를 클릭하여 메뉴와 메뉴에 대한 권한을 추가할 수 있습니다.

![4_account-auth-namespace-create.png](/assets/images/auth/4_account-auth-namespace-create.png){: width="800" }

---

**생성된 네임스페이스 권한 확인**

네임스페이스 권한 목록에서 생성한 권한이름으로 생성 된 것을 확인할 수 있으며, 입력 정보를 수정하거나 추가 후에 [수정]버튼을 클릭하여 수정할 수 있습니다.

![4_account-auth-namespace-create-success.png](/assets/images/auth/4_account-auth-namespace-create-success.png){: width="800" }

---

**네임스페이스 권한 삭제**

[삭제] 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스 권한 명 입력 후 [Delete] 버튼 클릭 시 네임스페이스 권한이 삭제됩니다.

![4_account-auth-namespace-delete-confirm.png](/assets/images/auth/4_account-auth-namespace-delete-confirm.png){: width="800" }

---

## 연습문제

**1. 네임스페이스 권한을 생성하세요.**

```
권한 이름 : devops
메뉴명 : 워크로드 대시보드, 네임스페이스 대시보드, 카탈로그
권한 : admin
```
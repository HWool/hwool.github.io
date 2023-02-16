---
layout: default
title: 9. 스토리지
nav_order: 9
has_children: true
permalink: /docs/storage
---

# 9. 스토리지

컨테이너 내의 디스크에 있는 파일은 임시적으로 컨테이너가 내려가면 디스크에 있는 파일은 사라지게 됩니다. 그리고 파드 집합이 공유가 필요한 파일을 공유할 수 없는 문제가 존재합니다.
이러한 문제를 위해 스토리지를 사용하여 컨테이너가 내려가도 디스크에 있는 파일을 스토리지 내에 보존하고 파드 집합에서 파일을 공유할 수 있도록 합니다.

![storage.png](/assets/images/storage/storage.png){: width="800" }
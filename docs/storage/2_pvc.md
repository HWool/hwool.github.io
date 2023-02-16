---
layout: default
title: 9.2 퍼시스턴트볼륨클레임
nav_order: 2
parent: 9. 스토리지
---

# 퍼시스턴트볼륨클레임
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

## 퍼시스턴트볼륨클레임 (PVC)

퍼시스턴트볼륨클레임 (PVC)은 사용자의 스토리지에 대한 요청입니다.
파드는 노드 리소스를 사용하고 PVC는 PV 리소스를 사용하게 됩니다. 
파드는 특정 수준의 리소스(CPU 및 메모리)를 요청할 수 있습니다.


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: populated-pvc
spec:
  dataSourceRef:
    name: example-name
    kind: ExampleDataSource
    apiGroup: example.storage.k8s.io
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
{% endhighlight %}
   
</details>

---

## 메뉴이동
`스토리지` ➡ `퍼시스턴트볼륨클레임`

![storage-002.png](/assets/images/storage/storage-002.png)

---

## 화면구성
생성된 퍼시스턴트볼륨클레임 정보를 제공합니다.

![storage-006.png](/assets/images/storage/storage-006.png){: width="800" }

---

## 퍼시스턴트볼륨클레임 생성
`+생성`을 클릭 후 내용을 입력하여 퍼시스턴트볼륨클레임를 생성할 수 있다. 퍼시스턴트볼륨클레임는 YAML로 입력할 수 있다.

![storage-007.png](/assets/images/storage/storage-007.png){: width="800" }


**퍼시스턴트볼륨클레임 입력값**

| 이름         |         값    | 
|:-------------|:------------------|
| Name	| 생성할 PVC 이름 |
| Namespace	 | 생성할 네임스페이스 이름 |
| Source - StorageClass	| 스토리지 클래스 선택 | 
| Source - Label Selector	| Selector Key/Value | 
| Access Mode	| ReadWriteOnce(RWO), ReadOnlyMany(ROX), ReadWriteMany(RWX), ReadWriteOncePod(RWOP) |
| Volume Mode	| Filesystem/Block |
| Capacity      | 용량 |



---

## 퍼시스턴트볼륨클레임 수정
퍼시스턴트볼륨클레임 목록에서 특정 퍼시스턴트볼륨클레임를 클릭하여 우측 YAML에 수정할 내용 입력 후 `수정`버튼을 클릭하면 수정할 수 있습니다.

---

## 퍼시스턴트볼륨클레임 삭제
`삭제` 버튼 클릭 시 삭제 팝업창이 나타나며 삭제하려는 해당 네임스페이스/퍼시스턴트볼륨클레임 명 입력 후 `Delete` 버튼 클릭 시 퍼시스턴트볼륨클레임이 삭제됩니다.

![pvc-delete.png](/assets/images/storage/pvc-delete.png){: width="800" }
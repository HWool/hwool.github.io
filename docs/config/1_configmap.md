---
layout: default
title: 7.1 컨피그맵
nav_order: 1
parent: 7. 구성
---

# 구성
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

## 컨피그맵(Configmap)
컨피그맵은 키-값 쌍으로 민감한 정보가 아닌 데이터를 저장하는 데 사용하는 API 오브젝트입니다. 파드는 볼륨에서 환경 변수, 커맨드-라인 인수 또는 구성 파일로 컨피그맵을 사용할 수 있습니다.


<details>
<summary>예제 Yaml</summary>
  
{% highlight yaml %}

apiVersion: v1
kind: Pod
metadata:
  name: configmap-demo-pod
spec:
  containers:
    - name: demo
      image: alpine
      command: ["sleep", "3600"]
      env:
        # 환경 변수 정의
        - name: PLAYER_INITIAL_LIVES # 참고로 여기서는 컨피그맵의 키 이름과
                                     # 대소문자가 다르다.
          valueFrom:
            configMapKeyRef:
              name: game-demo           # 이 값의 컨피그맵.
              key: player_initial_lives # 가져올 키.
        - name: UI_PROPERTIES_FILE_NAME
          valueFrom:
            configMapKeyRef:
              name: game-demo
              key: ui_properties_file_name
      volumeMounts:
      - name: config
        mountPath: "/config"
        readOnly: true
  volumes:
    # 파드 레벨에서 볼륨을 설정한 다음, 해당 파드 내의 컨테이너에 마운트한다.
    - name: config
      configMap:
        # 마운트하려는 컨피그맵의 이름을 제공한다.
        name: game-demo
        # 컨피그맵에서 파일로 생성할 키 배열
        items:
        - key: "game.properties"
          path: "game.properties"
        - key: "user-interface.properties"

{% endhighlight %}
   
</details>

---


---
## 메뉴이동
`구성` ➡ `컨피그맵`

![config-001.png](/assets/images/config/config-001.png)

---

## 화면구성
배포된 디플로이먼트 정보를 제공합니다.

![config-005.png](/assets/images/config/config-005.png){: width="800" }

---
## 컨피그맵 생성
`+생성` 을 선택하면 나타나는 모달에서 쿠버네티스 컨피그맵 리소스 정보를 입력하여 생성할 수 있습니다. 생성 시에는 FORM/YAML로 입력할 수 있습니다.

![config-006.png](/assets/images/config/config-006.png){: width="800" }

---

## 컨피그맵 수정
수정하려는 컨피그맵을 선택하고 우측의 YAML 편집기에서 정보를 변경 후 수정 버튼을 선택하여 반영합니다.

---

## 컨피그맵 삭제
삭제하려는 컨피그맵을 선택하고 우측의 삭제 버튼을 선택합니다.모달에서 네임스페이스와 컨피그맵 이름을 입력하여 삭제합니다.

![configmap-delete.png](/assets/images/config/configmap-delete.png){: width="800" }

---
## 연습문제

**1. 클러스터에 몇 개의 컨피그맵이 있습니까?**

<input />

**2. 아래 속성으로 새 컨피그맵과 파드를 생성하고 생성한 컨피그맵을 파드 환경변수로 사용하세요.**

```
- Configmap Name: game-demo
- key: "game.properties", path: "game.properties"
- key: "user-interface.properties", path: "user-interface.properties"
---
Pod name: webapp-pod
Image name: nginx
Env From: configMapKeyRef=game-demo
```


**4. 생성한 파드와 컨피그맵을 삭제하세요.**
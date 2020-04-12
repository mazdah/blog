---
layout: single
title: "바닐라 자바스크립트를 이용하여 로컬 파일 불러오기"
subtitle: "with html, javascript"
date: 2020-02-07 14:30:00 +0900
lastmod: 2020-02-07 14:30:00 +0900
background: '/img/posts/04.jpg'
author_profile: false
---

일반적으로 `html`과 `javascript`에서 로컬에 있는 파일을 불러와서 작업을 하고 싶을때 `cors`라는 정책 때문에 직접 불러올 수가 없어서

만약 로컬파일을 코드 상에서 직접 작업하고 싶다면 node.js 등을 활용해서 로컬 서버를 구성한 후 불러와야 된다.

![cors error](https://user-images.githubusercontent.com/59393359/74086007-3c0fca00-4ac2-11ea-8c28-6b7d7a390dbe.PNG)

---

하지만 사용자가 파일을 직접 불러오게끔 구성한다면 자바스크립트에서도 로컬파일을 불러와서 작업을 할 수 있다.

먼저 html코드로 사용자가 파일을 불러와서 `summit` 할 수 있도록 구성해보았다.

<br/>

---

# 1. html 코드

```html
<form>
    <div>
        <label for="input_file">파일을 추가해주세요.</label>
        <input type="file" id="input_file">
    </div>
    <div>
        <button onclick="test(event)">summit</button>
    </div>
</form>
```

label의 `for`에 input의 `id`를 넣어주어 같이 클릭 될 수 있게 했고,

파일을 불러오고나서 `summit` 버튼을 클릭하게되면 아래에 있는 `test()` 함수가 실행되게 된다.

<br/>

---

# 2. 자바스크립트 코드

아래의 자바스크립트 코드는 사용자가 불러온 txt파일을 콘솔창에 출력해주는 예제이다.

```html
<script>
    function test(event) {
        event.preventDefault(); //submit 할때 새로고침 되는것을 방지
        let fileObject = document.getElementById("input_file");
        let fileName = fileObject.files[0];

        let fr = new FileReader();
        fr.readAsText(fileName, "utf-8");

        fr.onload = () => {
            parseText(fr.result);
        }
    }

    function parseText(text) {
        console.log(text)
        // 여기서 파일 가공하면됨
    }
</script>
```

***

먼저 첫번째 `event.preventDefault();` 코드는 summit을 할때 새로고침이 되는것을 방지해주는 메소드이다.

***

아래 코드는 불러온 파일의 이름을 알아낸다.

```javascript
let fileObject = document.getElementById("file");
let fileName = fileObject.files[0];
```

***

`readAsText()`를 이용하여 텍스트파일로 읽을수 있게 하고, `utf-8`을 인자로 줌으로써 한글이 깨지지 않도록 한다.

`fr.onload()` (파일불러오는 것이 완료되면 안에있는 내용을 실행하는 함수)가 `parseText()` 함수에게 `fr.result` (파일의 내용) 를 넘겨주게 된다.

```javascript
let fr = new FileReader();
fr.readAsText(fileName, "utf-8");

fr.onload = () => {
    parseText(fr.result);
}
```

***

이제 `parseText` 함수 안에서 자유롭게 파일을 가공하면 된다.

```javascript
function parseText(text) {
    console.log(text)
}
```

<br/>

***

## 참고 링크

[mdn javascript FileReader](https://developer.mozilla.org/ko/docs/Web/API/FileReader)

<br />
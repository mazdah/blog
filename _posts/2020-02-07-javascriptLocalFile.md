---
layout: post
title: "[HTML, javascript] 바닐라 자바스크립트를 이용하여 파일 불러오기"
subtitle: "^__^"
date: 2020-02-07 14:30:00 +0900
background: '/img/posts/02.jpg'
---

일반적으로 html과 자바스크립트에서\ 로컬에 있는 파일을 불러와서 작업을 하고 싶을때 `cors`라는 정책 때문에 직접 불러올 수가 없습니다.
![cors error](https://i.imgur.com/Mxi1XfO.png)


만약 로컬파일을 코드 상에서 불러오고 싶다면 node.js 등을 활용해서 로컬 서버를 구성한 후 불러와야 됩니다.

하지만 사용자가 파일을 직접 불러오게끔 한다면 자바스크립트에서도 로컬파일을 불러와서 작업을 할수 있습니다.

먼저 html코드로 사용자가 파일을 불러와서 summit 할 수 있도록 구성해보았습니다.


# html 코드

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
label의 `for`에 input의 `id`를 넣어주어 같이 클릭 될 수 있게 했습니다.

파일을 불러오고나서 `summit` 버튼을 클릭하게되면 아래에 있는 `test()` 함수가 실행되게 됩니다.


# 2. 자바스크립트 코드
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
자바스크립트 코드는 불러온 txt파일을 콘솔창에 출력해주는 예제입니다.

***

먼저 첫번째 `event.preventDefault();` 코드는 summit을 할때 새로고침이 되는것을 방지해주는 메소드 입니다.

***

```javascript
let fileObject = document.getElementById("file");
let fileName = fileObject.files[0];
```
위 코드는 불러온 파일의 이름을 알아냅니다.

***

```javascript
let fr = new FileReader();
fr.readAsText(fileName, "utf-8");

fr.onload = () => {
    parseText(fr.result);
}
```
`readAsText()`를 이용하여 텍스트파일로 읽을수 있게 하고, `utf-8`을 인자로 줌으로써 한글이 깨지지 않도록 합니다.

그 후 `fr.onload()` 함수로 파일불러오는 것이 완료되면 `parseText()` 함수에 `fr.result` (파일의 내용) 를 넘겨주게 됩니다.

***

```javascript
function parseText(text) {
    console.log(text)
}
```
이제 이 함수 안에서 자유롭게 파일을 가공할 수 있습니다.

***
# 참고 링크
## [mdn javascript FileReader](https://developer.mozilla.org/ko/docs/Web/API/FileReader)
# 오버워치 캐릭터 선택화면

![image](https://user-images.githubusercontent.com/48821257/126022522-adc17ea3-f444-4870-b850-46cb2b4d76c4.png)

## SCSS를 이용하여 오버워치 캐릭터 선택화면을 만들기.

### prompt
> npm init -y
> npm i parcel-bundler -D

npm을 이용하여 parcel-bundler를 개발자 모드로 install 한다.

### [package.json]
``` json
// ...
"scripts": {
    "dev": "parcel index.html",
    "build": "parcel build index.html"
  },
// ...
```

scripts 부분을 위와 같이 수정.

### [main.scss]

``` scss
$url: "./images"; // 이미지의 위치를 변수로 저장

body {
  height: 100vh;
  background-image: url("#{$url}/bg.jpg"); // 변수 사용시 보간법을 이용하여 #{$변수명} 사용.
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

.container {
  padding: 50px 0;
  .heros { // SCSS에서는 중첩 가능
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 700px;
    margin: 0 auto; /* 요소의 가운데 정렬 */
    padding: 40px 20px;
    .hero {
      width: 80px;
      height: 84px;
      background-color: #555;
      margin: 4px;
      border-radius: 10px;
      box-sizing: border-box;
      border: 3px solid #fff;
      transform: skewX(-14deg);
      transition: transform .1s,
        background-color .6s;
      overflow: hidden;
      &:hover { // 상위 선택자를 선택 시 &를 사용
        background-color: #ff9c00;
        transform: scale(1.3) skewX(-14deg);
        z-index: 1;
      }
      .image {
        width: 140%;
        height: 100%;
        background-position: center;
        background-size: 90px;
        background-repeat: no-repeat;
        transform: skew(14deg) translateX(-16px);
      }
      // .hero
      @for $i from 1 through 32 { // for문 사용시 @for $변수명 from 초기값 through 마지막값으로 처리.
        &:nth-child(#{$i}) .image { background-image: url("#{$url}/hero#{$i}.png");} // 변수 사용시 보간법을 이용하여 #{$변수명} 사용. 
      }
    }
  }
  .logo {
    max-width: 300px;
    margin: 0 auto;
    padding: 0 20px;
    img {
      width: 100%;
    }
  }
}

```

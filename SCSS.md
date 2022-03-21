# SCSS
기존 CSS의 단점을 보완하기 위해 나온 문법. CSS 전처리기 라고도 부른다.  
SCSS 혹은 SASS가 CSS와 호환되려면 컴파일 과정을 거쳐야한다.  
SCSS가 어떤 형태로 CSS로 컴파일 되는지 확인할 수 있는 사이트를 첨부해둔다.  
[SASS Meister](https://www.sassmeister.com/)

## 변수
기존 CSS에서는 존재하지 않던, 변수 기능이 생겼다.
```SCSS
h1 {
  color: red;
} /* 기존 CSS */

-------------------
$color: red;
h1 {
  color: $color;
} // SCSS
```
이처럼 변수 기능이 생겨, 동일한 값을 가지는 속성들을 묶어서 관리할 수 있게 되었다.  
일반적인 다른 언어처럼 유효범위가 존재해 전역변수 혹은 지역번수를 설정할 수 있다.  
하지만 같은 중괄호 내에 있어도 재할당 후 하위에 존재하는 속성에 같은 변수를 사용할 경우 재할당 된 값으로 설정되므로, 순서나 재할당 등은 유의해서 사용해야 한다.

## 주석
기존의 CSS의 주석의 경우, `/* */ ` 형태의 주석블록 안에 작성을 하였다.  
그러나 SCSS의 경우, 자바스크립트와 동일하게 `//` 형태의 라인형 주석처리가 가능해졌다.  
이 둘은 차이가 있는데, 주석블록의 경우 컴파일 후에도 CSS 파일 내에 주석이 남아있고, 라인주석의 경우 컴파일 후에는 CSS 파일 내에 존재하지 않는다.

## 중첩(Nesting)
기본적인 CSS에서는 상위 선택자 뒷쪽에 하위 선택자를 붙이는 형태였다면, SCSS에서는 상위 선택자 내부의 요소처럼 하위 선택자를 다룰 수 있어 포함관계를 좀 더 직관적으로 볼 수 있고, 중복적으로 나오는 요소들을 줄여 효율적으로 코드를 작성할 수 있다.
```HTML
<div class="container">
  <ul>
    <li>
      <div class="name">Malade</div>
      <div class="age">85</div>
    </li>
  </ul>
</div>
```
```CSS
/* CSS */
.container ul li {
  font-size: 40px;
}

.container ul li .name {
  color: blue;
}

.container ul li .age {
  color: orange;
}
```

```SCSS
// SCSS
.container {
  ul {
    li {
      font-size: 40px;
      .name {
        color: blue;
      }
      .age {
        color: orange
      }
    }
  }
}
```

## 상위 선택자 참조(&)
`&` 기호를 사용, 상위 선택자의 일치선택자를 참조해 그 속성을 설정할 수 있게 해준다.
```HTML
<div class="btn">TEST btn</div>
<div class="btn active">TEST btn active</div>
```
```CSS
/* CSS */
.btn {
  font-size: 30px;
}
.btn.active {
  color: red;
}
```
```SCSS
// SCSS
.btn {
  font-size: 30px;
  &.active {
    color: red;
  }
}
```
일치선택자, 혹은 `hover` 등 상태변경을 나타내는 경우에도 사용할 수 있다.

## 중첩된 속성
한 요소의 속성들을 좀 더 직관적이고 보기 편하게 모아서 관리할 수 있다.
```CSS
/* CSS */
.box {
  font-weight: bold;
  font-size: 10px;
  font-family: sans-serif;
  margin-top: 10px;
  margin-left: 20px;
  padding-top: 10px;
  padding-bottom: 40px;
  padding-left: 20px;
  padding-right: 30px;
}
```
```SCSS
// SCSS
.box {
    font: { 
        weight: bold;
        size: 10px;
        family: sans-serif;
    };
    margin: {
        top: 10px;
        left: 20px;
    };
    padding: {
        top: 10px;
        bottom: 40px;
        left: 20px;
        right: 30px;
    };
}
```

## 연산
일반적인 다른 언어와 같이 연산(`+, -, *, /, %`) 기능을 지원한다.  
단, 나누기(/)의 경우 괄호 안에 넣어서 연산하거나 변수기능을 이용해서 연산을 해야한다.  
연산을 할 때 띄어쓰기가 꼭 들어가야 올바른 연산이 되는 듯?

## 재활용
SCSS에서는 기존 작성한 속성값들을 다시 재활용해 번거롭게 같은 코드를 반복작성할 필요 없도록 하는 기능을 제공한다.  
`@mixin`으로 사용하는데, 다른 언어에서의 함수 재활용처럼 생각하면 되는 듯 하다.
```CSS
/* CSS */
.container {
  display: center;
  justify-content: center;
  align-items: center;
}
.container .item {
  display: center;
  justify-content: center;
  align-items: center;
}
```
```SCSS
// SCSS
@mixin center {
    display: center;
    justify-content: center;
    align-items: center;
}

.container {
    @include center;
    .item {
        @include center;
    }
}
```

또한 다른 언어의 함수와 마찬가지로, 인수를 받아서 사용할 수 있다.
```SCSS
@mixin box($size) {
  width: $size;
  height: $size;
}

.container {
  @include box(200px);
  background-color: orange;
}
```
인수를 따로 지정하지 않아도 오류가 발생하지 않도록, 기본값을 초기화 시켜줄수도 있다.
```SCSS
@mixin box($size: 100px) {
  width: $size;
  height: $size;
}

.container {
  @include box;
  background-color: orange;
}
```
함수와 비슷하게 작동하기 때문에 인수를 여러개 받을 수도 있다.
```SCSS
@mixin box($size: 100px, $color: orange) {
  width: $size;
  height: $size;
  background-color: $color;
}

.container {
  @include box(200px, orange);
}
```
순서를 지키지 않고 사용할 경우 키워드 인수 방식을 사용할 수 있음.
```SCSS
@mixin box($size: 100px, $color: orange) {
  width: $size;
  height: $size;
  background-color: $color;
}

.container {
  @include box($color: orange);
}
```

## 반복문
SCSS에서는 다른 언어와 마찬가지로 반복문을 사용할 수 있다.
```SCSS
@for $i from 1 through 10 { // 제로베이스가 아님
  .box {
    width: 100px;
  }
}
```

하지만 무조건적으로 반복하는것은 좋은 방법은 아니므로, 이러한 방식으로도 사용한다.
```SCSS
@for $i from 1 through 10 {
  .box:nth-child(#{$i}) { // JS에서의 백틱기호 안에 인수를 넣는것과 비슷한 방식
    width: 100px;
  }
}
```

## 함수
위에서 봤던 코드 재활용의 @mixin 기능이 JS에서의 함수와 비슷했다면, 이번엔 실제로 함수 기능을 하는 코드가 있다.  
@mixin | @function
--|:--
리턴 없음 | 리턴 있음
사용 시 @include | 이름으로 호출
정해진 값 재활용 | 연산을 쉽게
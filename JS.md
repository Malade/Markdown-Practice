# typeof
자료형을 알려주는 키워드

ex) 
```JS
console.log(typeof 'Hello World!')
console.log(typeof 123)
console.log(typeof true)

// 출력결과
string
number
boolean
```

# Switch 문
조건문의 일종. 여러 조건이 필요한 경우에 사용할 수 있다.

ex) 
```JS
switch (a) {
  case 0:
    console.log('a is 0')
    break
  case 1:
    console.log('a is 1')
    break
  case 2:
    console.log('a is 2')
    break
  default:
  console.log('etc...')
}
```

한 조건의 결과설정 혹은 출력 이후에는 `break` 를 사용해 다른 결과가 중복되어 나오지 않도록 설정한다.  
`if`문의 `else` 조건의 설정같은 경우 `switch` 문에서는 `default` 조건으로 설정할 수 있다.

# 삼항연산자
조건이 `Boolean` 인 경우 사용한다.  
첫 항에 조건문이 들어가고, `참`일 경우 두번째 항을 실행, `거짓`일 경우 세번째 항을 실행한다.

ex)
```JS
const a = 1 < 2
// 조건 ? 참 : 거짓
print(a ? '참' : '거짓')

//result -- 참
```


# var, let, const

최근의 JS에서는 `var`라는 키워드를 사용하는 것이 권장되지 않는다고 한다.
이유가 무엇일까?  

`var`라는 키워드로 변수를 지정하게 되면, `block` 레벨에서의 유효범위가 아닌, `함수` 레벨에서의 유효범위를 갖게 된다고 한다.

ex)
```JS
function scope() {
  if (true) {
    const a = 123
  }
  console.log(a)
}

scope(a)

//결과 -- reference error
```

```JS
function scope() {
  if (true) {
    var a = 123
  }
  console.log(a)
}

scope(a)

//결과 -- 123
```

이처럼 `var` 키워드로 변수를 선언할 경우 함수 레벨의 유효범위를 갖기 때문에 더 많은 메모리를 차지하고, 메모리 누수로 이어진다.  


# Truthy, Falsy
`true`는 참, `false`는 거짓이다. 하지만 JavaScript 에서는 토씨 하나 달라질 경우 거짓이 참이 되고, 참이 거짓이 되는 경우가 있다.  
이러한 값들을 `Truthy(참 같은 값)` 와 `Falsy(거짓 같은 값)` 이라고 하는데, 그 종류들을 적어본다.

## Truthy
true, {}, [], 1, 2, `'false' (string)`, -12, '3.14' ...

## Falsy
false, '', null, undefined, 0, -0, NaN

# 즉시실행함수
익명의 함수를 실행해야 할 때나 만든 함수를 즉시 실행해야하는 경우 사용함.  

ex)
```JS
(function () {
  console.log(a * 2)
}) ()
```

만들어진 함수를 소괄호 내에 넣고, 그 뒤에 빈 소괄호를 붙임으로써 즉시실행함수가 완성된다.  
단, 그 전에 실행된 함수가 있다면 세미콜론으로 구분해야 오류가 나지 않는다.

ex)
```JS
const a = 7
function double() {
  console.log(a*2)
}

double()

(function () {
  console.log(a * 2)
}) ()

// 결과 -- TypeError

-----------------------------------

double();

(function () {
  console.log(a * 2)
}) ()

// 결과 -- 14  14
```

# 호이스팅(Hoisting)

`함수 선언부`가 유효범위 최상단으로 끌어올려지는 현상.  
함수 실행부 이후에 함수를 선언해도 함수가 정상작동 할 수 있도록 도와주는 기능.

ex)
```JS
// a = 7

double()

const double = function() {
  console.log(a*2)
}

// 결과 -- TypeError. double is not a function

-----------------------------------

double()

function() {
  console.log(a*2)
}

// 결과 -- 14
```

함수의 이름을 보고 로직을 추측할 수 있고, 비교적 코드 해석을 용이하게 하는 기능.

# 타이머 함수

## setTimeout()
일정 시간 후 함수 실행.  
`setTimeout(함수, 시간)` 의 방식으로 사용한다.

ex)
```JS
setTimeout(() => {
  console.log('Hello World!')
}, 3000) // 단위는 ms

// 3000ms 이후 Hello World! 출력
```

## setInterval()
시간 간격마다 함수 실행.  
`setInterval(함수, 시간)` 의 방식으로 사용한다.

ex)
```JS
setInterval(() => {
  console.log('Hello World!')
}, 3000) // 단위는 ms

// 3000ms 마다 Hello World! 출력
```

## clearTimeout()
설정된 Timeout 함수를 종료한다.

## clearInterval()
설정된 Interval 함수를 종료한다.


# 콜백(Callback)

함수의 인수로 사용되는 함수.  
어떤 이벤트가 발생했거나 특정 시점에 도달했을 때 시스템에서 호출하는 함수.  
문법적인 구분보다는, 호출방식에 의한 구분으로 볼 수 있다.   
[콜백함수 설명 블로그](https://www.hanumoka.net/2018/10/24/javascript-20181024-javascript-callback/)

ex)  
```JS
function timeout(callback) {
  setTimeout( () => {
    console.log('Hello World!')
    callback()
  }, 3000)
}

timeout( () => {
  console.log('Done!')
})
```

# this 
일반 함수는 호출 위치에 따라 this 정의  

화살표 함수는 자신이 선언된 함수 범위에서 this 정의

# forEach, map 차이

`map()` 메서드는 배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환합니다.

`forEach()` 메서드는 주어진 함수를 배열 요소 각각에 대해 실행합니다.

배열의 요소 각각에 대해 실행한다는 공통점이 있지만 반환을 하는지 함수 실행만 하는지에 대한 차이가 있습니다.

# 구조 분해 할당 (Destructing Assignment)

객체, 혹은 배열 데이터를 다시 할당해서 내부의 데이터를 꺼내어 쓸 수  있다. 
객체의 경우는 Key를 입력해 Value 를 꺼낼 수 있고, 배열은 인덱스에 따라서 꺼낼 수 있다.   
모든 데이터를 꺼낼 필요 없이, 필요한 데이터만 꺼낼 수 있다.

ex) 
```JS
const user = {
  name : 'Malade',
  age : 28,
  email : 'oxywriter@gmail.com'
}

console.log(`${name}`)
console.log(`${age}`)
console.log(`${email}`)

// 결과 --- Uncaught reference error
// name, age, email 이 undefined

-----------------------------------------------

const user = {
  name : 'Malade',
  age : 28,
  email : 'oxywriter@gmail.com'
}

const { name, age, email, address } = user

console.log(`${name}`)
console.log(`${age}`)
console.log(`${email}`)

// 결과 --- Malade
//          28
//          oxywriter@gmail.com
```


# 전개 연산자 (Spread)
배열의 데이터를 `전개`해서 출력한다.  

ex)
```JS
const fruits = ['Apple', 'Banana', 'Cherry']

console.log(fruits)
console.log(...fruits)

// 결과 --- ['Apple', 'Banana', 'Cherry']
//          Apple Banana Cherry

function toObject(a, b, c) {
  return {
    a: a,
    b: b,
    c: c
  }
}

console.log(toObject(...fruits))

// 결과 --- {a: 'Apple'
//           b: 'Banana'
//           c: 'Cherry}
```

# 데이터 불변성 (Immutability)
원시 데이터가 한번 만들어져 메모리에 할당된다면, 같은 값을 이용하는 데이터를 만들 때 새로운 메모리에 할당하는 것이 아닌 이미 할당되어있는 메모리에 있는 값을 이용한다.

`원시 데이터 : String, Number, Boolean, undefined, null`  

ex)
```JS
let a = 1
let b = 4
console.log(a, b, a === b)

// 결과 : 1 4 false

b = a
console.log(a, b, a === b)

// 결과 : 1 1 true

a = 7
console.log(a, b, a === b)

// 결과 : 7 1 false

let c = 1
console.log(b, c, b === c)

// 결과 : 1 1 true
```

위의 코드를 보면, 처음에는 a = 1 일 때와 b = 4 일때는 같지 않다. 하지만 b에 a의 값을 할당하면, a와 b의 값이 같기 때문에 참이 나온다기 보다는 같은 메모리 상의 데이터를 바라보기 때문에 참이 나온다.  
그리고 c에 1이란 값을 정해주면 새로운 메모리를 할당받는 것이 아닌, 이미 1이란 데이터가 들어있는 메모리를 바라보기 때문에 b와 동일한 메모리를 바라본다. 따라서 둘이 같은지 비교할 경우 참의 값을 가진다.

`참조형 데이터`의 경우, 한번 정해진 값에서 값을 변경하여도 같은 메모리 상에서 데이터가 변경되고 새로운 메모리가 할당되지 않는다.

`참조형 데이터 : Object, Array, Function`

ex) 
```JS
let a = { k : 1}
let b = { k : 1}
console.log(a, b, a === b)

//결과 : {k : 1}
//       {k : 1}
//       false

a.k = 7
b = a
console.log(a, b, a === b)

//결과 : {k : 7}
//       {k : 7}
//       true

a.k = 2
console.log(a, b, a === b)

//결과 : {k : 2}
//       {k : 2}
//       true

let c = b
console.log(a, b, c, a === c)

//결과 : {k : 2}
//       {k : 2}
//       {k : 2}
//       true


a.k = 9
console.log(a, b, c, a === c)

//결과 : {k : 9}
//       {k : 9}
//       {k : 9}
//       true
```

위에서 본 것과 같이, 한번 a를 참조한 b나 c는 a의 값이 바뀌어도 바뀐 값을 그대로 따라간다. 이는 같은 메모리를 참조하고 있기 때문이다.

# export
export 방식에는 두가지가 있다.  
하나는 `default` export 방식, 다른 하나는 `named` export 방식이다. 
`default` 방식의 경우 한 파일에서 한개의 데이터만 export 할 수 있다.  
`named` 방식의 경우 한 파일에서 여러개의 데이터를 내보낼 수 있다.

ex) 
```JS
export function random() {
  return Math.floor(Math.random() * 10)
}

export const user = {
  name : 'Malade',
  age : 28
}

// getRandom.js 에서 main.js로 export
```

```JS
import { random, user } from './getRandom'

console.log(random())
console.log(user)

// 결과 : 3
//        {name : 'Malade', age : 28}
```

<hr/>

```JS
export default function getType(data) {
  return Object.prototype.toString.call(data).slice(8, -1)
}

export default 123

// getType.js 에서 default 방식으로 export
```

```JS
import getType from './getType'

console.log(getType([1, 2, 3]))

// 결과 : ERROR - Only one default export allowed per module
```

이처럼, `named` export 방식의 경우 한 번에 여러개의 데이터를 export 할 수 있지만, `default` export의 경우 오직 하나의 데이터만을 내보낼 수 있음을 알 수 있다. 
단, `named` export 방식의 경우 import 할 때 가져오는 데이터를 `중괄호 {}` 안에 넣어줘야 한다.
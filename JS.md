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


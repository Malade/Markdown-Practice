# TypeScript
JavaScript에 Type 이라는 개념을 적용시킴  
JavaScript를 이해함으로써, 코드 실행 전 에러를 잡고 고치는데 쓰이는 시간을 절약시켜줌  
TypeScript는 `Compiled Language`,  
JavaScript는 `Interpreted Language`

Compiled | Interpreted
--|--
컴파일이 필요 O | 컴파일이 필요 X
컴파일러 필요 O | 컴파일러 필요 X
컴파일하는 시점 O (컴파일 타임) | 컴파일하는 시점 X
컴파일된 결과물을 실행 | 코드 자체를 실행
컴파일된 결과물을 실행하는 시점 | 코드를 실행하는 시점 O (= 런타임)

## Type Annotation
TypeScript가 JavaScript와 가장 차별되는 부분.  
특정 변수의 타입을 값 할당 없이도 따로 지정해줄 수 있다.  
Annotation의 경우 `a: type` 의 형태로 지정된다.

ex)
```TS
let a: string

a = 'Mark' // 오류 없음

a = 39 // 오류
```

## TS Types 와 JS Types

- TS  
`Static Type`. 개발중에 타입이 체크됨. 따라서 함수 사용 등의 경우 변수의 타입을 개발과정에서 체크, 오류를 미리 잡을 수 있음.

- JS  
`Dynamic Types`. 런타임중에 해석을 통해 타입이 체크됨. 별도의 타입오류 체크 과정이 들어가야 하기 때문에 개발과정이 상대적으로 번거로움

## TypeScript의 자료형들
TypeScript에서 프로그램 작성을 위해 기본 제공하는 데이터 타입들.  

- ECMAScript 표준에 따른 기본 자료형  
    - Boolean
    - Number
    - String
    - Null
    - Undefined
    - Symbol (ECMAScript 6 에 추가됨)
    - Array : Object 형

`사용자가 만든 타입은 결국 이 기본 자료형들로 쪼개진다.`
- 프로그래밍을 도울 몇가지 추가 타입
    - Any, Void, Never, Unknown
    - Enum
    - Tuple : Object 형

## Primitive Type
오브젝트와 레퍼런스 형태가 아닌 `실제 값`을 저장하는 자료형.  
Primitive Type의 내장 함수를 사용 가능한것은 자바스크립트의 처리 방식 덕분.
- 6가지
    - Boolean
    - Number
    - String
    - Symbol
    - Null
    - Undefined  

literal 값으로 Primitive Type의 서브 타입을 나타내거나, 또는 래퍼 객체 형태로 만들 수 있다.

ex)
```TS
// literal
true
'hello'
3.14
null
undefined

// wrapper object
new Boolean(false) // typeof new Boolean(false) : 'object'
new String('world') // typeof new String('world') : 'object'
new Number(42) // typeof new Number(42) : 'object'
```

## Type Casing
TypeScript의 핵심 Primitive Types 는 모두 소문자임.  
Number, String, Boolean, Symbol 또는 Object 유형은 소문자 버전과 동일하지 않음.  
대문자의 경우 `래퍼 객체` 를 만들때 사용하고, `타입을 나타내기 위해선 소문자만 사용해야 함.`


## Number / number
JS와 같이 TS의 모든 숫자는 부동 소수점 값.  
TS는 16진수 및 10진수 리터럴 외에도 ECMAScript 2015에 도입된 2진수 및 8진수를 지원함.  
NaN, 1_000_000 과 같은 표기도 가능하다.

ex)
```TS
let decimal: number = 10 // 10진수 리터럴
let hex: number = 0xff00 // 16진수 리터럴
let binary: number = 0b1010 // 2진수 리터럴
let octal: number = 0o7744 // 8진수 리터럴
let NotANumber: number = NaN
let underscoreNumber: number = 1_000_000
```

## string
다른 언어에서와 마찬가지로 텍스트 형식을 참조하기 위해 'string' 형식을 사용함.  
JS와 마찬가지로 문자열 데이터를 둘러싸기 위해 큰 따옴표(")나 작은 따옴표(')를 사용함.

## Template String
행에 걸쳐 있거나, 표현식을 넣을 수 있는 문자열.  
이 문자열은 백틱(\`) 기호에 둘러쌓여 있음.  
포함된 표현식의 경우 \`${expr}\` 와 같은 형태로 사용함.

ex)
```TS
let fullName: string = `Bob Bobbington`
let age: number = 38;

let sentence: string = `Hello, my name is ${fullName}.
I'll be ${age + 1} years old next month.`
// template string을 사용하지 않을 경우
let sentence: string = "Hello, my name is " + fullName + ".\n\n" + "I'll be " + (age + 1) + " years old next month."
```

## symbol
ECMAScript 2015의 Symbol.  
new Symbol 로 사용할 수 없음.  
Symbol을 함수로 사용해서 symbol 타입을 만들어낼 수 있음.  
프리미티브 타입의 값을 담아서 사용하며, 고유하고 수정 불가능한 값으로 만들어준다.  
주로 접근을 제어하는데 쓰는 경우가 많았음.
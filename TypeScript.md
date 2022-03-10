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

## Undefined & Null
TS에서 undefined와 null은 실제로 각각 undefined 및 null 이라는 타입을 가짐.  
void와 마찬가지로, 자체로는 유용하지않음.  
둘 다 소문자만 존재함

ex)
```TS
let a:undefined = undefined
let b:null = null
```

따로 TSconfig의 설정을 만지지 않는 이상, undefined와 null은 모든 다른타입의 서브타입이다. number에 null 또는 undefined를 할당할 수 있다는 의미임.  
하지만, 컴파일 옵션에서 `'--strictNullChecks'` 를 사용하면, null과 undefined는 void나 자기 자신들에게만 할당 가능함.  
이런 경우, null과 undefined를 할당할 수 있게 하려면 `union` 타입을 사용해야함

## null in JS
null 이라는 값으로 할당된 것을 null 이라고 함.  
무언가가 있지만 사용할 준비가 덜 된 상태.  
null 이라는 타입은 null 이라는 값만 가질 수 있음.  
런타임에서 typeof 연산자를 이용해서 알아내면, `object` 가 나옴

## undefined in JS
값을 할당하지 않은 변구는 undefined라는 값을 가짐.  
무언가가 아예 준비되지 않은 상태.  
object의 property가 없을 때도 undefined임.  
런타임에서 typeof 연산자를 통해 알아내면 `undefined`임


## union  
타입을 두가지 이상 가질 수 있게 할 때 쓰는 타입. 합집합이라고 보면 된다.

ex)
```TS
let a: string | null = null
```

## object
primitive type 이 아닌것 을 나타내고 싶을 때 사용하는 타입
- primitive type
    - number
    - string
    - boolean
    - bigint
    - symbol
    - null
    - undefined

## Array
원래 JS에서 array는 객체.  
TS에서 배열의 선언은 두가지 방법을 가질 수 있다.
```TS
let a: number[] = [1, 2, 3]
let b: Array<number> = [1, 2, 3]
```

두가지 타입을 동시에 가지는 배열을 선언할 때는, union 타입을 사용할 수 있다.
```TS
let a: (number | striing)[] = [1, 2, 3, 'Mark']
```

## Tuple
Array와 비슷하게 여러 타입을 동시에 갖는 배열을 선언할 수 있다.  
하지만, 선언한 타입의 순서와 배열의 길이를 정확히 지켜야한다.
```TS
let x: [string, number]
x = ['hello', 3] // 오류 없음
x = [3, 'hello'] // 오류, 선언한 타입은 맞으나 순서가 틀림
x[2] = 'hello' // 오류, 배열의 세번째 인자의 타입 지정하지 않아서 선언 불가. 확인해볼 시 세번째 인자는 undefined이기 때문에 undefined만 선언 가능
```

## any
어떤 타입이어도 상관없는 타입. 컴파일 타임에 타입 체크가 정상적으로 이뤄지지 않기 때문에, 최대한 쓰지 않는 것이 좋다.  
컴파일 옵션 중에는 any를 써야 하는데 쓰지 않으면 오류를 띄우는 옵션도 있다. 이것이 `noImplicitAny` 이다.
```TS
function returnAny(msg): any {
    console.log(msg)
}

returnAny('return any of type')
```
`any`는 계속해서 개체를 통해 전파되기 때문에, 모든 편의는 타입 안전성을 잃는 대가로 온다.  
타입 안전성이 TS를 사용하는 주요 동기 중 하나이기 때문에 필요치 않은 경우에는 any를 사용하지 않는것이 좋다.

```TS
function leakingAny(obj: any) {
  const a = obj.num // a의 타입이 any 가 됨
  const b = a + 1 // b의 타입이 any가 됨
  return b
}

const c = leakingAny({num : 0}) // c의 타입도 any
c.indexOf('0')
```
이처럼, any로 선언된 어떤 인자를 참조해서 다른 개체가 생성이 된다면 그 개체 또한 any가 된다. 함부로 사용해서는 `절대` 안된다.

## unknown
프로그램 작성 시 모르는 변수의 타입을 묘사해야 할 수 있음. 이러한 값은 동적 컨텐츠(예 : 사용자로부터, 혹은 API의 모든 값) 을 의도적으로 수락하길 원할 수 있음  
이 경우, 컴파일러와 코드를 읽을 사람에게 이 변수가 무엇이든 될 수 있음을 알려주는 타입을 제공해야 하기 때문에 `unknown` 타입을 사용함  
unknown 타입과 any 타입의 차이점이라고 한다면, any 타입은 다른 타입에 바로 할당이 가능하지만, unknown 타입은 타입체크를 한번 거쳐서 할당이 가능하다.

```TS
declare const unk1: unknown;
declare const any1: any

const aNumber: number = unk1 // 오류. unknown 형식은 number 형식에 할당할 수 없음.
const aString: string = any1 // 오류 없음. any는 어디에든 할당이 가능함.
if (unk1 === true) {
    const aBoolean: boolean = unk1 // 오류 없음. if문에서 unk1의 타입을 확인했기 때문에 boolean 타입인 aBoolean에 할당이 가능함.
}
```

TS 3.0 버전부터 지원되었으며, any보다 Type-safe 한 타입이다.  
any와 같이 아무 타입이나 할당할 수 있지만, 컴파일러가 타입을 추론할 수 있게끔 타입의 유형을 좁히거나 위의 예제와 같이 타입체크를 해서 타입을 확정해주지 않으면 다른 곳에 할당할수 없고 사용이 불가하다.  
사용 전에 데이터의 일부 유형의 검사를 수행해야 함을 알리는 API 등에 사용할 수 있을 것 같다.

## never
일반적으로는 return 등 에 사용되는 타입.  
모든 타입의 subtype 이며, 모든 타입에 할당 할 수 있음.  
하지만 never 에는 그 어떤 것도 할당이 불가능함.  
any조차 never에 할당할 수 없음.  
잘못된 타입을 넣는 실수를 막고자 할 때 사용됨. 

```TS
let a: string = 'hello'
if (typeof a !== 'string') {
    let b: never = a
}

type Indexable<T> = T extends string ? T &  { [index: string] : any } : never
```

## void
결과 값을 반환하지 않는 함수에 설정함.  
값을 반환하지 않는 함수의 경우 실제로는 undefined를 반환한다.

```TS
function returnVoid(msg: string): void {
    console.log(msg)
    return
}

const r = returnVoid('리턴이 없음')
// r의 타입은 void
```

## noImplicitAny
타입이 명시적으로 지정되지 않은 경우 컴파일러에서 타입을 any로 추론하게 되는데, 이 경우 `noImplicitAny` 옵션을 켜게 되면 컴파일 오류를 일으켜 타입을 명시적으로 지정하도록 유도한다.

## strictNullChecks
모든 타입에 자동으로 들어있는 null과 undefined를 제거해준다.  
함수 등의 리턴 값이 명시적으로 지정되지 않은 경우 함수가 정상작동하지 않았다면 리턴 값을 undefined로 추론하는데, 이런 경우를 막아준다.

## noImplicitReturns
함수 내에서 모든 코드가 값을 리턴하지 않으면, 컴파일 에러를 발생시킨다.

## 타입을 만드는 방법
TS에는 본인만의 타입을 만드는 몇가지 방법이 존재한다.
- interface
```TS
interface PersonInterface {
    name: string
    age: number
}
```

- type alias
```TS
type PersonTypeAlias = {
    name: string
    age: number
}
```
이 외에도 `class` 등을 사용 가능하다.

## structural type system
구조가 같으면, 같은 타입이다.

```TS
interface IPerson {
    name: string
    age: number
    speak(): string
}

type PersonType = {
    name: string
    age: number
    speak(): string
}

let personInterface: IPerson = {} as any
let personType: PersonType = {} as any

personInterface = personType
personType = personInterface
```
위의 예제는 structural type system의 예제로, `Iperson` 타입으로 선언된 `personInterface` 와 `PersonType` 으로 선언된 `personType`은 내부적인 구조가 같기 때문에, 서로를 할당해도 오류가 일어나지 않는다.

## nominal type system
구조가 같아도 이름이 다르면, 다른 타입이다
```TS
type PersonID = string & { readonly brand: unique symbol }

function PersonID(id: string): PersonID {
    return id as PersonID
}

function getPersonById(id: PersonID) {}

getPersonById(PErsonID('id-aaaaaa'))
getPErsonById('id-aaaaaa')
```
위의 예제는 사용할 수 있다는 예시이고,  
기본적으로 TS는 structural type system을 따른다. 

# Type Compatibility
같거나 서브 타입인 경우, 할당이 가능하다. 이를 `공변` 이라 한다.  

함수의 매계변수 타입만 같거나 슈퍼타입인 경우, 할당이 가능하다. 이를 `반병`이라 한다.

```TS
class Person {}
class Developer extends Person {
    coding() {}
}
class StartupDeveloper extends Developer {
    burning() {}
}

function tellme(f: (d: Developer) => Developer) {}

//Developer => Developer 에 Developer => Developer 를 할당하는 경우
tellme(function dToD(d: Developer): Developer {
    return new Developer()
})

// Developer => Developer 에 Person => Developer 를 할당하는 경우
tellme(function pToD(d: Person): Developer {
    return new Developer()
})

// Developer => Developer 에 StartupDeveloper => Developer 를 할당하는 경우
tellme(function sToD(d: StartupDeveloper): Developer {
    return new Developer()
})
```
`strictFunctionTypes` 옵션을 켜면, 함수 할당시 함수의 매개변수 타입이 같거나 슈퍼타입인 경우가 아닌 경우 에러를 통해 경고함.

## 타입 별칭(Type Alias)
Interface와 비슷함.  
Primitive, Union Type, Tuple, Function  
기타 직접 작성해야 하는 타입을 다른 이름으로 지정할 수 있음.  
만들어진 타입의 refer로 사용하는 것이지 타입을 새로 만드는것이 아니다.

```TS
type MystringType = string
const str = 'world'
let myStr: MyStringType = 'hello'
myStr = str
// 크게 의미 없는 Alias
```

### Aliasing Union Type
```TS
let perso: string | number = 0
person = 'Mark'
type StringOrNumber = string | number
let another: StringOrNumber = 0
another = 'Anna'

// 유니온 타입은 A도 B도 가능한 타입. 길게 쓸 것을 짧게 줄일 수 있어서 효율적
```

### Aliasing Tuple
```TS
let person: [string, number] = ['Mark', 35]
type PersonTuple = [string, number]
let another: PersonTuple = ['Anna', 24]

// 튜플에 별칭을 줘서 여러군데서 사용할 수 있도록 함
```

### Aliasing Function
```TS
type EatType = (food: string) => void
```

## include
컴파일할 파일 경로를 설정함(src 폴더 하위의 모든 .ts 확장자를 가진 파일)

## exclude
컴파일 대상을 제외하는 옵션

## @types
TS 2.0부터 사용 가능해진 내장 type definition 시스템.  
아무 설정을 안하면 `node_modules/@types` 라는 모든 경로를 찾아서 사용함.  
`typeRoots` 를 사용하면 배열 안의 모듈 혹은 `./node_modules/@types/` 안의 모듈 이름에서 찾아옴.  
[] 빈 배열을 넣는다는건 이 시스템을 이용하지 않겠다는 것.  
typeRoots와 types 를 같이 사용하지 않음.

## target 과 lib
- target
    - 빌드의 결과물을 어떤 버전으로 할 것인지 지정.  
    지정을 안하면 기본은 es3

- lib
    - 기본 type definition 라이브러리를 어떤 것을 사용할 것인지 지정.
    - lib 를 지정하지 않을 때
        - target이 'es3'이고, 디폴트로 lib.d.ts를 사용
        - target이 'es5'이면, 디폴트로 dom, es5, scripthost를 사용
        - target이 'es6'이면, 디폴트로 dom, es6, dom.iterable, scripthost를 사용
    - lib를 지정하면 그 lib 배열로만 라이브러리를 사용함.
        - 빈 배열 [] => 'no definition found'

## compile options
- rootDir
    - 시작하는 루트 폴더
- outDir 
    - 컴파일 후 생성되는 js 파일이 생성될 폴더명
- outFile
    - 단일파일로 출력시 파일명

## compile options - strict
모든 strict type checking 옵션을 사용하거나 사용하지 않을 수 있다.
- noImplicitAny  
    명시적으로 any라는 타입으로 지정하지 않았다면 오류를 발생시킴. any 타입으로 지정되지 않았다면 any가 아닌것.
    - suppressImplicitAnyIndexErrors  
        noImplicitAny를 사용할 때, 인덱스 객체에 인덱스 signature가 없는 경우 오류가 발생하는데 이를 예외처리함.
- noImplicitThis  
명시적이지 않게 any 타입을 사용하여 this 표현식에 사용하면 오류를 발생시킴.  
첫번째 매개변수 자리에 this를 놓고, this 에 대한 타입을 어떤 것이라도 표현하지 않으면 noImplicitAny가 오류를 발생시킴
```TS
function noImplicitThisFunc(this, name: string, age: number) {  // this 의 타입이 지정되지 않아 error
    this.name = name
    this.age = age

    return this 
}
```
JS에서는 매개변수에 this 를 넣을 경우 이미 예약된 키워드라 SyntaxError를 일으킨다.  
Class 에서 constructor 를 제외한 멤버 함수의 첫번째 매개변수도 일반 함수와 마찬가지로 this를 사용할 수 있음

- strictNullChecks  
null 및 undefined 값이 모든 유형의 도메인에 속하지 않으며, 그 자신을 타입으로 가지거나 any 일 경우에만 할당이 가능.  
예외로 undefined에는 void를 할당 가능  
null과 undefined 값을 가지기 위해서는 union type을 이용해 직접 명시해야함

- strictFunctionTypes


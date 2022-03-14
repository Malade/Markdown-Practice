# Interface
기존에 존재하는 타입들을 모아 한번에 여러 가지 타입을 갖는 새로운 타입을 정의하는 것과 유사함.
```TS
// interface를 쓰지 않은 코드
function p1({name: string, age: number}): void {
  console.log(`이름은 ${p1.name}, 나이는 ${p1.age}`)
}

const p2({name:string, age: number}) = {
  name: 'Mark'
  age: 39
}
```

```TS
// interface를 쓴 코드
interface Person1  {
  name: string
  age: number
}

function hello1(person: Person1): void{
  console.log(`안녕하세요 ${person.name} 입니다.`)
}

const p1: Person1 = {
  name: 'Mark',
  age: 39,
}
```

interface로 인해서 복잡하게 인자의 타입을 반복해서 쓸 필요가 없다.


## interface 상속
```TS
interface IPerson2 {
  name: string
  age?: number
}

interface IKorean extends IPerson2 {
  city: string
}

const k: IKorean = {
  name: 'Mark',
  city: 'Seoul',
  age: 39
}
```

## interface를 class 로 확장
```TS
interface IPerson1 {
  name: string,
  age?: number,
  hello(): void
}

class Person implements IPerson1 {
  name: string;
  age?: number | undefined;

  constructor(name: string) {
    this.name = name
  }

  hello(): void {
    console.log(`안녕하세요! ${this.name} 입니다.`)
  }

}

const person: IPerson1 = new Person('Mark')
```


## Declaration Merging
같은 이름의 interface를 여러개 만들 경우, 나중에 사용할 때 같은 이름을 가진 interface들은 동일한 것으로 간주된다. 이는 type alias 에서는 불가능하고, interface 에서만 가능하다.
```TS
interface Merging {
  a: string
}

interface Merging {
  b: string
}

let me: Merging;
me.a = 'Hello' // 사용 가능
me.b = 'World' // 사용 가능 
```
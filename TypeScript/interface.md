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

# 공변과 반공변
잘 이해가 가지 않는 항목이기 때문에, 따로 문서를 만들기로 했다.  
참고 링크와 함께 공부를 해보면 좋을 것 같다.  
[공변과 반공변](https://iamssen.medium.com/typescript-%EC%97%90%EC%84%9C%EC%9D%98-%EA%B3%B5%EB%B3%80%EC%84%B1%EA%B3%BC-%EB%B0%98%EA%B3%B5%EB%B3%80%EC%84%B1-strictfunctiontypes-a82400e67f2)

## 간결한 예시
- 공변성
  - A->B 일때 T\<A> -> T\<B> 인 경우
- 반공변성
  - A->B 일때 T\<B> -> T\<A> 인 경우


우선은 이것들을 설명하기 위해선 Type 과 Sub tpye 의 관계를 알아야 한다.
`Dog`타입과 `Animal` 타입이 존재하고, `Dog`가 `Animal`의 서브타입이라고 하자.
```Ts
interface Animal {
  id: number
}

interface Dog extends Animal {
  name: string
}
```
이 경우, `Dog` 가 `Animal`을 확장했기 때문에, 
```TS
declare let animal: Animal
declare let dog: Dog

animal = dog
```
는 아무 문제없이 성립된다.
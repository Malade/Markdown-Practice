# Class
- object를 만드는 설계도.  
- class 이전에 object를 만드는 기본적인 방법은 function 이 있다.  
- JS에서도 class는 ES6 부터 가능하다.  
- OOP를 위한 초석.  
- TS에서는 class도 사용자가 만드는 타입의 하나이다.  
- class 키워드를 이용해 클래스를 만들 수 있다.  
- class 이름은 보통 `대문자`를 이용함.  
- new를 이용해 class를 통해 object를 만들 수 있음.  
- constructor를 통해 object를 생성하며 값을 전달할 수 있음(초기화)  
- this를 이용해 만들어진 object를 가리킬 수 있음.  
- JS로 컴파일 될 때, es5의 경우는 function으로 변경된다. 이는 JS에서 es6가 되어야 class를 지원하기 때문이다.  
- 생성자 함수가 없으면, 디폴트 생성자로 불린다. 단, 프로그래머가 만든 생성자가 하나라도 있다면 디폴트 생성자는 사라진다.
- strict 모드에서는 프로퍼티를 선언하는 곳 또는 생성자에게 값을 할당해야 한다.
- 프로퍼티를 선언하는 곳 또는 생성자에서 값을 할당하지 않는 경우에는 !를 붙여서 위험을 표현한다. 
- 클래스의 프로퍼티가 정의되어 있지만, 값을 대입하지 않으면 undefined 이다.
- 생성자에는 async를 설정할 수 없다. 

## 접근 제어자 (Access Modifiers)
`public` 과 `private`, 그리고 `protected`.  
외부에서 class 내부의 요소에 접근할 수 있는지 없는지 설정할 수 있다.  
클래스 내부의 모든 요소(생성자, 프로퍼티, 메소드)에 설정 가능하다.
### public
디폴트 설정값. 따로 지정하지 않을 경우에도 public 이다. 어디서든 접근할 수 있음.
### private
클래스 외부에서 접근할 수 없게 하는 기능.  
JS에서 private을 지원하지 않아 묵시적으로 프로퍼티나 메소드 이름 앞에 `_`를 붙여서 표현했다.

## 추상
추상 클래스를 정의할 때는 class 앞에 `abstract` 를 표기함. 추상 메서드도 동일.  
추상 메서드는 정의만 있을 뿐 몸체(body)가 구현되어 있지 않음. 추상 클래스를 상속하는 클래스에서 해당 추상 메서드를 필히 구현.  
추상 클래스 내에서 실제 메서드도 구현할 수 있다.
```TS
// 추상 클래스
abstract class Project {

  public project_name:string|null = null;
  private budget:number = 2000000000; // 예산

  // 추상 메서드 정의
  public abstract changeProjectName(name:string): void;

  // 실제 메서드 정의
  public calcBudget(): number {
    return this.budget * 2;
  }

}

// [오류]
// [ts] 추상 클래스의 인스턴스를 만들 수 없습니다.
// constructor Project(): Project
let new_project = new Project();
```
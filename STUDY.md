# 유의적 버전

## Major.Minor.Patch

## `12`.14.1  (`Major`.Minor.Patch)
맨 앞 숫자는 Major 버전을 뜻함.  
기존 버전과 호환되지 않음

## 12.`14`.1 (Major.`Minor`.Patch)

Minor 버전을 의미함.  
기존 버전과 호환되는 새로운 기능이 추가된 버전을 의미.

## 12.14.`1` (Major.Minor.`Patch`)

Patch 버전을 의미함.  
기존 버전과 호환되는 버그 및 오타 등이 수정된 버전

## `^`12.14.1 (`^`Major.Minor.Patch)
Major 버전 안에서 가장 최신 버전으로 업데이트 가능  
캐럿 기호가 붙어있을 경우 update 명령어를 통해 Major 버전 내의 최신 버전으로 업데이트가 가능하지만,  
붙어있지 않을 경우 업데이트 없이 명시된 버전만을 사용한다는 뜻

---

# .gitignore
git을 사용할 때 버전관리를 원하지 않는 폴더나 파일 등을 명시적으로 표시할 수 있음.  
.gitignore 파일 내에 한 줄에 하나씩 무시할 폴더 혹은 파일을 적으면 됨

ex)
```md
images/
README.md
test.txt
```


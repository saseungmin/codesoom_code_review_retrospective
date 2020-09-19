## 🚀 1주차
### 🤔 참고사항
- [Object.entries()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
- [ikaruce/git-style-guide](https://github.com/ikaruce/git-style-guide) 
- [좋은 git 커밋 메시지를 작성하기 위한 8가지 약속](https://djkeh.github.io/articles/How-to-write-a-git-commit-message-kor/)
- [Commit Message Style Guide For Git](https://commit.style/)
- `git commit` 에디터는 vi 에디터를 기본적으로 쓴다.
  - 주의) `git commit -m "message"` 는 쓰지 않는다. `-m`은 anti pattern이다.
- [Vi 에디터를 이용한 커밋 메시지 작성 방법](https://cau-dosc.github.io/how-to-write-commit-messages-using-vi.html)
- [Taeung/git-training](https://github.com/Taeung/git-training)
### 📚 과제 1 - let을 제거해보자 코드 리뷰
- 코드의 맥락이 달라진 부분은 한 줄 띄어준다.
- 각 기능 별로 핸들러 함수를 구현한다.

### 📚 과제 2 - 간단한 사칙 연산 계산기 구현
```javascript
const numberList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]; // ❌
// 변경
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]; // ⭕
```
- 위처럼 컬렉션을 사용할 땐 자료구조의 종류를 변수 이름에 표현하는 걸 권하지 않는다.
만약 다른 자료구조로 교체한다면 저 List라는 단어는 어떻게 될까요?

```javascirpt
frontNum: '',
backNum: '',
// 사실 리팩토링하면서 frontNum은 필요가 없었다.
```
- `Num`과 같이 축약하지 않는 게 좋다.
- 그리고 `front`와 `back`의 의미가 모호하다.

```
...
    } else {
      render({
        ...props,
        func: operator,
      });
    }
...
```
- **`else`는 절대 쓰지말자!!!**
- else is evil입니다.

```
'+': (frontOperand, backOperand) => frontOperand + backOperand,
'-': (frontOperand, backOperand) => frontOperand - backOperand,
'*': (frontOperand, backOperand) => frontOperand * backOperand,
'/': (frontOperand, backOperand) => frontOperand / backOperand,
```
- 여기서는 구분에 전혀 지장이 없기 때문에 아래와 같이 변경
```javascript
const initialState = {
  ...
  operatorFunc: {
    '+': (x, y) => x + y,
    '-': (x, y) => x - y,
    '*': (x, y) => x * y,
    '/': (x, y) => x / y,
  },
};
```
- 상태와 상태아닌것에 대한 구분은 명확하게 한다.
- 굳이 상태를 관리하지 않는 그저 화면에 표현하기 위해 사용하는 것들은 상태로 관리하지 않는다.



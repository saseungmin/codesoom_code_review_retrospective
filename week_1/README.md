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


### 🌈 1주차 회고

- 주변 지인분의 추천으로 코드숨 2기를 신청을 고민하게 되었고 가격도 만만치 않은 금액이었지만 TDD와 코드리뷰를 해주는 커리큘럼에 신청하게 되었다.
- 이제 1주차를 끝냈지만, 굉장히 만족스럽다. 일단 온라인으로 각자 원하는 시간에 자유롭게 기간 내에 하는 것은 직장이 있는 분들한테도 부담 없이 할 수 있는 것 같다. 
- `-m`에 대해서 별다른 생각하지 않았는데 git 커밋 메시지를 작성할 때 `git commit -m "message"`는 `anti pattern`점을 다시 알게 되었다.
- 커밋 메시지를 작성할 때도 생각 없이 메시지를 작성했지만 주신 링크를 보면서 커밋 메시지의 중요성을 다시 한 번 깨달았고 message-style에 맞춰가고 커밋 메시지 약속을 지켜가며 좋은 메시지를 적는 습관을 만들어야겠다.😤
- `else`는 절대 쓰지 말자!
- 기능별로 핸들러 함수를 구현하고 그 함수는 하나의 일만 하는 함수로 만드는 것이 좋다는 점!
- 변수 네이밍을 할 때 어떻게 지을까라고 생각을 하고 짓긴 하였지만, 여전히 깊게 고민은 하지 않았던 거 같다. 귀찮다고 생각하지 말고 변수명을 지을 때 *얘는 뭐하는 애지?? 그러면 이름을 어떻게 지어야 할까?* 라는 고민을 많이 하여 짓는 습관을 지녀야겠다.
- `pull request`를 제대로 써본 것은 이번이 처음이라 익숙지 않았지만, 점점 나아지는 것 같다.
- 상태로 관리해야 할 것과 상태가 아닌 것에 대해서 구분을 명확하게 해야 할 필요성을 많이 느꼈다. 
- 1주차를 마무리하면서 느낀 점은 트레이너? 분들께서 코드리뷰를 정말 집요하게 잘해주시는 것 같다. 12주차 동안 많이 배워갈 수 있다는 기대감이 생겼다! 🚀
- 이번 주의 나보다 다음 주의 더 나은 내가 되길 바라며 12주 뒤엔 코드숨에서 배운 좋은 습관과 지금보다 발전한 나를 보며 성취감을 얻게 됐으면 좋겠다.
- 과제를 해결해 나가고 배우면서 이건 왜 할까? 를 고민해야겠다. 지금까지 아무 생각 없이 풀어나갔던 거 같다. 코드리뷰를 받고 풀어나가면서 굳이 필요 없었던 코드들을 확인할 수 있었고 풀어나가는 과정에서 고민하고 고민하는 자세를 갖는 습관을 지녀야겠다.
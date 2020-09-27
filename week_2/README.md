## 🚀 2주차 회고

### 📚 과제 1 - Counter 앱 만들고 파일 분리하기
- 리액트 라이브러리 임포트와 컴포넌트 임포트를 구분해줘야 한다는 생각을 해본적이 없던거 같다.
확실히 임포트 간의 구분을 해주니 컴포넌트 임포트를 명확하게 보여줄 수 있는 거 같아 좋은 방법같다!!
앞으로 임포트를 할 때도 신경을 써야하는 부분이다! 🤔
```javascript
// 변경 전
import React, { useState } from 'react';
import ReactDOM from 'react-dom';
import Page from './components/Page';

// 변경 후
import React, { useState } from 'react';
import ReactDOM from 'react-dom';

import Page from './components/Page';
```

- 화면에 보여주는 역할을 하는 컴포넌트는 그 역할만 하고 어떤 일을 할지는 컴포넌트를 사용하는 입장에서 결정할 수 있게 분리를 해주는 것이 좋다라는 것을 배웠다.
이런 세세한 부분에서 좀 더 집중해서 코드를 봐야할 거 같다.
```jsx
// 변경 전
<button type="button" onClick={() => onClick(number)}>
    {number}
</button>
// 변경 후
<button type="button" onClick={onClick}>
    {number}	     
</button>	   
```

### 📚 과제 2 - 간단한 Todo App 만들기
- 조건문에는 **부정문보단 긍정문으로!!**
아래는 `todos.length`가 존재하지 않으면으로 조건문이 되는데 존재하면! 이라는 말로 변경을 하자.
삼항 연산자의 로직을 밖으로 빼줘서 `arr.length`가 존재할 때 배열의 마지막 인덱스의 `id`를 `last`라는 함수로 만들어 `id`에 `+1`을 해준다는 의도를 명확하게 들어낼 수 있었다.
- 이 과정에서 [null 병합 연산자](https://ko.javascript.info/nullish-coalescing-operator)를 처음 알았다. 
```javascript
// 변경 전
const todo = {
    id: !todos.length ? 1 : todos[todos.length - 1].id + 1,
    item,
}
// 변경 후 1
const item = {
    id: todos.length ? todos[todos.length - 1].id + 1 : 1,
    value,
}
// 변경 후 2
const last = (arr) => arr.length && arr[arr.length - 1].id;

const item = {
  id: last(todos) + 1,
  value,
};
```
- 함수명을 지을 때 `on`을 붙는 경우와 `handle`이 붙는 경우에 대해서도 이번 기회에 확실히 개념은 잡은거 같다! 항상 신경쓰자.🙏
실제로 일을 처리하는 함수는 `handle`을 붙어주고 실제로 사용하는 입장에서 바라볼때는 `on`을 붙는 것.
예를 들어 `TodoInsert` 컴포넌트에서 `submit`을 했을 때 그 `submit` 함수를 다루는 경우는 `handleSubmit`이라는 이름을 사용하고, 만약 `TodoInsert`에서 `handleSubmit`을 받을 때는 `on`이 붙는 `onSubmit`을 사용한다.

- 이벤트 객체를 다루는 함수는 UI컴포넌트 그 자체에서 관리를 해야한다! 이거 또한 생각하지 못했다.. 알고나서 내가 얼마나 생각 없이 코딩을 했는지..😢
상태를 변경해주는 함수는 UI 레이어와 상관이 없어야 한다.
```javascript
const handleOnChange = (e) => {
    change(e.target.value);
};
```
- [`Guard Clauses`](https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html) 사용하자 사용하자 사용하자
의도를 명확하게 하자 하자 하자
확실히 삼항 연산자로 구분을 할 때보다 하고자하는 의도를 명확하게 보일 수 있는 거 같다..
```jsx
// 변경 전
function TodoList({ todos, onRemove }) {
  return (
    <div>
      {todos.length ? todos.map((value, index) => (
        <TodoItem
          key={value.id}
          todo={value.item}
          count={index}
          onRemove={() => onRemove(value.id)}
        />
      )) : (<div>할 일이 없어요!</div>)}
    </div>
  );
}
// 변경 후
const isEmpty = (arr) => arr.length === 0;

function TodoList({ todos, onRemove }) {
  if (isEmpty(todos)) {
    return <p>할 일이 없어요!</p>;
  }

  return (
    <div>
      {todos.map((value, index) => (
        <TodoItem
          key={value.id}
          todo={value.item}
          count={index}
          onRemove={() => onRemove(value.id)}
        />
      ))}
    </div>
  );
}
```

### 📚 느낀점
- 2주차가 끝났고 1주차에 느꼈던 것들을 잘 실천했을까??
`commit message` 작성은 vi 에디터를 사용한 작성을 했고, message-style에 맞춰서 작성을 노력하고 있다. 
`else`는 사용하지 않았다! 계속 생각하며 기피하자!
변수이름은 잘 지었을까?? 🤔 이거는 좀 더 훈련이 필요한 부분 같다..
이번 주는 저번 주와 다르게 좀 더 빠르고 많은 코드리뷰를 받기 위해 과제 `pull request`를 빠르게 하였다! 확실히 많은 코드 리뷰를 받을 수 있었고, 처음 작성했을 때와 비교했을 때 많이 달라진 코드를 확인할 수 있었다.👍 
다행히 1주차보단 확실히 나은 **'나'** 는 된 거 같다.
- 2주차의 과제를 수행하며 나의 잘못된 코딩 습관을 알 수 있었다.. 그에 따라 한 번 더 생각하게 되었다. *지금 나는 이렇게 생각하여 풀려고 하는데 이게 좋은 방법 맞아??*  나에게 되묻는게 점점 많아지고 있다. 
시간은 좀 오래 걸리지만 리펙토링하는 작업이 생각보다 즐겁다!!
역시..난 코딩이 즐겁다..✌
- 이번 주에 받은 코드리뷰를 바탕으로 3주차의 과제에도 생각하며 좋은 코딩 습관을 적용해보자! 😤
-  다음 주도 화이팅하자! 🚀
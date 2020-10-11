## 🚀 3주차 회고 및 코드리뷰 정리
- 저번주는 추석으로 인하여 한 주 쉬고 이번주부터 다시 시작하게 되었다. 😤
- 3주차인 이번주는 2주차때 작성한 To-do의 테스트를 작성해보는 것이였다!
  
### 📚 Testing??
- 테스트?? 흠.. 테스트는 해본적이 없었고, 최근에 우아한 테크러닝에서 들었던 [testing library](https://testing-library.com/) 에 대한 간단한 설명이 전부였다..
- 이번주는 쉽지 않을 거 같은 예상.. 역시.. 처음 부딪혀본 결과, 많이 고통스러웠다.🤔
- 역시 배울게 너무나도 많은 거 같다..
- 이번주는 자바스크립트 테스팅 프레임워크인 [Jest](https://jestjs.io/)에 대해서 알 수 있었고, 리액트 테스팅 라이브러리도 공부할 수 있었던 과제였던 거 같다.

### ✌ 이번주에 받은 코드리뷰를 바탕으로 배운 것들은?
- 테스트도 유지보수해야하는 코드로서 생각하며 구현하자.
- `setup` 함수에 모두 모아서 `props`로 받아 `render`를 해줬었는데 생각보다 많이 복잡했졌던거 같았다.

```javascript
// 변경 전
const setup = ({ handleChange = jest.fn(), handleClick = jest.fn() }) => {
  const utils = render(<Input onClick={handleClick} onChange={handleChange} />);
  const { getByLabelText, getByText } = utils;
  const input = getByLabelText('할 일');
  const button = getByText('추가');
  const taskTitle = '아무것도 하지 않기';

  return {
    ...utils,
    input,
    button,
    taskTitle,
  };
};
```
- `handleChange`, `handleClick` 도 최초 한번만 선언할 수 있게 되었다.

```javascript
// 변경 후
const handleChange = jest.fn();
const handleClick = jest.fn();
const inputLabel = '할 일';

const renderInput = (value) => render((
  <Input
    value={value}
    onClick={handleClick}
    onChange={handleChange}
  />
));
```

- `describe-context-it` 구조로 `Given, When, Then`에 맞춰서 표현해주는 것! 테스트가 명확하게 뭘하는지 알 수 있다! ([참고1](https://ko.javascript.info/testing-mocha), [참고2](https://www.betterspecs.org/#contexts))

```javascript
describe('List', () => {
  context('tasks의 값이 없을 때', () => {
    // Given
    const tasks = [];

    it('"할 일이 없어요!"를 표시한다.', () => {
      // When
      const { container } = render(<ListComponent />);

      // Then
      expect(container).toHaveTextContent('할 일이 없어요!');
    });
  });
});
```

- `context` 안에는 `with, without, when`만 사용하면 어떤 테스트를 하려는지 명확하게 의도가 전달된다!
- 처음에 잘 이해가 안갔지만, 코드리뷰를 통해서 알게 되었다..ㅎ😅
- **의도 전달이 중요하다!**
- 어떤 것이 있을 때, 없을 때를 구분해서 테스트를 구분하니 확실히 알아보기 쉬운거 같다.

```javascript
context('with tasks', () => {
  it('renders tasks', () => {
  // ~~ 생략 ~~
  });
});
context('without tasks', () => {
  it('"할 일이 없어요!" 를 표시', () => {
  // ~~ 생략 ~~ 
  });
});
```

- `handleClickAddTask`의 `mocking` 함수가 상단에 선언을 해주었었고, Page test에서 두번을 사용하게 되었었다.
- 이 상황에서 각 테스트에서 `expect(handleClickAddTask).not.toBeCalled();`를 하니 두 번째 테스트 에서 아래와 같은 에러가 발생하였었다.

```
expect(jest.fn()).not.toBeCalled()

Expected number of calls: 0
Received number of calls: 1
```
- 이 상황이 나타나는 이유는 각 테스트마다 독립적이지 못하고 첫번째 테스트에 영향을 받게 되어서 이미 호출된 건수가 1개가 존재했던 것이였다.
- 이런 문제를 해결하기 위해서 `clean up`을 해준는 함수 중 하나가 [mockClear](https://jestjs.io/docs/en/mock-function-api#mockfnmockclear)였다.
- 그래서 각 테스트 별로 의존성을 없애고 독립적으로 실행되게 만들기 위해서 `beforeEach` 와 [`jest.clearAllMocks()`](https://jestjs.io/docs/en/jest-object#jestclearallmocks)를 사용해주는 방법을 알았다.
- **각 테스트는 독립적으로 실행되어야 한다.**

```javascript
beforeEach(() => {
  jest.clearAllMocks();
});
```

### 😢 그래서 느낀 점은?
- 처음 접해보는 테스팅 과제임에도 불구하고 생각보다 시간 투자를 못했던거 같다.
- 좀 더 많이 고민해보고 많이 수정해보면서 뼈에 와닿을 정도로 느껴봤어야 했는데 부족했다는 생각을 받았다.
- 추가적으로 값이 여러 개로 주어질 때에 대해서도 테스트 코드를 작성을 못 해봤던거 같다.
- 과제 풀이를 보면서 다시 한 번 되집는 시간을 가져야겠다.
- 퇴근 후 매일같이 코드숨 뿐만 아니라 공부를 하고 있지만, 시간적인 여유가 없는 건지 내가 소홀해진건지 모르겠다..
- 물론 여전히 공부하고 풀어나가고 배워가는 건 너무나도 재밌다.
- 프론트 앤드 공부를 시작하면서 처음 목표로 잡았었던 *지치지말고 꾸준히*라는 건 아직까진 잘 지켜지고 있는 거 같다.
- 코드숨을 잘 마무리 지을 수 있을까..? 있어야 한다. 😤
- 4주차는 또 어떤 과제가 기다리고 있을까?? 기대가 된다. ㅎㅎ 😅


#### 📌 3주차 받은 코드리뷰

![3주차](../img/3주차.png)
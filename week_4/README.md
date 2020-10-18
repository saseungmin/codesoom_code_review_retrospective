## 🚀 4주차 회고 및 코드리뷰 정리

- 이번주의 첫 번째 과제는 저번주에 이어서 TDD를 통해 Todo App을 redux를 사용하여 수정하는 것이였다.
- 다행이도 첫번째과제는 아샬님 영상이 있어서 도움이 많이 되었다.
- 두 번째 과제는 첫 번째 과제를 바탕으로 레스토랑의 정보를 입력?하는 그런 간단한 시스템을 TDD로 만드는 것이였다.
- TDD에 대해서는 낯선감이 있었지만, `redux`는 `react`를 공부를 했던 터라 조금이나마 반가웠다.

### ✌ 이번주에 받은 코드리뷰를 바탕으로 배운 것들은?
- 테스트의 내용을 작성할 때 실제로 **어떤 일이 일어나는지, 어떤 변화가 일어나는지**를 기술하자. 

```javascript
// 변경 전
it('버튼 클릭시 호출되는지 확인한다.', () => {
  // ...
});

// 변경 전
it('버튼을 클릭하면 onClick 핸들러가 실행된다.', () => {
  // ...
});
```
- 여러 개를 나타내는 건 복수로 나타내자. 이건 알고 있었지만, 너무 무심했던거 같다. 생각을 못했다..😢
- 변수를 복수를 사용하면 변수 이름만 봐도 여러개를 나타낸다는 것을 알 수 있게 되어서 의도를 쉽게 드러낼 수 있다.
```javascript
// 변경 전
const inputType = [
  { placeholderName: '이름', inputName: 'name' },
  { placeholderName: '분류', inputName: 'category' },
  { placeholderName: '주소', inputName: 'address' },
];
// 변경 후
const inputTypes = [
  { placeholderName: '이름', inputName: 'name' },
  { placeholderName: '분류', inputName: 'category' },
  { placeholderName: '주소', inputName: 'address' },
];
```
- 아무것도 출력하고 싶지 않았을 때 테스트를 확인하는 방법.
- `toBeEmpty`는 더 이상 사용되지 않는다.
- 그렇기 때문에 `toBeEmptyDOMElement`를 사용한다.

```javascript
const { container } = listRender(restaurants);

expect(container).toBeEmptyDOMElement();
```
- 테스트에서 사용되는 데이터들이 반복해서 사용되는 것들은 테스트용 데이터를 미리 만들어놓고 사용하여 중복을 줄일 수 있고, 테스트의 복잡성을 낮출 수 있다!
- 이러한 테스트용 데이터를 `fixture`라고 부른다.
- 하지만 **테스트용 데이터와 테스트를 검증하는데 사용되는 것과 구분을 해줘야 한다.** 둘은 다른 일이다.
- 그렇기 때문에 검증하는 데 필요한 것들은 눈에 보여야 이해하기가 쉬워진다!! 📚

```javascript
// 변경 전
inputTypes.forEach((placeholder) => {
  expect(getByPlaceholderText(placeholder)).not.toBeNull();
});

// 변경 후
['이름', '분류', '주소'].forEach((placeholder) => {
  expect(getByPlaceholderText(placeholder)).not.toBeNull();
});
```
- 과도한 추상화는 테스트를 이해하는지 어렵다.
```javascript
// 변경 후
fireEvent.change(getByPlaceholderText('이름'), { 
  target: { value: '시카고 피자' }
});

expect(handleChange).toBeCalled();
```

### 😢 그래서 느낀 점은?
- TDD로 기능 구현하는 것은 생각할 것이 너무 많았고, 시간과 생각의 고통이 생각보다 컸다. 😢
- 이번 과제는 TDD Cycle에 맞춰서 구현하느라 커밋만 70개 정도 됐다. TDD Cycle에 맞게 잘 한지는 잘 모르겠지만, 계속 해보며 고통을 느끼고 방법을 찾아간다는 느낌을 받는걸 보니까 맞게 하고 있는거 같다.
- 만약 TDD로 구현하지 않고 react와 reduc로만 구현했다면 쉽게 할 수 있던 과제였겠지만, 그만큼 얻어가는 것도 적었을 것이다.
- 과제를 수행하는데에 있어서 점점 시간이 부족해진다는 느낌을 받고 있다. 그래서 이번주는 굉장히 늦게 마무리를 지었다..😢 코드리뷰를 받기위해 최대한 빠르게 하려고했고, 저번주보다 더 많은 시간을 투자했지만 더 늦게 해버렸다. 
- 앞으로 시간 투자를 더 많이 해야할 과제들일텐데 시간을 쪼개서 투자하기가 쉽진 않은거 같지만 아직까진 못할꺼같다는 아니다.😤 열심히 해봐야겠다..😢

#### 📌 4주차-1 받은 코드리뷰

![4주차-1](../img/4주차1.png)

#### 📌 4주차-2 받은 코드리뷰

![4주차-2](../img/4주차2.png)
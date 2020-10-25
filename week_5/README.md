## 🚀 5주차 회고 및 코드리뷰 정리
- 이번주 과제는 redux-thunk를 사용해 비동기 처리를 하는 레스토랑 조회 구현하기였다.
- 물론 이번 과제도 TDD로 진행되었다!
- 확실히 저번주보다는 속도가 붙었던거 같다.
- 하지만 역시 테스트를 작성할 때는 구현할 때보다 생각을 더 많이 해야해서 아직까진 연습이 더 필요하다고 느꼈다.
- 또한, 이번주에는 비동기 api에 대해서 테스트에 대해서 작성할려하니 역시 쉽지 않았다.
- 그러므로 인해서 `fetch` 사용할 때 테스트를 작성하는 방법을 알았다. 또한, `redux-mock-store` 를 사용하여 action을 테스트하는 방법도 알았다.

### ✌ 이번주에 받은 코드리뷰를 바탕으로 배운 것들은?

- 테스트를 위해 사용하기 위한 데이터들을 변수명에 굳이 `fixture`라고 할 필요가 없다. 
- 만약 사용하는 곳에서 이후에 `fixture`가 아닌 데이터를 사용하게 된다면 모두 변경점이 되게 된다.

```javascript
// 변경 전
export const regionsFixture = [];
// 변경 후
export const regions = [];
```

- `(V)`를 체크를 표현해주는 name과 별개로 그려져야 한다.
- 그래서 `name`을 그대로 넘기고 선택된 값을 알기 위해서 `check` 값을 같이 넘겨주었다.
- 그 후 Item 컴포넌트에서 작업해주었다.

```jsx
// 변경 전
// CategoryList.jsx
<ul>
    {categories.map(({ id, name }) => (
    <Item
        key={id}
        name={id === categoryState ? `${name}(V)` : name}
        onClick={() => onSelectCategoryClick({ type: 'category', id })}
    />
    ))}
</ul>
// Item.jsx
const Item = ({ name, onClick }) => (
  <li>
    <button type="button" onClick={onClick}>
      {name}
    </button>
  </li>
);

// 변경 후
// CategoryList.jsx
<ul>
    {categories.map(({ id, name }) => (
    <Item
        key={id}
        name={name}
        check={id === selectedCategory}
        onClick={() => onSelectCategoryClick({ type: 'category', id })}
    />
    ))}
</ul>
// Item.jsx
const Item = ({ name, onClick, check }) => (
  <li>
    <button type="button" onClick={onClick}>
      {name}
      {check && '(V)'}
    </button>
  </li>
);
```

- `CategoryList`와 `RegionList` 두 개의 컴포넌트를 하나의 `container`에 같이 묶어서 `ListContainer`로 사용했다.
- 같이 사용해도 될거 같다는 생각을 한 이유는 두 개의 컴포넌트가 넘기는 값만 다르고 하는 일은 비슷했다고 판단하였고, 충분히 하나의 `container`로 사용해도 함수나 `action`에 있어서 문제가 되지 않을 것이라 판단하였다.
- 하지만 코드리뷰에서 하나의 `container`로 묶으니까 역할이 불분명해진다는 지적을 받았다.
- 그래서 `categoriesContainer`와 `regionsContainer`로 분리를 하였다.
- `action`을 테스트할 떄 직접 `action` 객체의 배열을 검증하는 것이 좀 더 명확해진다.
- 실제로 어떤 `payload`가 들어가는지 표현할 수 있다.

```javascript
// 변경 전
expect(actions[0]).toEqual(setRestaurants({ type: 'categories', info: categoriesInfo }));

// 변경 후
expect(actions).toEqual([{
  type: 'setRestaurants',
  payload: {
    type: 'categories',
    info: categoriesInfo,
  },
}]);
```

### ✌ 새롭게 알게 된 것들과 참고 자료
- [동시기 처리 모델 vs 비동기식 처리 모델](https://poiemaweb.com/js-async)
- [Promise](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [async 와 await](https://ko.javascript.info/async-await)
- [fetch](https://ko.javascript.info/fetch)
- [자바스크립트 코딩의 기술 Chapter 9: 외부 데이터에 접근하라.](https://github.com/saseungmin/reading_books_record_repository/tree/master/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%20%EC%BD%94%EB%94%A9%EC%9D%98%20%EA%B8%B0%EC%88%A0/Chapter%209)
- [REST API 제대로 알고 사용하기](https://meetup.toast.com/posts/92)
- [redux-mock-store](https://github.com/reduxjs/redux-mock-store)
- [jest-fetch-mock](https://github.com/jefflau/jest-fetch-mock)

### 😢 그래서 회고는??
- 저번주와 비교했을 떄 TDD와 좀 더 친해진거 같다! 😒
- 하지만 친해졌다고 시간이 단축이 될 줄 알았지만, 여전히 이번주도 시간이 많이 걸렸던 과제였다..
- 시간 배분을 잘해야되는데 성격이 하나에 몰두하면 다른게 안보여서.. 시간 배분을 잘 못하는 거 같다.
- 다음 주 할 일들을 정리하여 정해놓고 해봐야겠다.. 
- 일단 코드숨 과제를 주라고 생각하고 과제를 하고, 요즘 알고리즘을 너무 안풀었다.. 제발 풀자.., you don't know js 책 읽으며 정리하기. 우테코 지원서 작성하기.. 블로그도 너무 안썼는데? 큰일났네? 코딩 첼린지 프로젝트도 마무리해야 되는데.. 우선순위를 정하고 해볼려해도 쉽지않다..
- 다음 주는 프로젝트 마무리 단계가 다가와서 야근이 생길 수도 있을 거 같다..ㅠ (12월 까지만 벼텨보자..)
- 그래도 다행인건 몸은 너무 힘들지만, 코딩하는 것이 힘들다고 생각들지는 않아서 그나마 다행이다.
- 몸이 지쳐가면 안되는데 그래서 그런가 자꾸 부정적으로 생각하는 거 같다. 
- 나름 긍정의 아이콘인데ㅜ 그럴 순 없다. 다음주도 의미있게 달려봐야겠다!!

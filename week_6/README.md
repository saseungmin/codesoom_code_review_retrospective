## 🚀 6주차 회고 및 코드리뷰 정리
- 이번 주 과제는 레스토랑 상세 페이지 구현하는 것이였다.
- `react router`를 다시 복습했던 계기가 되었다.
- 이번 주는 저번 주보다 과제를 어떻게 할지 수월하게 진행되어서 더 빠르게 PR를 할 수 있었다.
- 그에 따라 코드리뷰도 좀 더 많이 받을 수 있던 주였다.

### ✌ 이번주에 받은 코드리뷰를 바탕으로 배운 것들은?
- 과제하던 도중 [경로 문제](https://github.com/CodeSoom/week6-assignment-1/pull/26#issuecomment-717351178)(`http://localhost:8080/restaurants/1`)로 인하여 원하는 대로 작동되지 않았었는데 [링크](https://github.com/CodeSoom/week6-assignment-1/pull/26#discussion_r514432533)와 같은 코드리뷰를 받았다.
`<script src="main.js"></script>` 되어 있었던 경로를 `<script src="/main.js"></script>`로 변경해주니 해결이 되었다. `main.js`가 항상 루트위치에서 열리게 해주면 되었다.
- 슬랙에서 홀맨님의 답변에 `htmlWebpackPlugin`을 사용한 웹팩 설정이 눈에 띄였다.
- 예전에 webpack 인프런 강의를 듣던게 생각나서 [정리해놨던 것](https://github.com/saseungmin/webpack_babel_lint_tutorial/blob/master/webpack-study/Plugin.md#-htmltemplateplugin)을 찾아보았다.
- 분명 공부했고 그 당시 이해했다 생각했지만 역시 계속 써보고 익숙해지지 않는 이상 내 것이 아니였다.
- 이번 과제에서 코드리뷰를 통해 폴더 별로 분리해보라는 말을 듣고 폴더 별로 분리해보았다.
- 테스트 코드도 리팩토링 대상이다. 다했다 생각했지만, 익숙해지지가 않아서인지 하나 둘씩 까먹는거 같다.
- `withRouter` 없이 `match`나 `history`를 못가져오는 줄 알았지만, 그렇지 않았다.
- 레스토랑 상세정보를 불러온 후 언마운트될 때 스토어에 담겨 있는 기존의 상세정보를 없애주기 위해 action을 호출했었는데 이 방법보다 간단하게 풀어낼 수 있었다.

```jsx
// 기존 
useEffect(() => {
  dispatch(loadRestaurantDetail(id));
  return () => {
    dispatch(resetRestaurantDetail());
  };
}, []);
```
- 위 방법에서 `loadRestaurantDetail`에 대한 초기화를 컴포넌트 단에서 해주지 않고 `action` 최초 호출 시점에 초기화를 해주는 방법이였다.

```jsx
export function loadRestaurantDetail(restaurantId) {
  return async (dispatch) => {
    if (!restaurantId) {
      return;
    }
    dispatch(setRestaurantDetail(null));

    const restaurantDetail = await fetchRestaurantDetail(restaurantId);
    dispatch(setRestaurantDetail(restaurantDetail));
  };
}
```
- github test에 fail이 나는 경우가 가끔씩 있었는데 이문제에 대해서도 답을 얻었다.
- `re run`?을 하라고 하시는데 아직까지 잘 모르겠다. ([참고](https://github.com/CodeSoom/week6-assignment-1/pull/26#pullrequestreview-521152816))

### 🤔 저번 주와 다른 점과 느낀점은?
- 저번 주에는 급급하게 했던거 같은데 이번 주는 확실히 나아진 느낌? 이다.😤
- 그래도 매주 나아지고 있는 거 같다.. 그렇다고해서 많이 달라졌다고는 못하겠다ㅠ
- 저번 주에 다짐했던 시간 분배는 또 잘 못지켜진거 같다. 그래도 알고리즘은 3문제 정도는 푼거 같다. 알고리즘은 안하면 안할 수록 자꾸 잃어버리는 거 같다. 계속 꾸준히 풀어보는 방법 밖에 없는데 그게 진짜 쉽지 않은거 같다.
- 벌써 내일이면 7주차이고 그 다음주면 8주차이다.. 시간은 왜 이렇게 빠르게 흘러가는 건지.. 벌써 코드숨이 시작한지가 2달이 다 되간다는게 말도 안된다..
- 공부하는 건 너무 즐겁고 코딩도 즐겁고.. 하지만, 이번 주는 정말 공부 외적으로 너무 힘든 한주였다.
- 요 근래 들어서 제일 공부에 집중하기 힘들었다. 너무 싱숭생숭하고 마음을 다잡기가 너무 힘들다. 어쩌면 좋을까?? 마음에 진정이 필요하다.. 심리적으로 너무 불안한 거 같다.
- 지금 가장 중요한 건 공부이다. 제발 딴 생각하지말고 집중하자.

#### 📌 6주차 받은 코드리뷰

![6주차](../img/6주차.png)
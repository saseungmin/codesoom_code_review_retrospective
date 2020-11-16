## 🚀 8주차 회고 및 코드리뷰 정리

### 📚 배운점이 있다면?

- 이번주는 redux를 이용해서 개발했을 때 복잡해졌을 때 [Redux toolkit](https://redux-toolkit.js.org/)사용하는 방법과 꾸미기 위한 [Emotion](https://emotion.sh/docs/introduction)을 사용해봤다!
- 또한, `React.memo`와 `useCallback`을 사용하여 최적화 하는 법을 다시 알게 되었다.
- `Emotion`을 사용해보면서 알고 있었던 `styled-components`와 비교가 되었는데, 뭐가 좋다라는 것은 아직까지 모르겠다. 근데, 객체형식으로 사용하니까 `10em`이런 것들은 문자열로 묶어줘야해서 조금은 불편했던거 같다. 자동 완성 부분도 불편한 점이라고 생각했다.
- `Redux toolkit`을 사용하면서 `action`을 따로 만들지 않아도 된다는 점에서 큰 장점이 있다고 생각이 들었고, ducks-pattern 을 사용하여 `action`과 `reducer`를 하나의 파일로 만드니 좋았다. 또한, [기본적으로 미들웨어(redux-thunk)가 포함](https://redux-toolkit.js.org/api/getDefaultMiddleware#included-default-middleware)되어 있다는 장점이 있다!  하지만, 역시 공부가 필요하다 느꼈다.
- `React.memo`와 `useCallback`을 사용하면서 아직도 어디에 써야 최적화할 수 있을까는 
명확하게 답할 수는 없는거 같다. 이 또한 공부가 필요한 부분이다.
- `styled component`는 `styles` 폴더로 분리하는 것이 좋아보인다!
- 아직까지는 폴더를 분리하여 어떤 이름과 어떤 형태로 분리해야 할지 햇갈린다! 흠...🤔


### 📌 참고 사항
- [styled-components](https://styled-components.com/)
- [Emotion](https://emotion.sh/docs/introduction)
- [CSS-in-JS에 관해 알아야 할 모든 것](https://d0gf00t.tistory.com/22)
- [Redux-toolkit 한글 번역](https://soyoung210.github.io/redux-toolkit/tutorials/basic-tutorial/)
- [기본으로 포함된 미들웨어](https://redux-toolkit.js.org/api/getDefaultMiddleware#included-default-middleware)
- [PureComponent](https://ko.reactjs.org/docs/react-api.html#reactpurecomponent)
- [메모이제이션](https://ko.wikipedia.org/wiki/%EB%A9%94%EB%AA%A8%EC%9D%B4%EC%A0%9C%EC%9D%B4%EC%85%98)
- [React.memo()]()
- [React.memo() 현명하게 사용하기](https://ui.toast.com/weekly-pick/ko_20190731)
- [useCallback](https://ko.reactjs.org/docs/hooks-reference.html#usecallback)

### 🤔 이번주는 어땠어? 그리고 다음주는?
- 이번 주는 다음 주를 위한 발판?이였다..😢
- 이번 주는 좀..과제를 열심히 하지 않았다. 다 핑계일 뿐.. 내가 나태해진 것.. 다음 주부터 다시 죽어보자는 마인드로 한 달 열심히 해봐야겠다. 😤
- 8주차가 끝나고 이제 강의와 과제는 모두 끝이났다. 벌써 2달이 흘렀고 이제 남은 건 마지막 한 달인 개인 프로젝트만이 남았다.
- 개인 프로젝트는 뭐할지 생각을 해보았는데 쉽게 뭐할까?라는 것은 떠오르지 않았다. 
- 곰곰히 생각해 본 결과로는 예전부터 개발 스터디? 모임?을 찾고 마음 맞는 사람들과 같이 스터디를 진행할 수 있는 그런 사이트를 만들어야겠다 생각했다.
- 사실 4주안에 할 수 있을지는 모르겠지만, 말씀해주신 것처럼 제대로 만든 기능이 한 개 두 개를 목표로 해보자.
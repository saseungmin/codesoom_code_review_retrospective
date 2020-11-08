## 🚀 7주차 회고 및 코드리뷰 정리
- 7주차인 이번주는 로그인 기능과 리뷰를 작성하는 `POST`로 처리하는 기능을 구현하는 것이였다.
- 이번주 아샬님의 강의 영상의 길이가 긴 것을 보고 많은 시간이 필요할 것이라고 느꼈다.
- 하지만 더 많이 필요한 만큼 시간을 할애하지 못했다.
- 더 많은 시간을 투자하고 싶어도 회사일이 바빠서 하기가 쉽지 않았다.
- 이번주 PR은 화요일날 올렸지만, 과제를 완료한 것은 금요일에서 토요일 넘어가는 새벽이였다.
- 그래서 이번주는 리팩토링을 하지 못했다.
- 늦게 한 만큼 내 손해라는 것은 누구보다 잘 알고 있었지만, 그럴 수 없는 것이 아쉬웠다.
- 지금 과제하는 것도 꾸역꾸역? 히는 거 같은데 프로젝트 한 달을 잘 마무리 지을 수 있을까..?
- 그리고 지금 다니고 있는 회사를 퇴사하기로 마음먹었다. 지금 다니는 회사도 좋고, 사람들도 좋고 야근도 많지 않고 나쁘지 않다. 하지만, 나는 내가 하고 싶은 프론트앤드 개발자가 되고 싶다. 그게 전부다.

### ✌ 이번주에 받은 코드리뷰를 바탕으로 배운 것들은?
- `'입력이 안된 사항이 있습니다.'`는 [`Magic literal`](https://refactoring.com/catalog/replaceMagicLiteral.html) 이라는 것이라는 걸 알게 되었다.
- 하지만 테스트에서는 텍스트 그대로를 보여주는 것이 좋다.
- 윤석님의 [친절한 설명](https://github.com/CodeSoom/week7-assignment-1/pull/26#discussion_r516718860)이였다..
```jsx
const { container } = render(<ErrorMessage message={message} />);

expect(container).toHaveTextContent('입력이 안된 사항이 있습니다.');

// component
const ERROR_MESSAGE = '입력이 안된 사항이 있습니다.';

// 생략...
{error && <ErrorMessage message={ERROR_MESSAGE} />}
```

### 📚 참고 사항
#### [httpie](https://httpie.io/)
- HTTP 클라이언트 CLI 도구입니다. 간단한 데이터 조회 및 전송을 테스트해볼 수 있다.

#### [Authorization 헤더](https://developer.mozilla.org/ko/docs/Web/HTTP/Headers/Authorization)
- HTTP Authorization 요청 헤더는 유저 에이전트에서 서버에 인증정보를 전달하기 위해 사용된다.
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication

#### [LocalStorage](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage)
- LocalStorage는 브라우저에 데이터를 저장하기 위해 사용된다.
- localStorage는 저장된 데이터의 만료기간이 없고, key와 value는 항상 문자열로 저장된다.
- [SessionStorage](https://developer.mozilla.org/ko/docs/Web/API/Window/sessionStorage)
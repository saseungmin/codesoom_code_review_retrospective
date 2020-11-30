## 🚀 10주차 회고 및 개인 프로젝트 2주차 회고

### ✌️ 이번 주 개인 프로젝트를 진행하면서 배운 것들은?

#### 📚[firebase](https://firebase.google.com/)
- google의 firebase를 배웠다.
- 처음 사용해봐서 알아가는데 시간이 많이 걸렸다.
- firebase의 백앤드 역할을 대신할 `Cloud FireStore`를 사용해보았고, `Authentication`을 사용해서 로그인과 회원가입의 기능을 구현했다.
- 또한, firebase hosting을 사용해 배포를 하였다.

#### 📚[draft.js](https://draftjs.org/)
- 글을 작성할 떄 에디터를 적용했다.
- 또한, `draft.js` 기반으로 한 [react-draft-wysiwyg](https://jpuri.github.io/react-draft-wysiwyg/)도 같이 사용했다.

#### 📚컴포넌트에서 CSS 파일을 불러올 때 테스트가 깨졌던 이유
- 컴포넌트에서 css 파일을 import 실킬 때 테스트가 계속 깨져서 꽤 많이 고민을 했었다.

```javascript
import 'react-draft-wysiwyg/dist/react-draft-wysiwyg.css';
```

- https://github.com/CodeSoom/project-react-2-saseungmin/pull/30#discussion_r531165153
- [jest 공식 문서](https://jestjs.io/docs/en/webpack#handling-static-assets)를 참고하여 해봤지만 제대로 해결되지 않았다. 테스트를 watch로 하고 있다보니 테스트를 껐다가 다시 킬 생각을 하지 않아서 해결이 안됬던거 같다.
- [moduleNameMapper](https://jestjs.io/docs/en/configuration#modulenamemapper-objectstring-string--arraystring)

```javascript
// jest.config.js
moduleNameMapper: {
  '\\.(jpg|jpeg|png|gif|eot|otf|webp|svg|ttf|woff|woff2|mp4|webm|wav|mp3|m4a|aac|oga)$': '<rootDir>/__mocks__/fileMock.js',
  '\\.(css|less)$': '<rootDir>/__mocks__/styleMock.js',
},

// styleMock.js
module.exports = {};
```

#### 📚 테스트
- 테스트를 진행함에 있어서 꽤 고민을 많이 했다.
- 외부 라이브러리를 사용할 때 테스트 작성하는 방법 또한, 어떻게 테스트를 진행할 수 있을까?에 대한 점 등등.. [링크](https://github.com/CodeSoom/project-react-2-saseungmin/issues/31#issuecomment-734907598)
- coverage에 대한 압박감..? 꼭 100%가 되야할 거 같은 그런 것들..?
- api 호출시 테스트에 대한 점.[링크](https://github.com/CodeSoom/project-react-2-saseungmin/pull/32#discussion_r532153157)


### ✌️ 느낀점이 있다면?

- 저번 주보다 이번 주 마지막 프로젝트에 시간을 더 투자한 한 주였다. 
- 저번 주보다 할 것들, 계획을 잡아둔게 더 많았고, 그것들을 해결하기 위해서 여러모로 고민이 많았던 한 주였다. 또한, firebase 같은 경우도 처음 사용해보기 떄문에 시간이 더 더욱 오래걸릴 수 밖에 없었다. 
- 하지만, 역시 시간을 투자하고 배움에 고통을 느끼며 젹용해보고 배워가니 전에 몰랐던 firebase를 사용한 방법을 배웠고, 앞으로도 적용시킬 수 있는 부분이 생겼다는 점에 굉장히 만족스럽다. 
- 테스트를 작성하는데에 있어서는 고민을 많이 했던 한 주고 테스트를 작성에 많은 시간을 투자했다. 투자한 시간 만큼 이 역시 배운점이 많았다. 또한, 외부 라이브러리 적용이나, api를 사용하는 부분은 우리가 할 수 있는 부분과 굳이 테스트를 함으로써 얻을 수 있는 부분이 많지 않기 때문에 coverage를 100%를 만족시키기 위해서 많은 고민은 접어두자! 🚀
- 함수형 자바스크립트 스터디를 시작했고, 책을 못 읽고 가서 아쉬웠다. 다음 주는 시간을 투자해서 책을 읽자.
- 이제 2주가 남았는데 할 것이 태산이다. 차근차근 해보자. 🧐 아직까진 열심히 하고있다. 계속 소홀하지 말고 꾸준히 해보자.
- You don't know JS책은 역시 이번 주도 펴보지도 못했다. 일단.. 함수형 자바스크립트 스터디와 코드숨에 집중하자.


### 🎯 진행사항
- [개인 프로젝트 2주차 계획](https://github.com/CodeSoom/project-react-2-saseungmin/issues/20)
- [GitHub 저장소](https://github.com/CodeSoom/project-react-2-saseungmin)
- URL 주소: https://sweet-1cfff.web.app/
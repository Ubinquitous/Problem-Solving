## 리액트 라우터 키워드 똑똑하게 사용하기

이건 한 코딩 유튜버 분의 영상을 들으며 클론코딩을 하던 도중,  
한 2~3시간 동안 애를 먹은 오류이다.  

친구가 이 레포지토리를 보고서 블로그 같아서 킹받는다고 했었는데,  
의도한 것은 아니지만 서술하며 쓰고, 여러가지 코드들을 넣다보니 그렇게  
된 것 같다.. 음 뭐 이런 형식도 나쁘지 않다고 생각함.  

거두절미하고 본론으로 들어가보자.

## keyword를 찾을 수 없습니다 :: "Routes"
사실 결론부터 말하자면 버전 차이다. 리액트 라우터가 최근에 업데이트가  
되어서 업데이트가 되지 않은 버전을 설치 후 "어.., 왜 오류가 발생하지?"  
하는 사람과 그 반대로 최신 버전을 설치 후 예전 키워드를 사용하며 어리  
둥절하는 경우가 있다. 물론 경험담임.

React router-dom 6v 이후로는 사용법이 바뀌었다. 따라서 위의 소제목  
과 같은 에러가 발생했다면 버전이 6v 이전인 5v일 것이다. 

따라서 다음과 같이 Switch 키워드를 사용해야한다.

```jsx
    import { BrowserRouter as Router, Switch, Route } from 'react-router-dom';

    <Router>
        <Switch>
            <Route>
                <CustomComponents1 />
                <CustomComponents2 />
            </Route>
        </Switch>
    </Router>
```

이렇게 하면 정상적으로 작동된다. 안된다면 터미널에서 다음의 명령어를 통해 버전 확인을 해보는 걸 추천.

```
> react-router-dom --version
> react-router --version
```

## keyword를 찾을 수 없습니다 :: "Switch"

이건 설명 안해도 될 것이다. 반대로 하면 됨.  
근데 내 경험담인데 오류 때문에 멘탈 터져서 인터넷 찾아보는데  
흥분해서 글은 눈에 안보이고 코드만 원할 때가 생각나기 떄문에  
친절히 코드를 보여주겠다. 나는 인터랙튑한 개발자니까  

```jsx
    import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';

    <Router>
        <Routes>
            <Route>
                <CustomComponents1 />
                <CustomComponents2 />
            </Route>
        </Routes>
    </Router>
```

근데 그럼 오류가 또 날거야 왜냐

## Route 안에는 Element가 들어갈 수 없습니다

이것도 사실 버전 때문에 생기는 오류다. 잡담 안하고 바로 보여주겠다.

```jsx
    import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';

    <Router>
        <Routes>
            <Route element={<CustomComponents1 />} />
            <Route element={<CustomComponents2 />} />
        </Routes>
    </Router>
```

이런 식으로 Route 안에 element = {} 식으로 넣고 싶은 컴포넌트를 표현해주고,  
Route를 셀프 클로징 태그로 바꾸어주면 해결된다. 또 버전이 업데이트가 되어  
사용 방법이 바뀌거나 하면 수정하겠다.


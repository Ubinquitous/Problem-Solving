## map 함수를 사용할 때에 나는 에러

리액트에서 map 함수를 사용하여 더미데이터를 파싱하던 도중 에러가 발생했다.  
좀 오랜만에 쓰는 것 같은데... 막상 내가 겪는 에러는 많은데 잘 안쓰는 것 같음.  
map 함수에 대한 에러는 구글링을 통해 알아보니 내 에러와 같은 대표적인 두 가지  
에러가 있었다.

## cannot read properties of undefined (reading 'map')

```js
return(
  <div>
      {index.map(indexs => {
        return (<h1 href={indexs.link}> {indexs.title} </h1>);
	  })}
  </div>
);
```

대충 이런 구조의 맵 함수를 돌리면 에러가 뜬다. 뭐 undefined를 읽을 수 없다고 함.  
프론트엔드 개발자라면 map을 사용할 때 이외에도 이 에러를 한 번 이상은 만나봤을 것이다.
해결법은 다음과 같다.

```js
return(
  <div>
      {index && index.map(indexs => {
        return (<h1 href={indexs.link}> {indexs.title} </h1>);
	  })}
  </div>
);
```

&& 연산자를 사용하여 이 에러를 해결할 수 있다. React는 화면이 리턴되고 나서 모든 것을 실행한다.  
그렇기 때문에 아직 무언가를 불러오지 않은 상태에서 함수를 사용하면 Undefined로 에러가 나는 것.  
이에 대한 자세한 사항은 리액트와 브라우저의 라이프사이클 메서드에 대해서 공부하는 걸 추천한다.  

JS에서 boolean && expression은 boolean의 값에 따라 boolean이 true면 expression,  
false면 false를 실행한다.  

최근까지 이게 뭐 하는 식인지 잘 몰랐었는데, 오라클에서의 NVL과 매우매우 비슷함. &&를 공부하기보단  
NVL에 대해서 공부하고 비교해가며 이해하는 걸 추천함.

## Array.map is not a function

매우 간단하다. 소제목과 같이, n.map에서의 n에는 Array type만 들어갈 수 있다.  
```md
 Objects, {} in JavaScript does not have the method .map(). It's only for Arrays, [] - Stack over flow
```
그래서 map에는 배열 타입밖에 넣지 못한다. 그래서 다음과 같이 json을 수정할 수 있다.

```js
const [data] = useState({
    data: 1,
    name: 'Ubin',
    gender: 'M',
}, {
    data: 2,
    name: 'Hohyun',
    gender: 'M'
}) 
// 위의 코드를 다음과 같이 변경할 수 있다.
const [data] = useState(
    [ // 배열 (중요)
        {
            data: 1,
            name: 'Ubin',
            gender: 'M',
        },
        {
            data: 2,
            name: 'Hohyun',
            gender: 'M'
        }
    ]
    ) 
```

파싱할 때에도 array[0].object 이런 식으로 파싱해야 undefined가 뜨지 않는다.  
최근에 props로 넘겨온 자료를 파싱할 때 자꾸 undefined가 떠서 많이 힘들어하고 있는데,  
조만간 그와 관련해서도 하나 끄적여보겠다.
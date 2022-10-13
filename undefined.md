# Cannot Read Undefined 무시법

최근에 재미있고 유연한 기능을 알았다.  
프론트엔드 주니어 개발자가 라이프사이클메서드를 잘못 다뤘을 때 제일 많이 만나는 에러가  
Cannot Read property...Undefined이다. 대충 값이 없는데 어떻게 코드를 읽냐는 뜻.  

보통 useEffect를 사용하지 않고 값을 화면에 return할 때 뜨기도 한다.  
난 코드를 제대로 짜놨는데 안되길래 계속 골머리를 싸고있었다. 그때 친구가 재밌는걸 알려줌.  

```jsx
const Component = () => {
    .
    .
    .
    return (
        <div>
            <span>{response.data.people[3].name}</span>
        </div>
    )
}
```
```ruby
error message : cannot read undefined...
> response.data.people[3].name
                    ~~~~~^
```

이럴 때에는 오류가 나는 객체의 부분에 ?를 넣어주면 된다.  
question operator는 undefined가 나오면 구문을 무시한다.
```
> response.data.people[3]?.name
```
  
확실히 많은 것을 알아야 코딩할 때 개발자가 편안하게 코딩할 수 있는 것 같다.
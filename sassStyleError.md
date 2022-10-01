## 작성한 스타일 코드가 반영되지 않음

한 2~3주 전에 있었던 오류다. 오류는 아니고 실력 미숙이다. 최근에 친구도 이 오류를 나에게 묻길래 생각나서 써본다.  

Scss를 사용할 때, 프로젝트 규모가 커지거나 하면 간혹 Scss가 이상하게 작동하는 경우가 있다. 추가적인 어떤 요소를  
넣어도 반영이 되지 않고, 내가 설계한 것과 다르게 움직이는 경우가 있다. 처음에 이것 때문에 2시간 동안 애먹었다.  

내가 겪은 오류의 이유는 className, 혹은 id명이 겹치기 때문이었다.  

```jsx
    <div>
        <div className='class' />
    </div>
```
```scss
    .class {
        background-color: red;
    }
```
```scss
    .class {
        width:50px;
        height:80px;
        border: 1px inset #194258;
    }
```
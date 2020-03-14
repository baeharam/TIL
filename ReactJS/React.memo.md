[참고 자료](https://ui.toast.com/weekly-pick/ko_20190731/)

## React.memo()

컴포넌트가 다시 렌더링되는 경우는 엄밀히 말해서 3가지이다.

* `setState()` 의 호출
* `props` 의 변화
* `forceUpdate()` 의 호출

앞선 2가지는 익숙한데, 마지막 경우는 조금 생소할 수 있다. 이는 state나 props를 사용하지 않고 다른 데이터를 사용하여 업데이트를 수행할 때 사용하는 메서드로 많이 쓰이진 않지만 역시 re-rendering을 발생시킨다. 어쨌든 이런 경우가 렌더링을 발생시키는데 위와 같은 변화가 없는데도 렌더링이 발생된다면 성능문제를 야기하기 때문에 개선해야 한다.

## 자식의 렌더링

부모가 렌더링 되면 자식에게 전달되는 props가 같아도 다시 렌더링 된다. 그렇기 때문에 같은 props를 통해서 렌더링 되는 경우를 방지하기 위해서 `React.memo()` 를 사용할 수 있다. 자식 컴포넌트를 `React.memo()` 로 묶어주면 PureComponent와 같이 동작하기 때문에 re-rendering이 발생하지 않는다. 물론 이것은 함수 컴포넌트일 때이며 클래스 컴포넌트라면 PureComponent를 사용하는 것이 적절하다.
# reducer 함수
1. 맨 처음 호출될 때의 state 값 : undefined
2. state가 undefined일 때의 기본값 parameter에 설정
3.  상태의 불변성을 유지하면서( ...state) 데이터에 변화를 일으켜야 한다. 
객체의 구조가 복잡해지면(object.something.inside.value) 불변성을 관리하며 업데이트하는 것이  번거롭기 때문에 redux의 state는 최대한 깊지 않은 구조로 짜는 것이 좋다.

```
function reduccer(state=initalState, action){
  switch (action.type) {
    case TOGGLE_SWITCH:
     return {
       ...state, toggle: !state.toggle
     }
  case INCREASE:
  return {
    ...state,
    counter: state.counter + action.diffrence
  }
  case DECREASE:
  return {
    ...state,
    counter: state.counter -1
  }
    default:
      return state
  }
}
```

## reducer 함수(순수한 함수)의 조건

1. 이전 state와 action 객체를 parameter로 받는다.

2. parameter 외의 값에는 의존하면 안된다.

3. 이전 state는 절대로 건드리지 않고 (불변성을 지키며), 변화를 준 새로운 state 객체를 만들어서 반환한다.

4. 똑같은 parameter로 호출된 리듀서 함수는 언제나 똑같은 결과 값을 반환해야 한다.
(ex. 랜덤 값을 만들거나, Date 함수를 사용하여 현재 시간을 가져오거나, 네트워크 요청 등은 같은 parameter를 입력해도 다른 결과를 만들어 낼 수 있기 때문에 사용하지 않는다. 이러한 작업은 action을 만드는 과정 혹은 추후 redux middleware에서 처리해도 된다.(비동기작업) )

 
<br/>

> [16.2.6] 리듀서 함수 정의,
> [16.3.3] 리듀서는 순수한 함수

# 구독하기 (react-redux를 사용하지 않을 경우)

1. store의 내장 함수 subscribe를 이용해 store의 상태가 바뀔 때마다 render 함수를 호출한다. 

```
store.subscribe(render);
```

> [16.2.9] 구독하기
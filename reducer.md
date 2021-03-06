# reducer

reducer是一个数据处理函数，这意味着一个reducer函数必须满足**输入值固定，则输出值固定**。

当使用`store.dispatch`执行一个action后，reducer函数会被触发，触发时会传递两个参数`state`和`action`。`state`是之前的状态，`action`是action函数的值。如下

```
function todoApp(state, action) {
  if (typeof state === 'undefined') {
    return initialState
  }

  // For now, don't handle any actions
  // and just return the state given to us.
  return state
}
```

通常，我们还需要指定reducer的缺省值，如下：

```
const initialState = {
  todos: []
}
function todoApp(state = initialState, action) {
  // For now, don't handle any actions
  // and just return the state given to us.
  return state
}
```

在此基础上，通常使用`switch`来匹配action的内容，如下：

```
const initialState = {
    todos: []
}
function todoApp(state = initialState, action) {
      switch(action.type){
        //case condition
        default:
            return state
      }
}
```

## 注意

和action一样，我们同样需要注意对象类型的数据，return时请使用`Object.assign`深复制。

同时，在变更数组类型数据时，建议根据情况使用以下方法：

1. 删除数据时使用`splice`。
2. 更改某条数据时使用 `slice` 和`concat`拆分后拼接。

## 合并多个reducer

redux提供 `createStore` 方法来合并多个reducer，如官方文档示例：

```
// reducers.js
export default theDefaultReducer = (state = 0, action) => state;

export const firstNamedReducer = (state = 1, action) => state;

export const secondNamedReducer = (state = 2, action) => state;


// rootReducer.js
import {combineReducers, createStore} from "redux";

import theDefaultReducer, {firstNamedReducer, secondNamedReducer} from "./reducers";

// Use ES6 object literal shorthand syntax to define the object shape
const rootReducer = combineReducers({
    theDefaultReducer,
    firstNamedReducer,
    secondNamedReducer
});

const store = createStore(rootReducer);
console.log(store.getState());
// {theDefaultReducer : 0, firstNamedReducer : 1, secondNamedReducer : 2}
```


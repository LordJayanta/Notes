

## STEP 1 : configure a store
1. create `app` folder on the src folder
2. create `store` file on the app folder

```jsx
import { configureStore } from '@reduxjs/toolkit';

export const store = configureStore({})
```




## STEP 2 : Create Reducer using `createSlice()`
1. create `features` folder on the `src` folder
2. Now in this folder you need to create a another folder for reducer. and in this case this is `todo`
3. Create file names `todoSlicer.jsx` 


```jsx
import { createSlice } from "@reduxjs/toolkit";

const initialState = {}

export const todoSlicer = createSlice({
    name: 'todo',
    initialState,
    reducers: {
        addTodo: () => {},
        removeTodo: () => {}
    }
})

export const {addTodo, removeTodo} = todoSlicer.actions;
export default todoSlicer.reducer
```


```jsx
import {createSlice, nanoid } from '@reduxjs/toolkit';

const initialState = {
    todos: [{id: 1, text: "Hello world"}]
}



export const todoSlice = createSlice({
    name: 'todo',
    initialState,
    reducers: {
        addTodo: (state, action) => {
            const todo = {
                id: nanoid(), 
                text: action.payload
            }
            state.todos.push(todo)
        },
        removeTodo: (state, action) => {
            state.todos = state.todos.filter((todo) => todo.id !== action.payload )
        },
    }
})

export const {addTodo, removeTodo} = todoSlice.actions

export default todoSlice.reducer
```



## STEP 3 : import reducer
```jsx
import { configureStore } from '@reduxjs/toolkit';
import todoReducer from '../features/todo/todoSlice';

export const store = configureStore({
    reducer: todoReducer
})
```


## STEP 4 : Setup Provider
1. Goto `src/main.jsx` file import **provider** and **store**
```jsx
import { Provider } from 'react-redux'
import { store } from './app/store.js'
```

2. Wrap the app in this provider

```jsx
<Provider store={store}>
    <App />
</Provider>
```

## STEP 5 : use Method or functions

```jsx
import { useDispatch } from 'react-redux';
import { addTodo } from './features/todo/todoSlicer';

const [input, setInput] = useState("");
const dispatch = useDispatch();

const handleSubmit = () => {
    dispatch(addTodo(input))
}
```


## STEP 6 : use value and variables

```jsx
import { useSelector } from 'react-redux';
const todos = useSelector(state => state.todos)
```
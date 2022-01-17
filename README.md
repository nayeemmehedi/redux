# redux

### redux has 3 parts 

### 1.store
### 2.reducer
### 3.action 


# store
   
 //npm i redux react-redux
import { combineReducers, createStore } from 'redux'

//npm install --save redux-devtools-extension
import { composeWithDevTools } from 'redux-devtools-extension';

import {CounterReducer} from '../Reducer/CounterReducer'


const CombineReducer = combineReducers({
    CounterReducer
})

export const store = createStore(CombineReducer,composeWithDevTools())


# reducer 

export const CounterReducer =(state=0,action)=>{

    switch (action.type) {

        case "increment":
            if(state<=9){
                return state+1

            }
            break
           
        

         case "decrement":
            if(state>=1){
                return state-1
                

            }
            break
           
        default:
            return state
    }

}


# action 


export const increment =()=>{
    return {
        type : "increment"
    }
}

export const decrement =()=>{
    return {
        type : "decrement"
    }
}





# index.js add store 

import { Provider } from 'react-redux';
import { store } from './ReduxFunction/Store/Store1st';



ReactDOM.render(
  <React.StrictMode>
    <Provider store = {store1}>
    <App />
    </Provider>
  </React.StrictMode>,
  document.getElementById('root')
);



# app.js


import {useSelector,useDispatch} from "react-redux"
import {increment, decrement} from "./ReduxFunction/Action/Action1st"

function App() {
  

  const value = useSelector(state => state.CounterReducer)
  const dispatch = useDispatch()

 
  return (
    <div className="App">

      <button style={{ backgroundColor:"blue"}} onClick={()=>dispatch(increment())}>add item</button>

      <h6>value ={'>'} {value}</h6>

      <button style={{ backgroundColor:"blue"}} onClick={()=>dispatch(decrement())} >Remove item</button>


    
    </div>
  );
}

export default App;

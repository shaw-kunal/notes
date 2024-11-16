###########################################################

Q. what are react hooks?
ans : React hooks are a new feature in react that allows you to use state as well as other react feature without having to write a class

Q. What are the benefits of using react hooks?
ans: can able to manage state
good perfomace
better code composition

Q.What is difference between a class component and functional component with hooks?
ans :

CLASS COMPONENT : require the use Es6 class - state is handle using "this.state" and updated using tht this.setState();
life cycle methods are:
render(),
componentDidMount(),
componentDidUpdate(),
componentWillUnmount();

<!--


class MyComponent extends React.Component {

    constructor(props){
     super(props);
     this.state ={count:0}
    }

    componentDidMount(){
      console.log("component mount")
    }
    componentDidUpdate(){
      console.log("Component update")
    }

   increment = () => {
    this.setState({ count: this.state.count + 1 });
  }

    render(){
         return (
               <div>
                  hello
                  <button onClick={this.increment}>click me</button>
              </div>
      )
    }

}

 -->

FUNCTIONAL COMPONENT:
systax: Uses a simpler function systax without needing classes.

state Management: Uses hooks like useState for mananing state and useEffect for handing side effects, among others (useContext, useReducer etc)

LifeCycle Method: No explicit lifecycle methods, you can handle side effects with useEffect() , which mimics lifeCycle behaviour.

4. Explain the difference betweena state and props in react.
   ans: A state is data that it own and manges. it can be updated over time , and modification will cause the component to re-render. State is mutable

A props is data that transfer from parent component to child component. they are read-only and the child componet can not change him. it is immutable in nature.

5##########################################################Q.
what are the rules of hooks in react.
and: 1. Hooks should only be called at the top level of you component. 2. Hooks should only call from the react funciton not be called within loops, condition or nested function.

###########################################################Q.How do you manage side effects in React functional components with hooks?
ans: The use Effect hook is used in react functional component to manage side effect.

###########################################################

Q. What is the useState hook and how is it used?
ans: useState hook is used to manage the state. it return a state variable and a function to update this state varible.

###########################################################
Q. What are the different ways to update the state in React?

ans: In react , there are two primariy method for updating state:

1. Using a class component's setState function.
2. Using a fucntional component's useState hook.

###########################################################

Q. How do you share the state between the component in react?

1. using props: the state share from parent to child
   2.using the state management tool like redux.
2. using the context API: The context API is usefull when you need to share state across many components , expecially when the state is needed at different leverl in the component tree. It allows u to avoid props drilling

<!--


   const UserContext = React.createContext();

   funtion App = () =>{
      const [user,setUser] = useState('');

      return (

       <UserCOntext.Provider value={{user,setUser}}>

        <ChildComponent1>
        <ChildComponent2>

       </UserContext.Provider>

      )

   }

   function ChildComponent(){

     const { user,setUser} = useContext(UserContext);

     return (

     <p>hii ,{user?.name}</p>

     )

   }



 -->

##########################################################
Q. How to create a custom hook ?

ans : creating a useToggle hook

<!--

   function useFetch(url){
     const [data,setData] = useState(null);

     const [loading,setLoading] = useState(true);
     const [error,setError] = useState(null);

     useEffect(()=>{
          const fetchData= async ()=>{
          setLoading(true);
          //fetch data logic and handle the error

          }
        }


        return {data,loading, error}

   }
   export default useFetch;

 -->

################################################################
Q. what is the useMemo hook and how is it used?
The useMemo hook in react is used to opeitmize performace by memoizing the result of an expensive calculation. it only recompute the valye when one of its dependencies changes, allowing you to avoid unnecuesary recalucation on every render.

<!-- const memoizeValue = useMemo (()=>findFact(n),[n]); -->

################################################################

Q. how react memo and useMemo are different
React.memo is a higher order component used to memoize a whole functional component. It prevents unnecessay re-render of the componet if the props have not changes.

Usga: it is used to wrap a functinal component and ensure it only re-render when its props changes. This

################################################################

useCallback: is a react hook used to memoize callback function, preventing them from being re-created on very render unless their dependencies change. This helps optimize performace.

why-
In react , functions are recreated on every render. This can lead to performace issue if -
You pass a function as a props to memoized child component(using React.memo) , causing the unusual re-render.

useCallback solves this by returning the same function instance as long as its dependencies don’t change.

<!--
index.jsx

import React, {useState, useCallback} from "react";


function ParentComponent(){

  const [count, setCount] = useState(0);
  const [text,setText] = useState("");

  // memoize the increament functon

   const increment  = useCallback(()=>{
      setCount((prev)=>prev+1);
   },[]);

  return (
    <div>
      <h1>Count: {count}</h1>
      <ChildComponent onIncrement={increment} />
      <input
        type="text"
        value={text}
        onChange={(e) => setText(e.target.value)}
        placeholder="Type something"
      />
    </div>
  );

  }


const childComponent = React.memo(({onIncrement})=>{
  console.log('ChildComponent re-rendered');
  return <button onClick={onIncrement}>Increment</button>

})


 -->

###############################################################

Q. what is useEffect and how it is differnent from useLayouteEffect

ans: in react both useEffect and useLayoutEffect are hook used to handle side effect in function component, but they differ in timing of execution and behaviour.

The useEffect hook is used in react functional components to manage side effects. The useLayoutEffect hook is a subhook of the useEffect hook that is used for sideeffect that must be performed before browser paint the next frame.

###############################################################

how do you use useReducer hook for complex state management ?

ans: The useReducer hook is used we need to update multiple state at once. Instead of managing state with useState (which gets messay with lots of state changes) , useReducer helps you organize how state changes happen using actions.

key concept :
State: The data you want to manage.
Action: Something that tells the state how to change(eg: 'START_FETCHING')

reducer: it is function that take current state and action , then return the new state

<!--

const INITIAL_STATE ={
    count: 0,
    loading: false,
    error:null
}

const reducer = (state,action)=>{
    switch(action.type){
        case 'INCREMENT':
            return {...state,count:state.count+1};
        case 'DECREMENT':
            return { ...state, count:state.count - 1};
        default :
        return state;
    }
}

function Counter(){
    const [state,dispatch] = useReducer(reducer,INITIAL_STATE);
    return (
      <div>
      <p>Count: {state.count}</p>
      <p>Loading: {state.loading ? 'Yes' : 'No'}</p>
      <p>Error: {state.error || 'None'}</p>
      <button onClick={() => dispatch({ type: 'INCREMENT' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'DECREMENT' })}>Decrement</button>
     </div>
    )
}
 -->


################################################################

Q. 8. What is the useSWR hook and how is it used?

ans: The useSWR  hook is a react hook for data fetching that stand for state-while-revalidate. Its part fo the popular SWR lib and it help to manage the remote data fetching and caching in a simple and effecient way. SWR automatically handles fetcing , caching ,updating and revalidating data from an api. making it very  usefull for building fast and reponsive apps.



################################################################

Q> what is the useRef Hook and how it is used?
ans: The useRef hook creates and manages mutable reference to values. This can be useFul for storing non-reactive data, such as a DOM element or a substring

################################################################


Q. what is useTransition hook and how it is used ?
ans: useTransition is a React Hook that lets you update the state without blocking the UI.

how it work- 
* it enbles you to mark certain state update as non-urgents. These update  can be delayed  untill after more urgent  update are finished.
* React gives priority to urgent task like typing , clicking or hovering while deferred tasks are processed in the backeground.


<!-- const [isPending, startTransition] = useTransition(); -->

################################################################

Q. what is conditional rendering in react.
ans : when there are multiple component in react and we want to render components according to our pregerence and some condition then we use  conditional rendering. 
eg : if user is login then show the logout button else show the login button
<!-- 
{isLoggedIn == false ? <DisplayLoggedOut /> : <DisplayLoggedIn />} -->



################################################################

Q.what is react router? 
and : react router is  a  standerd library for routeting in recact .  for navigation from one page to another  we  use the react-router.


################################################################
Q.  Explain the lifecycle method of component?
ans: A react component can go through four stages of its life cycle:

1. Initialization: This is the stage where the component is constructed with the given props and default state. This is done in the costructor of a component class. 

2. mounting:  Mounting is the stage of rendering the JSX  return by the render method. here componeDidMount() function call.

3. updating :  when any of  state of component  is  updated and the application is repainted. here componentDidUpdate() function call.

4. Unmounting: As the name suggest Unmountin is the final step of the component lifecycle  where the component is removed from the page.

################################################################
Q.Explain the methods used in mounting phase of components?

ans : Mounting is the phase of the component lifecycle when the initializaton of the component is completed and the  component is mounted on the DOM and re-render for the firest time on the webpage. the mounting phase consist of two such predefined functions as describe below:


componentWillMount() : this function is invoked right before  the component is mounted on the DOM.

ComponentDidMount(): this function is invoked right after the component is mounted on the DOM.



####################################################################

Q. what is this.setState function in react?

ans: we use the setState() method to change the state object. It ensure that the component has been updated and calls  for re-rendering of the component. 


####################################################################
Q. what are hooks in react?

ans: hook are a new addition in react. such that developer can use state and other feature without writting a class.

################################################################
Q. what is react fragments?
ans: when  we are trying the render more than one root element we have to put the  entire component inside a `div` tag. 
we use them intead of the extra div.




################################################################

Q. what is prop driling and its disadvantage?
ans: props drilling is basically a situation when the same data  is being sent at almost every level to requirments in the final level. 







################################################################################################################################
Q. what are the controlled and uncontrolled components in react?

ans: in react , component can be either controlled or uncontrolled based on how they manges form data. 

Controlled Component:  it is one where data (like the value of an input) is handler by the component's state. The component is reponsible for managing its own state, and any updted to the input field are done by modifying the state, which then re-render the component.

<!-- 
function ControlledComponent() {
  const [inputValue, setInputValue] = useState("");

  const handleChange = (event) => {
    setInputValue(event.target.value);
  };

  return (
    <div>
      <input type="text" value={inputValue} onChange={handleChange} />
      <p>{inputValue}</p>
    </div>
  );
} -->


Uncontrolled Component: An uncontrolled component is one where form data is handled by the DOM itself.Instead of using state to manage form input, a refs is used to access the form values direcly from the dom.

here : a ref is used to reference the input element and the value is retrived when necessary(for example , when submittin a form)


<!-- 

function UncontrolledComponent() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`Input value: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
}

 -->


##############################################################
Q. what  is useRef hook in react?
ans: this hook is used that allows to directly create a reference to the DOM element in the functional component. 






#########################################################################################################################


Q. explain the componentDidMount method in react?
ans: The componentDidMount() method allow us to execute the react code when the component is  already render in the DOM.


ans: Imagine you're building a form in React where a user inputs their name and clicks a submit button. You want to handle the form submission and input changes uniformly across all browsers. React's synthetic events ensure this happens without worrying about differences in event implementations in various browsers.

Scenario:
You create a form with an input field and a submit button. You need to handle the form submission and track the input changes.

Here's an example:
<!-- 
jsx
Copy code
import React, { useState } from 'react';

function UserForm() {
  const [name, setName] = useState("");

  // Handle input change
  const handleInputChange = (event) => {
    setName(event.target.value); // Synthetic event triggered here
  };

  // Handle form submission
  const handleSubmit = (event) => {
    event.preventDefault(); // Prevents page reload, using synthetic event
    alert(`User submitted: ${name}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input type="text" value={name} onChange={handleInputChange} />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default UserForm; -->

how it work - 

When the user types in the input field, React triggers a synthetic event for the onChange handler. This synthetic event ensures the event behaves the same, regardless of the browser.
The handleInputChange function is called with this event, and you can access the value (event.target.value) to update the state (name).
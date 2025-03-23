<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Components Props & States</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>
 <h2 style=" margin: 0; color:#57acf2; ">What is State in React?</h2>
 In React, state is an object that holds dynamic data and determines the component's behavior and rendering. It is used to make components interactive and re-render whenever state changes.

 `In Simple words we can say state is object that is used to control the component whose value can be changed`
 ### **Implementation and Important Points**
 - In class compponent we have the state but functional component are stateless component and in functional component state is achieved by the concept of hooks.
 - States are used to pass the value within the components.
 - State is mutable: Unlike props, which are read-only, state can change over time.
 - Triggers re-render: When state updates, the component automatically re-renders.
 - Local to a component: Each component manages its own state.

 <h2 style=" margin: 0; color:#57acf2; ">Updating State in React</h2>
 
 - Direct vs Functional Update
 ```js
// Wrong way (may cause issues with async state updates):
setCount(count + 1);
setCount(count + 1); // This will not increase by 2 due to batching
```
 ```js
// Correct way (using functional update to get the latest state):
setCount(prevCount => prevCount + 1);
setCount(prevCount => prevCount + 1); // This ensures the count increases by 2
```
```js
// update state of objects
const [user, setUser] = useState({ name: "John", age: 25 });
const updateAge = () => {
  setUser(prevUser => ({ ...prevUser, age: prevUser.age + 1 }));
};
```
```js
//Updating State of Arrays
//To update an array without modifying the original, use map, filter, or spread operator.
const [items, setItems] = useState(["Apple", "Banana"]);
const addItem = () => {
  setItems(prevItems => [...prevItems, "Orange"]);
};

```
 <h2 style=" margin: 0; color:#57acf2; ">What is Props in React?</h2>

 Props (short for "Properties") are used to pass data from a parent component to a child component in React. They make components reusable and dynamic by allowing data to be passed and rendered accordingly.

 `In Simple words we can say props is object that is used to pass the value b/w components whose value can't changed`

 ###  **Key Features of Props:**
- **Updates:** Does not trigger re-render
- **Immutable:** Props cannot be changed inside the child component.
- **Read-only:** The child receives props as input but cannot modify them.
- **Passed from Parent to Child:** Data flows top-down (unidirectional).
- **Reusable:** Components can be customized using different props.

### How to set default props for the component
- Default Props (Handling Missing Props)
```js
function Welcome({ name = "Guest" }) {
  return <h1>Hello, {name}!</h1>;
}
```
`OR`
```js
Welcome.defaultProps = {
  name: "Guest"
};
```
- PropTypes (Type Checking for Props):To ensure correct data types, we can use PropTypes.
```js
import PropTypes from "prop-types";
function UserProfile({ name, age }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
    </div>
  );
}

UserProfile.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number
};
```
## States vs Props
| Feature    | Props | State |
|------------|------------------------------|--------------------------------|
| **Mutability** | Immutable (Cannot be changed inside the component) | Mutable (Can be changed using `setState` or `useState`) |
| **Scope** | Passed from parent to child | Local to the component |
| **Usage** | Used for communication between components | Used for managing dynamic data |
| **Control** | Controlled by the parent | Controlled by the component itself |

<br><h2 style=" margin: 0; color:#57acf2; ">What is Components in React?</h2>

Components are the building blocks of any React application. They are reusable, self-contained pieces of UI that help in organizing the structure of an application.

In Simple words: `Components are reusable UI blocks in React that help structure and organize an application.`

- **Points to Remember**
    - Components break UI into smaller, reusable pieces
    - Functional components are preferred (due to React Hooks)
    - Class components are still in use but mostly in legacy codebases
    - Components can be stateless (only UI) or stateful (manage dynamic data)
    - Props allow communication between components

<br><h2 style=" margin: 0; color:#57acf2; ">Different types of components in react</h2>


| Type                         | Description | Key Features | Example Code |
|------------------------------|-------------|--------------|--------------|
| **Functional Components** (Modern ✅) | Simple JavaScript function that returns JSX | Uses `useState`, `useEffect`, easy to read, faster | ```jsx function Greeting({ name }) { return <h1>Hello, {name}!</h1>; } export default Greeting; ``` |
| **Class Components** (Older ⚠️) | Uses ES6 class syntax and has a `render()` method | Uses `this.state`, lifecycle methods like `componentDidMount` | ```jsx class Greeting extends React.Component { render() { return <h1>Hello, {this.props.name}!</h1>; } } export default Greeting; ``` |
| **Stateful Components** | Manages dynamic data using state | Uses `useState` or `this.state` | ```jsx function Counter() { const [count, setCount] = useState(0); return <button onClick={() => setCount(count + 1)}>Count: {count}</button>; } ``` |
| **Stateless Components** | Displays UI without managing state | Only receives `props` | ```jsx function Welcome({ message }) { return <h1>{message}</h1>; } ``` |
| **Controlled Components** | React controls form input values | Uses `useState` to handle input | ```jsx function Form() { const [text, setText] = useState(""); return <input value={text} onChange={(e) => setText(e.target.value)} />; } ``` |
| **Uncontrolled Components** | The DOM controls form input values | Uses `useRef` to get values | ```jsx function Form() { const inputRef = useRef(null); return <input ref={inputRef} />; } ``` |
| **Presentational Components** | Only handles UI, no logic | Stateless, only receives `props` | ```jsx function Button({ label }) { return <button>{label}</button>; } ``` |
| **Container Components** | Handles logic and passes data to other components | Fetches data, manages state | ```jsx function DataContainer() { const [data, setData] = useState([]); useEffect(() => { fetchData().then(setData); }, []); return <List items={data} />; } ``` |

[Click here to get the deep knowledge about them](./Deep%20Explanation%20of%20HOC,%20Controlled,%20and%20Uncontrolled%20Components%20in%20React.md)

  </div>
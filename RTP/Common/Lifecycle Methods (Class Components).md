<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Lifecycle Methods in Class Components (React)</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>
In React class components, lifecycle methods are special methods that run at different stages of a component's existence. These methods are categorized into three phases:

- Mounting Phase (When the component is created and inserted into the DOM)
- Updating Phase (When the component updates due to state/props changes)
- Unmounting Phase (When the component is removed from the DOM)

| Phase            | Method                 | Description |
|-----------------|-----------------------|-------------|
| **Mounting**    | `constructor()`        | Initializes state and binds event handlers. |
|                | `static getDerivedStateFromProps(props, state)` | Updates state based on props (rarely used). |
|                | `render()`              | Renders the UI (required in all class components). |
|                | `componentDidMount()`   | Runs after the component is added to the DOM (used for API calls, subscriptions, etc.). |
| **Updating**    | `static getDerivedStateFromProps(props, state)` | Called before rendering when props change. |
|                | `shouldComponentUpdate(nextProps, nextState)` | Optimizes performance by controlling re-renders. |
|                | `render()`              | Updates the UI based on new props/state. |
|                | `getSnapshotBeforeUpdate(prevProps, prevState)` | Captures info (like scroll position) before DOM updates. |
|                | `componentDidUpdate(prevProps, prevState)` | Runs after updates (used for API calls, handling side-effects). |
| **Unmounting**  | `componentWillUnmount()` | Cleans up before the component is removed (used for removing event listeners, canceling API calls). |
| **Error Handling** | `componentDidCatch(error, info)` | Catches JavaScript errors in child components (Error Boundaries). |

## **Example of LifecycleMethod**

```js
import React, { Component } from "react";

class LifecycleDemo extends Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
    console.log("Constructor: Initializing state");
  }

  static getDerivedStateFromProps(nextProps, prevState) {
    console.log("getDerivedStateFromProps: Syncing state with props");
    return null; // Return new state or null to keep it unchanged
  }

  componentDidMount() {
    console.log("componentDidMount: Component added to DOM");
  }

  shouldComponentUpdate(nextProps, nextState) {
    console.log("shouldComponentUpdate: Should re-render?");
    return true; // Return true to allow re-render, false to prevent
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log("getSnapshotBeforeUpdate: Capturing before update");
    return null; // Used for things like tracking scroll position
  }

  componentDidUpdate(prevProps, prevState) {
    console.log("componentDidUpdate: Component updated");
  }

  componentWillUnmount() {
    console.log("componentWillUnmount: Cleanup before removal");
  }

  componentDidCatch(error, info) {
    console.log("componentDidCatch: Handling errors");
  }

  render() {
    console.log("Render: Rendering UI");
    return (
      <div>
        <h1>Lifecycle Methods Demo</h1>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Update State
        </button>
      </div>
    );
  }
}

export default LifecycleDemo;
```
| Feature                        | getSnapshotBeforeUpdate() |
|--------------------------------|--------------------------|
| Purpose                        | Captures information before the DOM update. |
| Runs Before                    | The actual DOM update (right before rendering changes). |
| Must Return                    | A value (or `null` if no snapshot is needed). |
| Use Case Example                | Preserving scroll position in a chat app. |
| Commonly Used With             | `componentDidUpdate()`. |

## **How getSnapshotBeforeUpdate() Works?**
`getSnapshotBeforeUpdate(prevProps, prevState) is a React lifecycle method used in class components. It is called right before the DOM is updated, allowing you to capture some information (like scroll position, cursor position, etc.) before the update happens.`


* Runs before the actual DOM update.
* Captures data before the update occurs.
* Must return a value (or null if no snapshot is needed).
* The returned value is passed as the third parameter to componentDidUpdate().
```js
import React, { Component } from "react";

class ChatBox extends Component {
  constructor(props) {
    super(props);
    this.chatRef = React.createRef();
    this.state = { messages: ["Hello!", "How are you?"] };
  }

  getSnapshotBeforeUpdate(prevProps, prevState) {
    console.log("getSnapshotBeforeUpdate: Capturing scroll position before update");
    // Get the scroll position before the new message is added
    return this.chatRef.current.scrollHeight;
  }

  componentDidUpdate(prevProps, prevState, snapshot) {
    console.log("componentDidUpdate: Restoring scroll position");
    if (snapshot !== null) {
      // Maintain the user's scroll position after new messages are added
      this.chatRef.current.scrollTop = snapshot;
    }
  }

  addMessage = () => {
    this.setState((prevState) => ({
      messages: [...prevState.messages, "New message!"],
    }));
  };
  render() {
    return (
      <div>
        <h3>Chat Box</h3>
        <div
          ref={this.chatRef}
          style={{ height: "100px", overflowY: "auto", border: "1px solid black" }}
        >
          {this.state.messages.map((msg, index) => (
            <p key={index}>{msg}</p>
          ))}
        </div>
        <button onClick={this.addMessage}>Add Message</button>
      </div>
    );
  }
}
export default ChatBox;
{/*
How It Works Here
User scrolls through the chat messages.
Before new messages are added, getSnapshotBeforeUpdate() saves the current scroll position.
After the DOM updates, componentDidUpdate() uses the saved scroll position to restore it.
The chat window does not scroll to the top when a new message is added, improving user experience.
*/}
```
  </div>
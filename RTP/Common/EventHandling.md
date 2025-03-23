<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Event Handling in React vs. React Native</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

React and React Native handle events similarly, but there are key differences in how events work due to platform variations (DOM vs Native UI). Let’s break it down:

## **Key Takeaways**
- React Web uses SyntheticEvent, whereas React Native uses NativeEvent.
- React Web has onClick, but React Native uses onPress.
- React Web handles form inputs with onChange, while React Native uses onChangeText.
- There’s no preventDefault() in React Native—use custom logic instead.
- For gestures in React Native, use Gesture Responder System or react-native-gesture-handler.
- In React Native, preventDefault() does not exist, so you need custom logic.
- But In React Web, we use event.preventDefault()

## **Differences: React vs React Native Event Handling**
| Feature                | React (Web)                                      | React Native                                    |
|------------------------|------------------------------------------------|------------------------------------------------|
| **Event System**       | Uses SyntheticEvent (wrapped around native events). | Uses NativeEvent (directly from the OS).       |
| **Click Events**       | `onClick` (for buttons, divs, spans, etc.).      | `onPress` (for `TouchableOpacity`, `Pressable`). |
| **Touch Events**       | `onTouchStart`, `onTouchMove`, etc.              | `onTouchStart`, `onTouchMove`, etc.            |
| **Keyboard Events**    | `onKeyDown`, `onKeyUp`, `onKeyPress`.            | `onSubmitEditing` (TextInput only).            |
| **Form Handling**      | Uses `onChange` for `<input>` elements.         | Uses `onChangeText` for `TextInput`.           |
| **Event Object**       | SyntheticEvent with `event.target`, `event.preventDefault()`. | NativeEvent with `nativeEvent`, `e.nativeEvent.text`. |

  </div>
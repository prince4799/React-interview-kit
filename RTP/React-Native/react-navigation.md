<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; "> React Navigation – Complete Guide</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

React Navigation is the most popular routing and navigation library for React Native. It allows seamless navigation without reloading the app, ensuring smooth user experience in mobile applications.

## **Why Do We Need React Navigation?**
- Handles screen transitions in React Native.
- Supports stack, tab, and drawer navigation.
- Uses dynamic parameters in routes.
- Provides deep linking support.
- Offers smooth animations for navigation.

## **Protected Routes (Authentication)**

```js
import { NavigationContainer } from "@react-navigation/native";
import { createStackNavigator } from "@react-navigation/stack";
const Stack = createStackNavigator();
const isAuthenticated = false;

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        {isAuthenticated ? (
          <Stack.Screen name="Dashboard" component={Dashboard} />
        ) : (
          <Stack.Screen name="Login" component={Login} />
        )}
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

## **Interview Questions & Answers on React Navigation**
## **Basic Questions**

**What is React Navigation?**
* It’s a routing library for React Native that enables screen transitions without page reloads.

**What is the difference between React Router and React Navigation?**
* React Router is for web, while React Navigation is for React Native apps.

**What are the different types of navigation in React Native?**
* Stack, Bottom Tabs, Drawer, and Material Top Tabs.

**How do you navigate between screens?**
* Using navigation.navigate("ScreenName").

## **Advanced Questions**
**What is the difference between Stack and Tab Navigation?**
* Stack Navigation follows a push/pop mechanism (like a call stack), while Tab Navigation provides a persistent menu.

**How do you pass parameters between screens?**
* Using route.params in the destination screen.

**How do you implement authentication-based navigation?**
* By conditionally rendering different stacks for authenticated vs. unauthenticated users.

**How can you optimize navigation performance?**
* Use lazy loading and remove unnecessary re-renders.

  </div>
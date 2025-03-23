<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Optimizing Performance in React Native Apps</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>


<br><h2 style=" margin: 0; color:#57acf2; ">Optimize Rendering & Re-renders </h2>
- **Use useMemo & useCallback**: Prevents unnecessary function re-creation.
```
const memoizedValue = useMemo(() => computeHeavyData(data), [data]);
const memoizedCallback = useCallback(() => handlePress(id), [id]);
```

- **Use React.memo() for Components:** Avoids unnecessary re-renders.
```
const MyComponent = React.memo(({ name }) => <Text>{name}</Text>);
```

- **FlatList Optimizations:**
    - Use keyExtractor
    - Enable initialNumToRender
    - Use getItemLayout

```
<FlatList
  data={data}
  keyExtractor={(item) => item.id.toString()}
  initialNumToRender={10}
  getItemLayout={(data, index) => ({ length: 50, offset: 50 * index, index })}
/>
```


<br><h2 style=" margin: 0; color:#57acf2; ">  Reduce JavaScript Workload </h2>

- **Minimize State Updates:** Avoid unnecessary useState updates.
- **Batch State Updates:** Group multiple state updates using useReducer instead of multiple setState.
- **Use Event Throttling/Debouncing:** For expensive operations like scrolls or text input.

```
import { debounce } from "lodash";
const handleSearch = debounce((query) => fetchResults(query), 300);
```


<br><h2 style=" margin: 0; color:#57acf2; ">  Optimize Images & Assets </h2>

- **Use WebP Format:** Smaller file sizes for faster loading.
```
Lazy Load Images:
<Image source={{ uri: 'image_url' }} loadingIndicatorSource={placeholder} />
```
- **Use react-native-fast-image for better caching**.

<br><h2 style=" margin: 0; color:#57acf2; ">  Improve Navigation Performance </h2>

```js
Use react-native-screens for better screen rendering

import { enableScreens } from 'react-native-screens';
enableScreens();
```
- **Use Stack.Navigator with screenOptions to optimize animations**

<br><h2 style=" margin: 0; color:#57acf2; ">  Reduce Bundle Size & Optimize Dependencies </h2>
- Remove Unused Dependencies
- **Use Hermes Engine:** Improves JS execution performance.
- **Add this in android/app/build.gradle:**`enableHermes: true`
- Enable Proguard for Android to remove unused code.

<br><h2 style=" margin: 0; color:#57acf2; ">  Optimize Network Requests </h2>

- **Use Axios with Gzip Compression**
axios.get('https://api.example.com/data', { headers: { 'Accept-Encoding': 'gzip' } });
Batch API Calls when possible.


<br><h2 style=" margin: 0; color:#57acf2; ">  Use Background Threads for Heavy Tasks </h2>
- Use react-native-reanimated for smooth animations.
- Use react-native-gesture-handler for better gestures.
- Move Expensive Operations to Native Modules

<br><h2 style=" margin: 0; color:#57acf2; ">  Optimize Animations & UI Performance </h2>
- Use react-native-reanimated instead of Animated API for 60FPS animations.
- Reduce zIndex and avoid excessive ShadowProps.

<br><h2 style=" margin: 0; color:#57acf2; ">  Optimize SQLite / Local Storage </h2>
- Use react-native-mmkv for fast key-value storage instead of AsyncStorage.
- For databases, prefer SQLite or WatermelonDB for large datasets.

<br>

### `Optimizing lists in React` requires handling large data efficiently. The key techniques involve [pagination](#pagination-pagination-loads-data-in-chunks-instead-of-rendering-everything-at-once), [throttling](#throttlingthrottling-ensures-that-a-function-executes-at-most-once-in-a-specified-time-interval), and [debouncing](#debouncing-debouncing-ensures-that-a-function-executes-only-after-a-delay-and-prevents-multiple-calls-in-quick-succession).

### **Pagination**: Pagination loads data in chunks instead of rendering everything at once.

- **Types of Pagination**:
    - Offset-based Pagination: Fetch data using page numbers.
    - Cursor-based Pagination: Fetch data based on last item’s ID

```js

//Implementation using FlatList (React Native)

const [data, setData] = useState([]);
const [page, setPage] = useState(1);
const [loading, setLoading] = useState(false);

const fetchData = async () => {
  if (loading) return;
  setLoading(true);

  const response = await fetch(`https://api.example.com/data?page=${page}`);
  const newData = await response.json();

  setData((prevData) => [...prevData, ...newData]);
  setPage(page + 1);
  setLoading(false);
};

return (
  <FlatList
    data={data}
    renderItem={({ item }) => <Text>{item.name}</Text>}
    onEndReached={fetchData} // Load more data when reaching the bottom
    onEndReachedThreshold={0.5} // Trigger when 50% of the list is visible
    ListFooterComponent={loading && <ActivityIndicator />}
  />
);

```

```js 

//Implementation using Infinite Scroll (React.js)
const [items, setItems] = useState([]);
const [page, setPage] = useState(1);
const [loading, setLoading] = useState(false);

const loadMoreItems = async () => {
  if (loading) return;
  setLoading(true);

  const response = await fetch(`https://api.example.com/items?page=${page}`);
  const newItems = await response.json();

  setItems((prev) => [...prev, ...newItems]);
  setPage(page + 1);
  setLoading(false);
};

useEffect(() => {
  window.addEventListener("scroll", () => {
    if (
      window.innerHeight + document.documentElement.scrollTop >=
      document.documentElement.offsetHeight - 100
    ) {
      loadMoreItems();
    }
  });
}, []);

```

### **Throttling**:Throttling ensures that a function executes at most once in a specified time interval.
```js
//Use Case: Optimizing scrolling events
import { useRef } from "react";

const throttle = (func, limit) => {
  let inThrottle;
  return function () {
    if (!inThrottle) {
      func.apply(this, arguments);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
};

const handleScroll = () => {
  console.log("Scrolled!");
};

const throttledScroll = useRef(throttle(handleScroll, 2000));

useEffect(() => {
  window.addEventListener("scroll", throttledScroll.current);
  return () => window.removeEventListener("scroll", throttledScroll.current);
}, []);

```

### **Debouncing**: Debouncing ensures that a function executes only after a delay and prevents multiple calls in quick succession.
```js
// Use Case: Optimizing search input

import { useState, useEffect } from "react";
const [query, setQuery] = useState("");
const [results, setResults] = useState([]);

const fetchResults = async (searchTerm) => {
  const response = await fetch(`https://api.example.com/search?q=${searchTerm}`);
  const data = await response.json();
  setResults(data);
};

useEffect(() => {
  const handler = setTimeout(() => {
    if (query) fetchResults(query);
  }, 500); // Executes only after 500ms of no new input

  return () => clearTimeout(handler); // Cleanup on unmount or new input
}, [query]);

return <TextInput onChangeText={setQuery} placeholder="Search..." />;

```

### **Summary**
- Use `Pagination` for handling large lists efficiently.
- Use `Throttling` for event-driven actions like scrolling.
- Use `Debouncing` for optimizing user input like search queries.

</div>
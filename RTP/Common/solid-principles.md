[Go back](../Index.md)

```md
# SOLID Principles in React Native

## Overview
The **SOLID** principles are a set of five design principles that help developers write clean, scalable, and maintainable code. These principles are especially useful in **React Native** to structure components, state management, and business logic effectively.

## SOLID Principles at a Glance

| Principle | Description | Example in React Native |
|-----------|-------------|-----------------|
| **S** - Single Responsibility Principle (SRP) | A component/class should have only one reason to change. | Separate API calls from UI logic. |
| **O** - Open/Closed Principle (OCP) | Code should be open for extension but closed for modification. | Use HOCs or hooks to extend functionality. |
| **L** - Liskov Substitution Principle (LSP) | Subtypes must be substitutable for their base types without breaking behavior. | Ensure child components behave consistently like their parent components. |
| **I** - Interface Segregation Principle (ISP) | Clients should not depend on interfaces they do not use. | Avoid unnecessary props; create separate smaller components. |
| **D** - Dependency Inversion Principle (DIP) | High-level modules should not depend on low-level modules. Both should depend on abstractions. | Use hooks or context API instead of direct dependencies. |

---

## 1. Single Responsibility Principle (**SRP**)
> **A component should have only one reason to change.**

### ❌ **Bad Example** (Violates SRP: UI + API logic in the same component)
```jsx
const ProfileScreen = () => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetchUserData();
  }, []);

  const fetchUserData = async () => {
    const response = await fetch("https://api.example.com/user");
    const data = await response.json();
    setUser(data);
  };

  return <Text>{user?.name}</Text>;
};
```

### ✅ **Good Example** (Separate API logic into a service function)
```jsx
const fetchUserData = async () => {
  const response = await fetch("https://api.example.com/user");
  return response.json();
};

const ProfileScreen = () => {
  const [user, setUser] = useState(null);

  useEffect(() => {
    fetchUserData().then(setUser);
  }, []);

  return <Text>{user?.name}</Text>;
};
```

---

## 2. Open/Closed Principle (**OCP**)
> **Code should be open for extension but closed for modification.**

### ❌ **Bad Example** (Modifies an existing component to add new behavior)
```jsx
const Button = ({ label, onPress }) => (
  <TouchableOpacity onPress={onPress}>
    <Text>{label}</Text>
  </TouchableOpacity>
);

// Later, modifying it to add a loading state
const ButtonWithLoading = ({ label, onPress, isLoading }) => (
  <TouchableOpacity onPress={isLoading ? null : onPress}>
    <Text>{isLoading ? "Loading..." : label}</Text>
  </TouchableOpacity>
);
```

### ✅ **Good Example** (Uses HOC to extend behavior without modifying existing code)
```jsx
const withLoading = (Component) => ({ isLoading, ...props }) => (
  <Component {...props} disabled={isLoading}>
    {isLoading ? "Loading..." : props.children}
  </Component>
);

const Button = ({ label, onPress, disabled }) => (
  <TouchableOpacity onPress={disabled ? null : onPress}>
    <Text>{label}</Text>
  </TouchableOpacity>
);

const LoadingButton = withLoading(Button);
```

---

## 3. Liskov Substitution Principle (**LSP**)
> **A subclass should be substitutable for its base class without breaking functionality.**

### ❌ **Bad Example** (Child component changes behavior unexpectedly)
```jsx
const Button = ({ label, onPress }) => (
  <TouchableOpacity onPress={onPress}>
    <Text>{label}</Text>
  </TouchableOpacity>
);

const CustomButton = () => (
  <TouchableOpacity>
    <Text>Click Me</Text>
  </TouchableOpacity>
);
```

### ✅ **Good Example** (Child component maintains expected behavior)
```jsx
const CustomButton = (props) => <Button {...props} />;
```

---

## 4. Interface Segregation Principle (**ISP**)
> **Clients should not depend on interfaces they do not use.**

### ❌ **Bad Example** (Component expects all possible props)
```jsx
const UserProfile = ({ name, email, phone, address }) => (
  <View>
    <Text>{name}</Text>
    <Text>{email}</Text>
    <Text>{phone}</Text>
    <Text>{address}</Text>
  </View>
);
```

### ✅ **Good Example** (Smaller, focused components)
```jsx
const UserName = ({ name }) => <Text>{name}</Text>;
const UserContact = ({ email, phone }) => (
  <View>
    <Text>{email}</Text>
    <Text>{phone}</Text>
  </View>
);
```

---

## 5. Dependency Inversion Principle (**DIP**)
> **High-level modules should not depend on low-level modules. Both should depend on abstractions.**

### ❌ **Bad Example** (Direct API call inside component)
```jsx
const Dashboard = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch("https://api.example.com/data")
      .then((res) => res.json())
      .then(setData);
  }, []);

  return <Text>{data?.value}</Text>;
};
```

### ✅ **Good Example** (Abstract API logic using hooks)
```jsx
const useFetchData = (url) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then(setData);
  }, [url]);

  return data;
};

const Dashboard = () => {
  const data = useFetchData("https://api.example.com/data");
  return <Text>{data?.value}</Text>;
};
```

---

## Conclusion
Applying **SOLID principles** in **React Native** results in:
✅ More maintainable code  
✅ Better separation of concerns  
✅ Easier testing and debugging  
✅ Scalable architecture  

```


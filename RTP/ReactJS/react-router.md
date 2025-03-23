<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; "> React Router – Complete Guide</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

## **What is React router?**
React Router is a powerful routing library for handling navigation in React applications. It allows us to create single-page applications (SPAs) where navigation does not cause a full page reload, improving performance and user experience. 

## **Why Do We Need React Router?**
- SPAs don’t reload the page when navigating.
- Efficient URL-based routing without refreshing the entire app.
- Supports dynamic routing based on parameters.
- Enables nested routing, making layouts modular.
- Provides protected routes for authentication-based navigation.
- Handles 404 pages gracefully.
- Example: Basic Routing.
```js
import React from "react";
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
const Home = () => <h2>Home Page</h2>;
const About = () => <h2>About Page</h2>;
const Contact = () => <h2>Contact Page</h2>;
export default function App() {
  return (
    // <Router> → Wraps the entire app.
    <Router>
      <nav>
      {/*<Link> → Replaces <a> to prevent reloads.*/}
        <Link to="/">Home</Link> | 
        <Link to="/about">About</Link> | 
        <Link to="/contact">Contact</Link>
      </nav>
      {/*<Routes> → Contains multiple <Route> elements.*/}
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
        <Route path="/contact" element={<Contact />} />
      </Routes>
    </Router>
  );
}
```
## **Dynamic Routing**
```js
import { useParams } from "react-router-dom";
const User = () => {
  let { id } = useParams();
  return <h2>User ID: {id}</h2>;
};
export default function App() {
  return (
    <Router>
      <Routes>
        <Route path="/user/:id" element={<User />} />
      </Routes>
    </Router>
  );
}
```
## **Protected Routes (Authentication)**
```js
import { Navigate } from "react-router-dom";
const isAuthenticated = false; // Change to true to access dashboard
const ProtectedRoute = ({ children }) => {
  return isAuthenticated ? children : <Navigate to="/" />;
};

const Dashboard = () => <h2>Dashboard</h2>;
export default function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<h2>Home Page</h2>} />
        <Route path="/dashboard" element={<ProtectedRoute><Dashboard /></ProtectedRoute>} />
      </Routes>
    </Router>
  );
}
```

## **Nested Routes (Layout System)**
```js
{/*
* Explanation
* <Outlet /> acts as a placeholder for nested routes.
* URLs:
* /dashboard/profile → Shows Profile page.
* /dashboard/settings → Shows Settings page.
*/}
import { Outlet } from "react-router-dom";
const DashboardLayout = () => (
  <div>
    <h2>Dashboard</h2>
    <Outlet />
  </div>
);
const Profile = () => <h3>Profile Page</h3>;
const Settings = () => <h3>Settings Page</h3>;

export default function App() {
  return (
    <Router>
      <Routes>
        <Route path="/dashboard" element={<DashboardLayout />}>
          <Route path="profile" element={<Profile />} />
          <Route path="settings" element={<Settings />} />
        </Route>
      </Routes>
    </Router>
  );
}
```
## **Redirects & 404 Page Handling**
```js
//"*" → Matches any undefined route and shows a 404 page.
export default function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<h2>Home</h2>} />
        <Route path="*" element={<h2>404 Page Not Found</h2>} />
      </Routes>
    </Router>
  );
}
```

## **Interview Questions & Answers on React Router**
### Basic Questions
**What is React Router?**
* React Router is a routing library for React applications that enables navigation without refreshing the page.

**What is the difference between `<BrowserRouter>` and `<HashRouter>`?**
* `<BrowserRouter>` uses clean URLs (e.g., /home), while `<HashRouter>` uses hash-based URLs (#/home), useful for older browsers.

**What is the difference between `<Routes>` and `<Switch>`?**
* `<Routes>` (introduced in React Router v6) replaces `<Switch>` to match routes more efficiently.

### Advanced Questions
**How does React Router handle dynamic parameters?**
* It uses useParams() to extract parameters from the URL.

**How do you implement authentication in React Router?**
* Using Protected Routes with `<Navigate>` for redirection.

**What is lazy loading in React Router?**
* It loads components only when needed, reducing initial load time.
```js
import { lazy, Suspense } from "react";
const Home = lazy(() => import("./Home"));
<Suspense fallback={<div>Loading...</div>}>
  <Home />
</Suspense>;
```

**What are nested routes, and why are they useful?**
* They allow multiple pages under a common layout using <Outlet />.

**How can you implement breadcrumbs using React Router?**
* By tracking route changes and mapping them to breadcrumb components.
 </div>
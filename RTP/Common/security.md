<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Security in React & React Native</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>  

Security is crucial in **React** and **React Native** applications to prevent **XSS (Cross-Site Scripting), CSRF (Cross-Site Request Forgery), Injection Attacks, and Data Leaks**. Below is a detailed breakdown of security concerns and best practices.  

---

### 🛡️ **Common Security Threats & Best Practices**  

| Security Concern | React | React Native | Best Practices |
|------------------|-------|-------------|---------------|
| **XSS (Cross-Site Scripting)** | Yes (via user inputs in JSX) | No (no DOM access) | Use `dangerouslySetInnerHTML` cautiously, sanitize inputs. |
| **Injection Attacks** | Yes (SQL, NoSQL, Command injection) | Yes | Use parameterized queries, validate inputs. |
| **CSRF (Cross-Site Request Forgery)** | Yes | No (since no cookies are used) | Use CSRF tokens, SameSite cookies. |
| **Clickjacking** | Yes | No | Use `X-Frame-Options` to prevent UI overlays. |
| **Data Leakage** | Yes | Yes | Never store sensitive data in local storage or AsyncStorage. |
| **Insecure API Calls** | Yes | Yes | Use HTTPS, avoid exposing API keys. |
| **Code Injection (eval, innerHTML)** | Yes | No | Avoid `eval()`, use strict CSP headers. |
| **Dependency Risks** | Yes | Yes | Regularly audit dependencies with `npm audit`. |

---

### 🔑 **Best Practices for Securing React & React Native Apps**  

#### 1️⃣ Secure API Requests  
- Use **HTTPS** for all API requests.  
- Implement **JWT (JSON Web Tokens)** for authentication.  
- Avoid exposing **API keys** in frontend code.  

#### 2️⃣ Secure Data Storage  
- **Do not store sensitive information** (like tokens, passwords) in **localStorage or AsyncStorage**.  
- Use **secure storage solutions** (e.g., `react-native-encrypted-storage`).  

#### 3️⃣ Prevent Cross-Site Scripting (XSS) & Cross-Site Request Forgery (CSRF)

#### What is XSS (Cross-Site Scripting)?
` XSS is a security vulnerability where attackers inject malicious scripts into web applications. These scripts run in the browser of unsuspecting users and can steal sensitive data or manipulate the page content.`
- **Sanitize user inputs** with libraries like **DOMPurify**.  
- Avoid using `dangerouslySetInnerHTML` unless necessary.  

- **How to Prevent XSS in React?**
* Use dangerouslySetInnerHTML with caution
* Avoid using raw HTML inside your components unless absolutely necessary.
* If needed, sanitize the input before rendering.
* Escape User Input
* React automatically escapes inserted values in JSX, preventing raw script injection.
```js
const userInput = "<script>alert('XSS');</script>";  
<div>{userInput}</div> // This will be displayed as text, not executed.
Use Trusted Third-Party Libraries for Sanitization
Example: DOMPurify
import DOMPurify from "dompurify";
const safeHTML = DOMPurify.sanitize(userInput);
<div dangerouslySetInnerHTML={{ __html: safeHTML }} />
```

- Set HTTP Security Headers
- Use Content-Security-Policy (CSP) to block inline scripts:
```pgsql
Content-Security-Policy: default-src 'self'; script-src 'self' 'trusted-scripts.com'
```

#### What is CSRF (Cross-Site Request Forgery)?
`CSRF is an attack where an attacker tricks a user into making an unwanted request to a website where they are authenticated.`

- **How to Prevent CSRF in React & React Native?**
- Use CSRF Tokens (For Forms & API Requests)
- The server generates a CSRF token, which is included in requests to verify authenticity.
- Use SameSite Cookie Attribute
- Set cookies with SameSite=Strict or SameSite=Lax to prevent CSRF.
- Set-Cookie: sessionID=abc123; Secure; HttpOnly; SameSite=Strict;
- Avoid GET Requests for Mutations
- Only allow POST, PUT, or DELETE requests for state-changing operations.
- Use Authentication Best Practices
- Implement OAuth, JWT, or other secure authentication mechanisms.

#### 4️⃣ Secure Navigation & Deep Linking  
- **Validate deep link URLs** to prevent unauthorized app access.  
- Use **React Navigation’s authentication guards**.  

#### 5️⃣ Secure Third-Party Libraries  
- Regularly update dependencies using:  
  ```sh
  npm audit fix
  ```
- Avoid **unmaintained or vulnerable libraries**.  

#### 6️⃣ Prevent Reverse Engineering in React Native  
- Use **Code Obfuscation** (via `hermes` or `ProGuard`).  
- Encrypt sensitive data **before storing it locally**.  

#### 7️⃣ Secure Authentication & Authorization  
- Implement **OAuth, JWT, and biometric authentication** (for mobile apps).  
- Use **role-based access control (RBAC)** for user permissions.  

---

### 🛠 **Security Tools & Libraries**  

| Tool | Purpose |
|------|---------|
| **Helmet.js** | Secure HTTP headers in React apps. |
| **DOMPurify** | Prevents XSS by sanitizing user inputs. |
| **jsonwebtoken (JWT)** | Secure authentication and token verification. |
| **OWASP Dependency-Check** | Detects security vulnerabilities in dependencies. |
| **react-native-encrypted-storage** | Secure key-value storage in React Native. |

---

### 🔍 **Security Interview Questions for React & React Native**  

1. **How do you prevent XSS attacks in React?**  
2. **Why shouldn't we store tokens in localStorage?**  
3. **How can you secure API requests in React Native?**  
4. **What are the risks of using third-party libraries in React projects?**  
5. **How does HTTPS protect data transmission?**  
6. **What is Content Security Policy (CSP) and how does it improve React security?**  
7. **How do you handle deep linking securely in React Native?**  


  </div>
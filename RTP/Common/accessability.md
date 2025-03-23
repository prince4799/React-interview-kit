<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Accessibility (a11y) in React & React Native </h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>
 

## 🔹 What is Accessibility (a11y)?  
**Accessibility (a11y)** ensures that applications are **usable by people with disabilities**, including those with visual, auditory, motor, and cognitive impairments. It enhances **usability, inclusivity, and legal compliance**.  

---

## 🌍 Why Accessibility Matters?  
✅ **Inclusivity** → Enables more users to interact with your app.  
✅ **Better UX** → Improves overall usability for everyone.  
✅ **SEO Benefits** → Helps search engines understand content (for web).  
✅ **Legal Compliance** → Fulfills WCAG, ADA, and other accessibility guidelines.  

---

## 📌 Key Accessibility Features in React & React Native  

| Feature | React (Web) | React Native |
|---------|------------|--------------|
| **ARIA Attributes** | Uses `aria-*` attributes to improve screen reader support. | Not applicable (uses `accessibility*` props instead). |
| **Semantic HTML** | Uses proper elements like `<button>`, `<label>`, `<nav>`, etc. | Requires explicit `accessibilityRole` and `accessible` props. |
| **Keyboard Navigation** | Supports `tabindex`, `onKeyDown`, etc. | Uses `accessible={true}` and gesture handlers. |
| **Screen Readers** | Works with `role` and `aria-live`. | Uses `accessibilityLabel`, `importantForAccessibility`. |
| **Focus Management** | Uses `autoFocus`, `tabIndex`, `ref.focus()`. | Uses `setNativeProps({ isFocused: true })`. |
| **Color Contrast** | Ensures high contrast between text and background. | Requires manual contrast checks for mobile UI. |

---

## 🔹 Accessibility in **React (Web)**  
React follows **WCAG (Web Content Accessibility Guidelines)** and **ARIA (Accessible Rich Internet Applications)** best practices.  

### ✅ Best Practices for Accessibility in React Web  
✔ **Use Semantic HTML** → Prefer `<button>` over `<div>` for buttons.  
✔ **Use ARIA attributes** → Add `aria-label`, `aria-labelledby`, `aria-hidden`.  
✔ **Ensure Keyboard Navigation** → Use `tabIndex`, `onKeyDown` for interactivity.  
✔ **Manage Focus Correctly** → Handle focus shifts with `ref.focus()`.  
✔ **Test with Screen Readers** → NVDA, VoiceOver, and ChromeVox.  

#### 🛠️ Example: Accessible Button in React Web  
```jsx
<button aria-label="Submit form">Submit</button>
```

## 🛠️ Tools for Accessibility Testing  

| Tool | Platform | Purpose |
|------|----------|---------|
| **axe DevTools** | Web | Tests WCAG compliance. |
| **Lighthouse** | Web | Audits accessibility in Chrome. |
| **NVDA & JAWS** | Web | Screen readers for testing. |
| **VoiceOver** | Web & Mobile | Built-in screen reader (Mac & iOS). |
| **TalkBack** | Mobile | Android's screen reader. |
| **react-native-accessibility-engine** | React Native | Checks accessibility issues in RN apps. |

  </div>
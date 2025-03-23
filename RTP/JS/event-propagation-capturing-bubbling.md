[Go back](../Index.md)


# Events in JavaScript

## 1. Introduction to Events
JavaScript events are actions or occurrences that happen in the browser, such as clicking a button, hovering over an element, or pressing a key. Events allow developers to execute functions in response to user interactions.

## 2. Types of Event Propagation
Event propagation determines how events travel through the DOM tree. It consists of three phases:

1. **Event Capturing (Trickling Phase)**
2. **Target Phase**
3. **Event Bubbling Phase**

### **2.1 Event Capturing (Trickling Phase)**
- The event starts from the topmost parent element and trickles down to the target element.
- Capturing phase is rarely used but can be useful in some scenarios.

#### Example:
```javascript
 document.getElementById("child").addEventListener("click", function() {
     console.log("Child clicked");
 }, true); // 'true' enables capturing phase
```

### **2.2 Event Bubbling Phase**
- The event starts from the target element and bubbles up to the topmost parent.
- This is the default event flow in JavaScript.

#### Example:
```javascript
 document.getElementById("child").addEventListener("click", function() {
     console.log("Child clicked");
 }, false); // 'false' enables bubbling phase (default behavior)
```

### **2.3 Event Propagation**
- Event propagation refers to how events move through the DOM tree (capturing and bubbling phases combined).
- By default, most events bubble up from the target element to its ancestors.

### **2.4 Event Delegation**
- A technique where a parent element is assigned an event listener to handle events on its children.
- Useful for dynamically created elements and improves performance.

#### Example:
```javascript
document.getElementById("parent").addEventListener("click", function(event) {
    if (event.target && event.target.matches(".child")) {
        console.log("Child clicked via delegation");
    }
});
```

## 3. Comparison Table

| Concept | Description | Default Behavior |
|---------|-------------|-----------------|
| **Event Capturing** | Events are handled from top to bottom | Disabled |
| **Event Bubbling** | Events bubble up from target to parents | Enabled |
| **Event Delegation** | Assigning events to parent elements instead of children | Useful for dynamic elements |

## 4. Common Interview Questions

### **Q1: What is Event Bubbling in JavaScript?**
**A:** Event bubbling is a process where an event triggered on a child element propagates up to its parent elements in the DOM tree.

### **Q2: What is the difference between Event Bubbling and Event Capturing?**
**A:** Event bubbling starts from the target element and moves up, while event capturing starts from the topmost ancestor and moves down.

### **Q3: How can we stop Event Bubbling?**
**A:** We can stop event bubbling using `event.stopPropagation()`.
```javascript
document.getElementById("child").addEventListener("click", function(event) {
    event.stopPropagation(); // Stops bubbling
    console.log("Child clicked, but bubbling stopped");
});
```

### **Q4: What is Event Delegation? Why is it useful?**
**A:** Event delegation is a technique where a parent handles events for its child elements, improving performance by reducing event listeners.

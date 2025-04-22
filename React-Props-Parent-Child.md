# React: Parent-Child Components & Props Documentation

---

## 1. What are Props?
**Props** (short for "properties") are the way components in React talk to each other. They are used to pass **data** and **functions** from a **parent component** to a **child component**.

---

## 2. Parent and Child Components
- **Parent Component**: A component that calls or renders another component.
- **Child Component**: The component being rendered inside the parent.

**Example:**
```jsx
function Parent() {
  return <Child name="Yugen" />;
}

function Child({ name }) {
  return <h1>Hello {name}!</h1>;
}
```

---

## 3. Passing Props
Props can be:
- Strings
- Numbers
- Functions
- Objects
- Arrays
- Booleans

**Example:**
```jsx
function Parent() {
  const age = 20;
  return <Child name="Yugen" age={age} />;
}

function Child({ name, age }) {
  return <p>{name} is {age} years old.</p>;
}
```

---

## 4. Passing Functions as Props
This allows the child to trigger a function defined in the parent.

```jsx
function Parent() {
  const handleClick = () => alert("Clicked!");
  return <Child onClick={handleClick} />;
}

function Child({ onClick }) {
  return <button onClick={onClick}>Click Me!</button>;
}
```

---

## 5. Passing Objects as Props

```jsx
function Parent() {
  const user = { name: "Yugen", age: 20 };
  return <Child details={user} />;
}

function Child({ details }) {
  return <p>{details.name} is {details.age} years old.</p>;
}
```

---

## 6. Passing Arrays as Props

```jsx
function Parent() {
  const tasks = ["Study", "Read", "Code"];
  return <Child items={tasks} />;
}

function Child({ items }) {
  return (
    <ul>
      {items.map((task, index) => <li key={index}>{task}</li>)}
    </ul>
  );
}
```

---

## 7. Default Props
If no prop is passed, React can fall back to a **default value**.

```jsx
function Button({ label }) {
  return <button>{label}</button>;
}

Button.defaultProps = {
  label: "Default Button"
};
```

---

## 8. Prop Drilling Problem
When data is passed through many layers:

```
<App> ➡️ <Parent> ➡️ <Child> ➡️ <GrandChild>
```

This is called **prop drilling**. It makes code hard to manage and update.

---

## 9. Solution: React Context
React Context allows you to share data globally without manually passing props.

```jsx
const UserContext = React.createContext();

function App() {
  return (
    <UserContext.Provider value="Yugen">
      <Child />
    </UserContext.Provider>
  );
}

function Child() {
  return <GrandChild />;
}

function GrandChild() {
  const user = React.useContext(UserContext);
  return <p>User: {user}</p>;
}
```

---

## 10. Summary
| Concept               | Purpose                           |
|------------------------|-----------------------------------|
| **Props**              | Pass data from parent to child.   |
| **Parent Component**   | Sends data via props.             |
| **Child Component**    | Receives data via props.          |
| **Function as Prop**   | Pass logic (event handling).      |
| **Object/Array Props** | Pass complex structured data.     |
| **Default Props**      | Prevent missing value errors.     |
| **Prop Drilling**      | Over-passing through many layers. |
| **Context API**        | Global data sharing.              |

---

> 💡 This document gives you the core understanding to manage parent-child relationships and props in React — from basic data passing to handling prop drilling issues via Context!


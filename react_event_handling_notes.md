
# 📘 React Event Handling & `e.target` – Beginner Notes

---

## 📍 What is an Event in React?

In React, an **event** is something that happens to an element:
- A click
- A key press
- A form submission
- A change in an input field

React allows us to listen for these events using event handlers like `onClick`, `onChange`, `onSubmit`, etc.

---

## 🎯 What is `e`?

`e` stands for the **event object**. It contains **all the information** about the event that just happened.

When a user interacts with a component, React automatically passes this `e` object to your handler function.

---

## 🔍 What is `e.target`?

- `e.target` is the **DOM element** that triggered the event.

### 🧪 Example:
```jsx
function Example() {
  const handleClick = (e) => {
    console.log(e.target);
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```
> When you click the button, `e.target` will be the button element itself.

---

## 📤 What is `e.target.value`?

When used in an `<input>` element, `e.target.value` gives the **current value** inside that input box.

### ✏️ Example:
```jsx
function Example() {
  const handleChange = (e) => {
    console.log("You typed:", e.target.value);
  };

  return <input type="text" onChange={handleChange} />;
}
```
> If you type `Yugen`, you'll see:
```
You typed: Yugen
```

---

## 📦 Destructuring from `e.target`

We can use object destructuring to grab values from `e.target` more cleanly.

### ✨ Example:
```jsx
function Example() {
  const handleChange = (e) => {
    const { name, value } = e.target;
    console.log(name, value);
  };

  return <input type="text" name="firstName" onChange={handleChange} />;
}
```
> This will log:
```
firstName Yugen
```

---

## 🧩 Full Example: Dynamic Form

```jsx
import { useState } from "react";

export default function App() {
  const [data, setData] = useState({
    name: "",
    roll: "",
    subject: "",
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setData((prevData) => ({
      ...prevData,
      [name]: value,
    }));
  };

  return (
    <div>
      <input name="name" placeholder="Name" onChange={handleChange} />
      <input name="roll" placeholder="Roll Number" onChange={handleChange} />
      <input name="subject" placeholder="Subject" onChange={handleChange} />
      <p>{data.name}, {data.roll}, {data.subject}</p>
    </div>
  );
}
```

> This is a reusable `handleChange` function. It works with **multiple inputs** using their `name` attribute.

---

## 📌 Summary Table

| Term              | Meaning                                              |
|-------------------|------------------------------------------------------|
| `e`               | Event object passed to your handler                  |
| `e.target`        | The element where the event happened                 |
| `e.target.value`  | The value typed inside the input                    |
| `e.target.name`   | The name of the input (must be given in JSX)         |
| `setData({...})`  | Updates the component’s state in React               |

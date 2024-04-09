# Login Form Example
```javascript
import React from "react";

export default function Form() {
  const [formData, setFormData] = React.useState({
    email: "",
    password: "",
    confirmPassword: "",
    isSubscribed: false,
  });

  function handleChange(event) {
    const { name, value, type, checked } = event.target;
    setFormData((prevFormData) => {
      return {
        ...prevFormData,
        [name]: type === "checkbox" ? checked : value,
      };
    });
  }

  function handleSubmit(event) {
    event.preventDefault();
    if (formData.password === formData.confirmPassword) {
      console.log("Successfully signed up");
    } else {
      console.log("Password not match");
    }
    if (formData.isSubscribed){
      console.log("Thanks your subscribing in the newsletter")
    }
  }

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="email"
        name="email"
        value={formData.email}
        placeholder="Enter your email"
        onChange={handleChange}
      />
      <br />
      <input
        type="password"
        name="password"
        value={formData.password}
        placeholder="Enter your password"
        onChange={handleChange}
      />
      <br />
      <input
        type="password"
        name="confirmPassword"
        value={formData.confirmPassword}
        placeholder="Confirm Password"
        onChange={handleChange}
      />
      <br />
      <input
        type="checkbox"
        name="isSubscribed"
        checked={formData.isSubsribed}
        onChange={handleChange}
        id="subsribe"
      />
      <label htmlFor="subscribe">I want to join the newsletter</label>
      <br />
      <br />
      <button>Sign Up</button>
    </form>
  );
}
```
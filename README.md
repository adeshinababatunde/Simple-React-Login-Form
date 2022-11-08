# Simple-React-Login-Form

import React,{useState} from "react";

// Use functional or class component based on your preference.
// Make it a default export.

export default function LoginForm({ onSubmit }) {
  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");

    const validate = () => {
      return username.length & password.length;
    }


    const submitHandler = e => {
      e.preventDefault();
      onSubmit(username,password)
    }
  return (
    <div>
      <form onSubmit={submitHandler}>
        <input type="text" id="username-input" name="username" value={username} onChange={(e) =>setUsername(e.target.value)} />
         <input id="password-input" type="password" name="password" value={password} onChange={(e) => setPassword(e.target.value)} />
         <button id="login-button" type="submit" disabled={!validate()} name="submit" />
      </form>
  </div>);
}

function App() {

  const onSubmit= data => {
    console.log(data)
  }
  return(
    <LoginForm onSubmit={onSubmit} />
  )
}

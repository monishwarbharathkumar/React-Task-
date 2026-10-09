import React, { useState } from "react";
import "./App.css";

const initialForm = {
  name: "",
  email: "",
  password: "",
};

function TextInput({ label, name, type = "text", value, onChange, error }) {
  return (
    <div className="field">
      <label>{label}</label>
      <input
        type={type}
        name={name}
        value={value}
        onChange={onChange}
        placeholder={`Enter ${label.toLowerCase()}`}
      />
      {error && <small>{error}</small>}
    </div>
  );
}

function App() {
  const [form, setForm] = useState(initialForm);
  const [submitted, setSubmitted] = useState(null);

  const errors = {
    name: !form.name.trim() ? "Name is required" : "",
    email: !form.email.trim()
      ? "Email is required"
      : !/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.email)
      ? "Enter a valid email"
      : "",
    password: !form.password ? "Password is required" : "",
  };

  const isValid = !Object.values(errors).some(Boolean);

  const handleChange = (e) => {
    setForm({
      ...form,
      [e.target.name]: e.target.value,
    });
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    if (!isValid) return;

    setSubmitted(form);
  };

  const handleClear = () => {
    setForm(initialForm);
    setSubmitted(null);
  };

  return (
    <div className="container">
      <h1>Signup Form</h1>

      <form onSubmit={handleSubmit}>
        <TextInput
          label="Name"
          name="name"
          value={form.name}
          onChange={handleChange}
          error={errors.name}
        />

        <TextInput
          label="Email"
          name="email"
          type="email"
          value={form.email}
          onChange={handleChange}
          error={errors.email}
        />

        <TextInput
          label="Password"
          name="password"
          type="password"
          value={form.password}
          onChange={handleChange}
          error={errors.password}
        />

        <button type="submit" disabled={!isValid}>
          Sign Up
        </button>

        <button type="button" onClick={handleClear}>
          Clear
        </button>
      </form>

      {submitted && (
        <div className="preview">
          <h2>Submitted Data</h2>
          <p><strong>Name:</strong> {submitted.name}</p>
          <p><strong>Email:</strong> {submitted.email}</p>
          <p><strong>Password:</strong> {submitted.password}</p>
        </div>
      )}
    </div>
  );
}

export default App;

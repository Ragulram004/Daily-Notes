### Day 7: Forms and Controlled Components

Welcome to Day 7 of our #30daysofMERNstack series! Today, we're going to learn how to create and manage forms in React using controlled components. By the end of this lesson, you'll know how to create forms and manage their state effectively.

#### Creating Forms in React

Forms are essential for collecting user input. In React, forms can be created using standard HTML form elements. However, managing their state requires a different approach.

**Example: Simple Form**:

```jsx
import React, { useState } from 'react';

function SimpleForm() {
  const [input, setInput] = useState('');

  const handleChange = (e) => {
    setInput(e.target.value);
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Submitted: ${input}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" value={input} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}

export default SimpleForm;
```

In this example:
- We use `useState` to manage the `input` state.
- The `handleChange` function updates the `input` state with the input value.
- The `handleSubmit` function prevents the default form submission behavior and displays an alert with the submitted input.

#### Controlled Components

In React, controlled components are form elements that derive their value from the component's state. This makes it easy to manage and validate user input.

**Example: Controlled Input**:

```jsx
import React, { useState } from 'react';

function ControlledInput() {
  const [name, setName] = useState('');

  const handleChange = (e) => {
    setName(e.target.value);
  };

  return (
    <div>
      <input type="text" value={name} onChange={handleChange} />
      <p>Your name is: {name}</p>
    </div>
  );
}

export default ControlledInput;
```

In this example:
- We use `useState` to manage the `name` state.
- The `handleChange` function updates the `name` state with the input value.
- The input value is controlled by the `name` state.

#### Managing Form State with Multiple Inputs

When dealing with forms that have multiple inputs, you can manage their state using a single state object.

**Example: Form with Multiple Inputs**:

```jsx
import React, { useState } from 'react';

function MultiInputForm() {
  const [formData, setFormData] = useState({ name: '', email: '' });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData({ ...formData, [name]: value });
  };

  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Submitted: ${formData.name}, ${formData.email}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" name="name" value={formData.name} onChange={handleChange} />
      <input type="email" name="email" value

={formData.email} onChange={handleChange} />
      <button type="submit">Submit</button>
    </form>
  );
}

export default MultiInputForm;
```

In this example:
- We use `useState` to manage the `formData` state object.
- The `handleChange` function updates the `formData` state with the input values.
- The form displays an alert with the submitted input values.

#### Conclusion

Today, we've learned how to create forms in React and manage their state using controlled components. Managing form state is crucial for building interactive and user-friendly forms.
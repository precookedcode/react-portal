
# @precooked/react-portal

![Precooked Logo](https://precookedcode.com/assets/logos/logo-horizontal-dark.svg)

A lightweight, customizable Portal component for React, ideal for rendering modals, tooltips, and other elements outside the main DOM hierarchy.

## Installation

Install `@precooked/react-portal` via npm:

```bash
npm install @precooked/react-portal
```

Or with Yarn:

```bash
yarn add @precooked/react-portal
```

## Usage

The `Portal` component renders its children to a DOM node outside of the main document flow, typically `document.body`. This helps with UI elements that need to overlay or avoid conflicts with the rest of the content.

### Importing

```typescript
import Portal from '@precooked/react-portal';
```

### Props

| Prop       | Type               | Default         | Description                                                |
|------------|--------------------|-----------------|------------------------------------------------------------|
| `children` | `React.ReactNode`  | **Required**    | The elements to be rendered inside the portal.             |

### Example

Here's an example of using `Portal` to render a simple modal component outside of the main DOM hierarchy:

```typescript
import React from 'react';
import Portal from '@precooked/react-portal';

const MyModal: React.FC<{ isOpen: boolean; onClose: () => void }> = ({ isOpen, onClose }) => {
  if (!isOpen) return null;

  return (
    <Portal>
      <div style={modalStyles}>
        <h2>My Modal</h2>
        <button onClick={onClose}>Close</button>
      </div>
    </Portal>
  );
};

// Usage in a component
const App: React.FC = () => {
  const [isOpen, setIsOpen] = React.useState(false);

  return (
    <div>
      <button onClick={() => setIsOpen(true)}>Open Modal</button>
      <MyModal isOpen={isOpen} onClose={() => setIsOpen(false)} />
    </div>
  );
};

const modalStyles = {
  position: 'fixed',
  top: '50%',
  left: '50%',
  transform: 'translate(-50%, -50%)',
  padding: '20px',
  backgroundColor: '#fff',
  boxShadow: '0px 4px 10px rgba(0, 0, 0, 0.1)',
};

export default App;
```

### License

This component is available under the [MIT License](./LICENSE).

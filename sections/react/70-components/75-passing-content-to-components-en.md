# Passing content to components

## Passing content to components

A component may receive content to be displayed via `props.children`

possible usage:

```jsx
<Notification type="error">
  <p>Changes could not be saved</p>
</Notification>
```

## Passing content to components

component definition:

```tsx
type Props = {
  type: string;
  children: React.ReactNode;
};

const Notification = (props: Props) => {
  return (
    <div
      style={{
        backgroundColor:
          props.type === 'error' ? 'salmon' : 'lightblue',
      }}
    >
      {props.children}
    </div>
  );
};
```

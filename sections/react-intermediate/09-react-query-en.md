# React Query

## React Query

**React Query**: library for interacting with web APIs (e.g. REST APIs)

## React Query Setup

in _index.js_:

```js
import {
  QueryClient,
  QueryClientProvider,
} from 'react-query';

const queryClient = new QueryClient();

ReactDOM.render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>,
  rootElement
);
```

## Writing queries

```js
import { useQuery } from 'react-query';
import { fetchTodos } from './todosApi';

function TodoApp() {
  const { isLoading, error, data: todos } = useQuery(
    ['todos'],
    fetchTodos
  );
  if (isLoading) {
    return <div>Loading ...</div>;
  } else if (error) {
    return <div>Could not load todos</div>;
  }
  return <TodoList todos={todos} />;
}
```

## Writing mutations

```js
import { useMutation, useQueryClient } from 'react-query';
import { addTodo } from './todosApi';

function TodoApp() {
  // ...
  const queryClient = useQueryClient();
  const addTodoMutation = useMutation(addTodo, {
    onSuccess: () => {
      // initiate a refetch of todos
      queryClient.invalidateQueries('todos');
    },
  });
  function onAddTodo() {
    addTodoMutation.mutate({ title: newTitle });
  }
  // ...
}
```

## Devtools

enabling a devtools popup:

```js
// index.js
import { ReactQueryDevtools } from 'react-query/devtools';

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      {/* The rest of your application */}
      <ReactQueryDevtools initialIsOpen={false} />
    </QueryClientProvider>
  );
}
```

## Exercise

Create an exchange rate app that loads data from an API like this:

_https://api.exchangerate.host/latest?base=USD&symbols=EUR_

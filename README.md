# idstm

*React store for straightforward shared state management*

Making dealing with shared state similar to React's `useState()` for local state.

## Usage

```js
import {Store, useStore} from 'idstm';
```

- Wrap up shared data into `new Store(data)`, put it into a React Context;

- Pick the store from the context with the React's `useContext()` hook from within a component;

- Read the store state and subscribe to its updates: `let [state, setState] = useStore(store);` Alternatively, use `let [state, setState] = useStore(store, false);` (with the hook's second parameter) to turn off the subscription to store state updates;

- Update the immutable store state via the mutable interface of `setState()`: `setState(draftState => { draftState.x += 5; });`

- Have as many stores as needed.

[Live demo](https://codesandbox.io/s/npu6rb)

See also [*idst*](https://www.npmjs.com/package/idst), an immutable store without the mutable interface of `setState()`.

## Package name

The package name is the initialism for *<ins>i</ins>mmutable <ins>d</ins>ata <ins>st</ins>ore with a <ins>m</ins>utable interface*.

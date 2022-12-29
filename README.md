# idstm

*<ins>I</ins>mmutable <ins>d</ins>ata <ins>st</ins>ore with a <ins>m</ins>utable interface for React apps*

## Purpose

Sharing data across React components by means of a single new hook in a fashion similar to the React's `useState()` hook for local state.

## Exports

`Store`, `useStore`.

## Usage

🔹 Wrap up shared data into `new Store(data)`, put it into a React Context;

🔹 Read and subscribe to updates in the store:
```js
const [state, setState] = useStore(store);
```

Call `useStore(store, false)` to get `[state, setState]` without subscribing to updates in the store.

🔹 Update the immutable store state via the mutable interface of `setState()`:
```js
setState(draftState => { draftState.x += 5; });
```

🔹 Have as many stores as needed.

---

[Live example](https://codesandbox.io/s/npu6rb)

See also [*idst*](https://www.npmjs.com/package/idst), an immutable store without the mutable interface of `setState()`.

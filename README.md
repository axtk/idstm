# idstm

*<ins>I</ins>mmutable <ins>d</ins>ata <ins>st</ins>ore with a <ins>m</ins>utable interface for React apps*

## Purpose

Using data shared across React components in a simple way similar to React's `useState()`.

## Usage

🔹 Wrap up shared data into `new Store(data)` imported from this package, put it into a React Context;

🔹 Read and subscribe to updates in the store:

```js
import {useStore} from 'idstm';

let [state, setState] = useStore(store);
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

# idstm

*<ins>I</ins>mmutable <ins>d</ins>ata <ins>st</ins>ore with a <ins>m</ins>utable interface for React apps*

🔹 Wrap up shared data into `new Store(data)`, put it into a React Context;

🔹 Read and subscribe to updates in the store:
```js
const [state, setState] = useStore(store);
```

🔹 Update the immutable store state via the mutable interface of `setState()`:
```js
setState(draftState => { draftState.x += 5; });
```

🔹 Have as many stores as needed.

See also [*idst*](https://www.npmjs.com/package/idst).

## Example

```jsx
import {createContext} from 'react';
import {Store} from 'idstm';

export const AppContext = createContext(new Store({counter: 0}));
```

```jsx
import {useContext} from 'react';
import {useStore} from 'idstm';

export const Display = () => {
    const store = useContext(AppContext);
    const [state] = useStore(store);

    return <span>{state.counter}</span>;
};
```

```jsx
import {useContext} from 'react';
import {useStore} from 'idstm';

export const PlusButton = () => {
    const store = useContext(AppContext);
    // adding `false` to turn off the subscription to changes here
    const [, setState] = useStore(store, false);

    const handleClick = () => {
        // `draftState` acts like a mutable for convenience and passes
        // the updates to the immutable store state under the hood
        setState(draftState => {
            draftState.counter++;
        });
    };

    return <button onClick={handleClick}>+</button>;
};
```

```jsx
import {createRoot} from 'react-dom/client';
import {Store} from 'idstm';

const App = () => <div><PlusButton/> <Display/></div>;

createRoot(document.querySelector('#app')).render(
    <AppContext.Provider value={new Store({counter: 42})}>
        <App/>
    </AppContext.Provider>
);
```

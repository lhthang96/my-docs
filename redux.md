# STORE MANAGEMENT BY REDUX

## Tips

### Using with TypeScript

When using with TypeScript, u might need to get the type of state of all reducers, with `combineReducer` API, u can get a rootReducer type as the following piece of code:

```
import { createStore, combineReducer } from 'redux';
import { useSelector, useDispatch, TypedUseSelectorHook } from 'react-redux';
import { reducerA, reducerB } from './reducer';

const rootReducer = combineReducer({
  reducerA,
  reducerB,
});

export const store = createStore(rootReducer);
export const RootState = ReturnType<typeof rootReducer>;

// Hooks
export const useStoreSelector: TypedUseSelectorHook<RootState> = useSelector;
export const useStoreDispatch = useDispatch
```

### Reset store to initial states

**Ref:** https://stackoverflow.com/questions/35622588/how-to-reset-the-state-of-a-redux-store

**Ref:** https://redux.js.org/recipes/structuring-reducers/initializing-state

Redux specify one of the two main ways to initilize state is setting reducer state to undefined. Combining the codes above, now we have:

```
import { createStore, combineReducer } from 'redux';
import { useSelector, useDispatch, TypedUseSelectorHook } from 'react-redux';
import { reducerA, reducerB } from './reducer';

const appReducer = combineReducer({
  reducerA,
  reducerB,
});

const rootActionTypes = {
  SIGNED_OUT: 'SIGNED_OUT'
}
const rootReducer = (state, action) {
  if (action.type === rootActionTypes.SIGNED_OUT) {
    // Dont forget to remove redux-persist state if it was existed
    state = undefined;
  }

  return appReducer(state, action);
}

export const store = createStore(rootReducer);
export const RootState = ReturnType<typeof rootReducer>;

// Hooks
export const useStoreSelector: TypedUseSelectorHook<RootState> = useSelector;
export const useStoreDispatch = useDispatch
```

> **Tip:** Useful when we need to reset store after user signed out

> **Note:** In case u are using redux-persist, don't forget to remove persisted state which is stored in `storage` (usually `local storage` on web and `async storage` on mobile apps).

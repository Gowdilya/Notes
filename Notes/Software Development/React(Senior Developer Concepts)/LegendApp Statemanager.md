#library #react 
https://legendapp.com/open-source/state/
https://www.youtube.com/watch?v=E4TH77SMOG8
### [1. 🦄 As easy as possible to use](https://legendapp.com/open-source/state/#1--as-easy-as-possible-to-use)

There is no boilerplate and there are no contexts, actions, reducers, dispatchers, sagas, thunks, or epics. It doesn't modify your data at all, and you can just call `get()` to get the raw data and `set()` to change it.

In React components you can call `use()` on any observable to get the raw data and automatically re-render whenever it changes.


```jsx
// Create an observable object
const state$ = observable({ settings: { theme: 'dark' } })

// Just get and set
const theme = state$.settings.theme.get();
state$.settings.theme.set('light')

// observe re-runs when accessed observables change
observe(() => {
    console.log(state.settings.theme.get())
})

const Component = function Component() {
    // use() makes this component re-render whenever it changes
    const theme = state$.settings.theme.use()

    return <div>Theme: {theme}</div>
}```


### [2. ⚡️ The fastest React state library](https://legendapp.com/open-source/state/#2-%EF%B8%8F-the-fastest-react-state-library)

Legend-State beats every other state library on just about every metric and is so optimized for arrays that it even beats vanilla JS on the "swap" and "replace all rows" benchmarks. At only `4kb` and with the massive reduction in boilerplate code, you'll have big savings in file size too.![[Screenshot 2023-08-20 at 8.16.25 PM.png]]

### [3. 🔥 Fine-grained reactivity for minimal renders](https://legendapp.com/open-source/state/#3--fine-grained-reactivity-for-minimal-renders)

Legend-State lets you make your renders super fine-grained, so your apps will be much faster because React has to do less work. The best way to be fast is to render less, less often.


```jsx
function Normal() {
    const [count, setCount] = useState(0);

    useInterval(() => {
        setCount(v => v + 1)
    }, 600)

    // This re-renders when count changes
    return (
        <div>
            Count: {count}
        </div>
    )
}
function FineGrained() {
    const count$ = useObservable(0)

    useInterval(() => {
        count$.set(v => v + 1)
    }, 600)

    // The text updates itself so the component doesn't re-render
    return (
        <div>
            Count: <Memo>{count$}</Memo>
        </div>
    )
}
```

### [4. 💾 Powerful persistence](https://legendapp.com/open-source/state/#4--powerful-persistence)

Legend-State includes a powerful persistence plugin system for local caching and remote sync. It easily enables offline-first apps by tracking changes made while offline that save when coming online, managing conflict resolution, and syncing only small diffs. We use Legend-State as the sync systems in [Legend](https://legendapp.com/) and [Bravely](https://bravely.io/), so it is by necessity very full featured while being simple to set up.

Local persistence plugins for the browser and React Native are included, and a remote sync plugin for Firebase will be ready soon.

```js
import { ObservablePersistLocalStorage } from '@legendapp/state/persist-plugins/local-storage'
import { persistObservable } from '@legendapp/state/persist'

const state$ = observable({ store: { bigObject: { ... } } })

// Persist this observable
persistObservable(state$, {
    persistLocal: ObservablePersistLocalStorage,
    local: 'store' // Unique name
})
```
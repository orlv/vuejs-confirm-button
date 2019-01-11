# vuejs-confirm-button

Vue button component

#### Installation

```
npm i -D vuejs-confirm-button
```


#### Example

```
<confirm-button :text="'Drop DB'"
                :confirm="'Are you sure?'"
                :callback="() => myMethod()"
                :main-style="main-style"
                :busy-style="busy"
                :idle-style="idle"/>
```

props 'main-style', 'busy-style' and 'idle-style' are optional

```
import ConfirmButton from 'vuejs-confirm-button'
```

```
components: {
    ConfirmButton
}

methods: {
  myMethod: function () {
    // ...
  }
}
```

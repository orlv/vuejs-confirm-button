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
                :main-style="'main-style'"
                :confirm-style="'confirm-style'"
                :busy-style="'busy-style'"
                :idle-style="'idle-style'"/>
```

props 'main-style', 'confirm-style', 'busy-style' and 'idle-style' are optional

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

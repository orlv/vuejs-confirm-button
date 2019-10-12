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
                :idle-style="'idle-style'"
                :confirm-timeout="2000"
                :busy-timeout="5000"/>
```

props 'main-style', 'confirm-style', 'busy-style', 'idle-style', 'confirm-timeout' and 'busy-timeout' are optional

```
import ConfirmButton from 'vuejs-confirm-button'
```

```
components: {
    ConfirmButton
}

methods: {
  myMethod () {
    // ...
  }
}
```

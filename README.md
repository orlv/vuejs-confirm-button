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
                :callback="() => myMethod()"/>
```

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

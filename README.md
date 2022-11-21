# lite-json-editor (Vue 3)

A lightweight minimalistic json formatter/editor for Vue 3

## Install

### Vue 3
```sh
npm i lite-json-editor
```

#### Usage
```vue
<script setup>
    import { ref } from 'vue'
    import LiteJsonEditor from 'lite-json-editor'

    const value = ref()
</script>

<template>
    <LiteJsonEditor v-model="value" />
</template>
```

#### Props

| Name         | Description             | Type                       | Default |
| ------------ | ----------------------- | -------------------------- | ------- |
| v-model      | binding value           | `Object`, `String`, `null` |         |
| indent       | json indent             | `Number`                   | 3       |
| dark         | dark mode               | `Boolean`                  | false   |
| withoutEdit  | disable editing         | `Boolean`                  | false   |
| withoutError | disable error trigger   | `Boolean`                  | false   |
| formatting   | color formatting        | `Object`                   |         |

#### Slots

This component provides a slot if you need to modify the error display behavior

```vue
<template>
    <LiteJsonEditor v-model="value">
        <img src="/example-error-icon.svg" />
    </LiteJsonEditor>
</template>
```

#### Formatting

Default colors are

- ![#a9dc76](https://via.placeholder.com/15/a9dc76/a9dc76.png) `#a9dc76` - number
- ![#84aecc](https://via.placeholder.com/15/84aecc/84aecc.png) `#84aecc` - braces
- ![#d26a6a](https://via.placeholder.com/15/d26a6a/d26a6a.png) `#d26a6a` - brackets
- ![#4f4f4f](https://via.placeholder.com/15/4f4f4f/4f4f4f.png) `#4f4f4f` - colon
- ![#f8c33b](https://via.placeholder.com/15/f8c33b/f8c33b.png) `#f8c33b` - comma
- ![#5f9fca](https://via.placeholder.com/15/5f9fca/5f9fca.png) `#5f9fca` - string
- ![#e393ff](https://via.placeholder.com/15/e393ff/e393ff.png) `#e393ff` - string_quotes
- ![#ff6188](https://via.placeholder.com/15/ff6188/ff6188.png) `#ff6188` - key
- ![#fc9867](https://via.placeholder.com/15/fc9867/fc9867.png) `#fc9867` - key_quotes
- ![#cccccc](https://via.placeholder.com/15/cccccc/cccccc.png) `#cccccc` - null
- ![#8ccf79](https://via.placeholder.com/15/8ccf79/8ccf79.png) `#8ccf79` - true
- ![#e69fc2](https://via.placeholder.com/15/e69fc2/e69fc2.png) `#e69fc2` - false

If you want to modify any of those values pass a formatting object containing `key: color` pairs of your desired changes

```vue
<template>
    <LiteJsonEditor v-model="value" :formatting="{ 'number': '#e3e3e3' }" />
</template>
```

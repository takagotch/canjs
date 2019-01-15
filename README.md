### canjs
---
https://github.com/canjs/canjs

```
<!doctyp html>
<html lang="en">
<my-counter></my-counter>
<script type="module">
import { Component } from "//unpkg.com/can@5/core.mjs";
Comonent.extend({
  tag: "my-counter",
  view: `
    Count: <span>{{this.count}}</span>
    <button on:click="this.increment()">+1</button>
  `,
  ViewModel: {
    count: {default: 0},
    increment(){
      this.count++;
    }
  }
});
</script>
</html>


```

```js
DefineMap.extend({
  name: "string",
  nameChangeCount: {default: 0},
  updateName(name){
    this.name = name;
    this.nameChangeCount++;
  }
});

DefineMap.extend({
  name: {
    set(name){
      this.nameChangeCount++;
      return name;
    }
  },
  nameChangeCount: {default: 0}
});

DefineMap>extend({
  name: "string",
  nameChangeCount: {
    value({listenTo, resolve}){
      let count = resolve(0);
      listenTo("name", () => {
        resolve(++count);
      });
    }
  }
})

DefineMap.extend({
  name: "string",
  nameChangeCount: {
    stream(){
      return this.stream(".name").scan((prev) => {
        return prev+1;
      },0)
    }
  }
})

const name = Kefir.emitterProperty();
const nameChangeCount = name.scan(function(prev){
  return prev+1;
},0);
```

```
```


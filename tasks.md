```js
function flatten(arr) {
  const res = [];

  move(arr);

  return res;
  
  function move(arr) {
    for (let i = 0; i < arr.length; i++) {
      if (Array.isArray(arr[i])) {
        move(arr[i]);
      } else {
        res.push(arr[i]);
      }
    }
  }
}

console.info('res :', flatten([2, [3, [5]], [33]]));
// [2,3,5,33]
```

The same function without inner function. To do it you should use 
conditional param
```js
function flatten(arr, res) {
  const r = res ? res : [];
  for (let i = 0; i < arr.length; i++) {
    if (Array.isArray(arr[i])) {
      flatten(arr[i], r);
    } else {
      r.push(arr[i]);
    }
  }

  return r;
}
```

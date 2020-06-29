```js
const injector = {
  dependencies: {},
  register: function(key, value) {
    this.dependencies[key] = value;
  },
  resolve: function(func, scope) {
    const args = [];
    const self = this;
    const deps = func.toString()
      .match(/^function\s*[^\(]*\(\s*([^\)]*)\)/m)[1].replace(/ /g, '').split(',');
    // deps array: ["service", "router", "other"]

    return function() {
      const a = Array.prototype.slice.call(arguments, 0);
      // returns real Array for arguments (initially arguments are an array likxe object)
      deps.forEach((depKey) => {
        const dep = self.dependencies[depKey];
        args.push(dep && depKey!= '' ? dep : a.shift())
        // shift sequentially returns not dependency arguments 
        // 'other-name' is not a dependency; it will be recognised as
        // first params that doesn't have a dep, other in our case
      })

      func.apply(scope || {}, args);
    }
  }
}

injector.register('service', function () {
  return {
    name: 'service-name'
  };
});

injector.register('router', function() {
  return {
    name: 'router-name'
  };
})

const doOther = injector.resolve(
  function(service, router, other) {
    console.info(service().name);
    console.info(router().name);
    console.info(other);
  }
);

doOther('other-name');
/*
service-name
router-name
other-name
*/
```

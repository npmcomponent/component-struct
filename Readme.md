*This repository is a mirror of the [component](http://component.io) module [component/struct](http://github.com/component/struct). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/component-struct`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*

# struct

  C struct style buffer views for reading and writing structures of varying types.

## Installation

    $ component install component/struct

## Example

```js
var struct = require('struct');

// buffer big enough for all 3 structs
var buf = new Uint8Array(3 * (32 + 5 + 16));

var Pet = struct({
  id: 'uint32',
  name: 'string',
  age: 'uint16'
});

// write

var tobi = new Pet({
  id: 1,
  name: 'Tobi',
  age: 2
});

var loki = new Pet({
  id: 2,
  name: 'Loki',
  age: 2
});

var jane = new Pet({
  id: 3,
  name: 'Jane',
  age: 6
});

var off = 0;
var pets = [tobi, loki, jane];
for (var i = 0; i < pets.length; i++) {
  off = pets[i].write(buf, off);
}

// read

var n = 3;
var off = 0;
var pet = new Pet;
while (n--) {
  off = pet.read(buf, off);
  console.log('%s (%s) is %s years old', pet.name, pet.id, pet.age);
}
```

## API

  ...

## License

  MIT

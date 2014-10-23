
# ember-template-compiler

An npm module for the `ember-template-compiler.js` file that ships with ember.js


## What can I do with this?

If you have a client build process and need to compile handlebars templates for ember.js

```no-highlight
npm install ember-template-compiler
```

```js
var compiler = require('ember-template-compiler');
var template = fs.readFileSync('foo.handlebars').toString();
var input = compiler.precompile(template).toString();
var output = "Ember.TEMPLATES['foo'] = Ember.Handlebars.template(" + input + ");";
```

Additionally you can pass a second argument into `precompile` which will build the precompiled template as an object (`true` or `undefined`) or as a string (`false`).  Building as a string is more efficient than building as an object then converting it to a string. 

```js
var input = compiler.precompile(template, false);
var output = "Ember.TEMPLATES['foo'] = Ember.Handlebars.template(" + input + ");";
```


## Handlebars Version

This package will only work with Handlebars 2.0 and greater.

### Upgrading from 1.x

When upgrading to 2.0, to get the same result as previously, you must specify the second argument to `precompile`,
i.e `precompile(template, false)` which will return a string, which is the old behavior.


## Development

To run the tests you must have the following node packages installed: `jasmine-node`, and `handlebars`.  Then run

```no-highlight
npm test
```


## License

Copyright © 2013 Toran Billups

Licensed under the MIT License

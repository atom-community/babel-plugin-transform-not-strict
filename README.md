# babel-plugin-transform-not-strict

Remove 'use strict' if the file is 'not strict'

Most of the bundlers and transpilers such as babel add `'use strict'` to the above of your file. This plugin will remove them if you add `'not strict'` to that file. You can also use this plugin to remove `'use strict'` from all the files

## Installation

```
npm install --save-dev babel-plugin-transform-not-strict
```

You should also install the peer dependencies:

```
npm install -save-dev "@babel/core"
```

## Usage

1. put the following in above the a file that is not strict:

```js
"not strict";

```

2. Add `"babel-plugin-transform-not-strict"` to the list of your babel plugins.

For example, create a `babel.config.js` file at the root of the project with the following content:

```js
let presets = [];

let plugins = ["babel-plugin-transform-not-strict"];

module.exports = {
  presets: presets,
  plugins: plugins,
  exclude: "node_modules/**",
  sourceMap: "inline",
};
```

### Usage Remove All

You can also use this plugin to remove `'use strict'` from all the files. Just pass `removeAll: true`.

```js
let presets = [];

let plugins = [
  [
    "babel-plugin-transform-not-strict",
    {
      removeAll: true,
    },
  ],
];

module.exports = {
  presets: presets,
  plugins: plugins,
  exclude: "node_modules/**",
  sourceMap: "inline",
};
```

### Usage Extra Directive or Comment Triggers

You can add more directive or comment triggers for removal of `'use strict'`. In the following example, `'use babel'` directive or comments that include `'@babel'` or `'@flow'` also instruct the plugin to become active and remove `'use strict'`

```js
let presets = [];

let plugins = [
  [
    "babel-plugin-transform-not-strict",
    {
      directiveTriggers: ["use babel"],
      commentTriggers: ["@babel", "@flow", "* @babel", "* @flow"],
    },
  ],
];

module.exports = {
  presets: presets,
  plugins: plugins,
  exclude: "node_modules/**",
  sourceMap: "inline",
};
```

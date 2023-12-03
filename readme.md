# cannon-es-umd

This is a fork of [cannon-es](https://github.com/pmndrs/cannon-es) to make a simple UMD version of it for jsDelivr CDN.

## How To Use

CDN URL
```
https://cdn.jsdelivr.net/gh/KLA6/cannon-es-umd@v0.20.0/cannon-es.umd.js
```

HTML
```
<script src="https://cdn.jsdelivr.net/gh/KLA6/cannon-es-umd@v0.20.0/cannon-es.umd.js"></script>
```

Web Worker
```
importScripts( 'https://cdn.jsdelivr.net/gh/KLA6/cannon-es-umd@v0.20.0/cannon-es.umd.js' )
```

## How It Was Made

Instal Webpack.
```
npm install --save-dev webpack webpack-cli
```

Make `webpack.config.js`.
```
const path = require('path');

module.exports = {
  entry          : './cannon-es.js'                 , // Source File in ESM
  output         : {
    path         : path.resolve( __dirname, 'dist' ), // Result Dir
    filename     : 'cannon-es.umd.js'               , // Result File
    library      : 'CANNON'                         , // Global Var
    libraryTarget: 'umd'                            ,
    globalObject : 'this'
  },
  module: { rules: [ { test   : /\.js$/       ,
                       use    : 'babel-loader',
                       exclude: /node_modules/ } ] }
};
```

Install Babel.
```
npm install --save-dev babel-loader @babel/core @babel/preset-env
```

Make `.babelrc`.
```
{
  "presets": ["@babel/preset-env"]
}
```

Build Webpack.
```
npx webpack
```

## Note

I don't know why, but using this induces higher CPU consuming than using the original Cannon.js.

CDN URL of Original Cannon.js
```
https://cdnjs.cloudflare.com/ajax/libs/cannon.js/0.6.2/cannon.min.js
```

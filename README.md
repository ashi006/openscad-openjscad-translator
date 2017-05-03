## openscad-openjscad-translator

## OpenSCAD to OpenJSCAD Translator

> Translates OpenSCAD syntax into OpenJsCAD syntax

## Overview

Node module that translates OpenSCAD syntax (http://www.openscad.org/) into OpenJsCAD syntax (http://joostn.github.com/OpenJsCad/).

**_IMPORTANT NOTE:_ This project is written against an older version of OpenSCAD (v 2011.06) which has now been superseded.**

## Table of Contents

- [Installation](#install)
- [Usage](#usage)
- [Build](#build)
- [Contribute](#contribute)
- [License](#license)

## Install

```
npm install @jscad/openscad-openjscad-translator
```

>NOTE: for now we need to use a temporary build of the sylvester (node-sylvester)
library since the one on NPM has a missing flag which makes use with browserify impossible:
see : [here](https://github.com/NaturalNode/node-sylvester/issues/9) and [here](https://github.com/NaturalNode/node-sylvester/issues/4)

## Usage

### Node

```javascript
  var parser = require('openscad-openjscad-translator')
  var fs = require('fs')

  var openSCADText = fs.readFileSync("test.scad", "UTF8")
  var openJSCADResult = parser.parse(openSCADText)

  console.log(openJSCADResult)
```

### Web

```html
  <script src="../dist/web-built.js"></script>

  <script type="text/javascript">
    var text = document.getElementById('txt').innerText
    console.log(openscadOpenJscadParser.parse(text))
  </script>
```

Include ```lib/underscore.js``` and ```dist/web-built.js``` and the **openscadOpenJscadParser** object will be available.  This has two attributes:
* **parse** - a function which accepts OpenSCAD text and returns OpenJsCAD text.
* **parser** - a Jison parser object which can be used for more advanced parsing (e.g. the **parse** method returns the text and the context object, allowing for processing of *use* statements.)

## Build

### Web

not minified :
```
npm run build
```
minified:
```
npm run build-min
```
Creates scripts in the ```dist``` folder.

## Develop

### Jison

```
npm run build-parser
```
Compiles the Jison lexer/parser to an AMD module in the ```src``` folder called ```openscad-parser.js```.

## Contribute

Pull Requests are accepted.

Please see the guidelines [here](https://github.com/jscad/openscad-openjscad-translator/blob/master/CONTRIBUTING.md)

Small Note: If editing this README, please conform to the [standard-readme](https://github.com/RichardLitt/standard-readme) specification.

## License

[The MIT License (MIT)](https://github.com/jscad/csg.js/blob/master/LICENSE)
(unless specified otherwise)

_NOTE: OpenSCAD and OpenSCAD API are released under the General Public License version 2._

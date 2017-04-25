# npmdoc-apidoc

#### basic api documentation for  [apidoc (v0.17.5)](http://apidocjs.com)  [![npm package](https://img.shields.io/npm/v/npmdoc-apidoc.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-apidoc) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-apidoc.svg)](https://travis-ci.org/npmdoc/node-npmdoc-apidoc)

#### RESTful web API Documentation Generator

[![NPM](https://nodei.co/npm/apidoc.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/apidoc)

- [https://npmdoc.github.io/node-npmdoc-apidoc/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-apidoc/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-apidoc/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Peter Rottmann"
    },
    "bin": {
        "apidoc": "bin/apidoc"
    },
    "bugs": {
        "url": "https://github.com/apidoc/apidoc/issues"
    },
    "dependencies": {
        "apidoc-core": "~0.8.1",
        "fs-extra": "~2.0.0",
        "lodash": "~4.17.4",
        "markdown-it": "^8.2.2",
        "nomnom": "~1.8.1",
        "winston": "~2.3.1"
    },
    "description": "RESTful web API Documentation Generator",
    "devDependencies": {
        "apidoc-example": "*",
        "jshint": "^2.9.4",
        "lodash-cli": "^4.17.4",
        "mocha": "~3.2.0",
        "npm-check-updates": "^2.8.9",
        "path-to-regexp": "^1.7.0",
        "semver": "^5.3.0",
        "should": "~11.1.2",
        "webfontloader": "^1.6.27"
    },
    "directories": {},
    "dist": {
        "shasum": "91ce7264b48c717e4cc18afba642277bc68a2325",
        "tarball": "https://registry.npmjs.org/apidoc/-/apidoc-0.17.5.tgz"
    },
    "engines": {
        "node": ">= 0.10.0"
    },
    "gitHead": "48b388c7a0fdf2a5137d1992836a3e30821bec46",
    "homepage": "http://apidocjs.com",
    "jshintConfig": {
        "camelcase": true,
        "curly": false,
        "eqeqeq": true,
        "forin": true,
        "latedef": false,
        "newcap": true,
        "undef": true,
        "unused": true,
        "trailing": true,
        "node": true,
        "browser": true,
        "predef": [
            "it",
            "describe",
            "before",
            "after"
        ]
    },
    "keywords": [
        "api",
        "apidoc",
        "doc",
        "documentation",
        "rest",
        "restful"
    ],
    "license": "MIT",
    "main": "./lib/index.js",
    "maintainers": [
        {
            "name": "apidoc"
        }
    ],
    "name": "apidoc",
    "optionalDependencies": {},
    "preferGlobal": true,
    "repository": {
        "type": "git",
        "url": "git+https://github.com/apidoc/apidoc.git"
    },
    "scripts": {
        "build-example": "bin/apidoc -i example/ -o tmp/",
        "check-updates": "npm-check-updates",
        "jshint": "jshint lib/ test/",
        "test": "npm run jshint && mocha test/",
        "update-lodash": "./node_modules/lodash-cli/bin/lodash -p -o template/vendor/lodash.custom.min.js include=groupBy,each,extend,some exports=amd"
    },
    "version": "0.17.5"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

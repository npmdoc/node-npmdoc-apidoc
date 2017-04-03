# api documentation for  [apidoc (v0.17.5)](http://apidocjs.com)  [![npm package](https://img.shields.io/npm/v/npmdoc-apidoc.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-apidoc) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-apidoc.svg)](https://travis-ci.org/npmdoc/node-npmdoc-apidoc)
#### RESTful web API Documentation Generator

[![NPM](https://nodei.co/npm/apidoc.png?downloads=true)](https://www.npmjs.com/package/apidoc)

[![apidoc](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-apidoc_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-apidoc/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-apidoc/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Peter Rottmann",
        "email": "rottmann@inveris.de"
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
            "name": "apidoc",
            "email": "info@apidocjs.com"
        }
    ],
    "name": "apidoc",
    "optionalDependencies": {},
    "preferGlobal": true,
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module apidoc](#apidoc.module.apidoc)
1.  [function <span class="apidocSignatureSpan">apidoc.</span>createDoc (options)](#apidoc.element.apidoc.createDoc)
1.  [function <span class="apidocSignatureSpan">apidoc.</span>package_info (_app)](#apidoc.element.apidoc.package_info)
1.  object <span class="apidocSignatureSpan">apidoc.</span>package_info.prototype

#### [module apidoc.package_info](#apidoc.module.apidoc.package_info)
1.  [function <span class="apidocSignatureSpan">apidoc.</span>package_info (_app)](#apidoc.element.apidoc.package_info.package_info)

#### [module apidoc.package_info.prototype](#apidoc.module.apidoc.package_info.prototype)
1.  [function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_getHeaderFooter (json)](#apidoc.element.apidoc.package_info.prototype._getHeaderFooter)
1.  [function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_readPackageData (filename)](#apidoc.element.apidoc.package_info.prototype._readPackageData)
1.  [function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_resolveSrcPath ()](#apidoc.element.apidoc.package_info.prototype._resolveSrcPath)
1.  [function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>get ()](#apidoc.element.apidoc.package_info.prototype.get)



# <a name="apidoc.module.apidoc"></a>[module apidoc](#apidoc.module.apidoc)

#### <a name="apidoc.element.apidoc.createDoc"></a>[function <span class="apidocSignatureSpan">apidoc.</span>createDoc (options)](#apidoc.element.apidoc.createDoc)
- description and source-code
```javascript
function createDoc(options) {
    var api;
    var apidocPath = path.join(__dirname, '../');
    var markdownParser;
    var packageInfo;

    options = _.defaults({}, options, defaults);

    // Paths.
    options.dest     = path.join(options.dest, './');
    options.template = path.join(options.template, './');

    // Line-Ending.
    if (options.lineEnding) {
        if (options.lineEnding === 'CRLF')
            options.lineEnding = '\r\n'; // win32
        else if (options.lineEnding === 'CR')
            options.lineEnding = '\r'; // darwin
        else
            options.lineEnding = '\n'; // linux
    }

    // Options.
    app.options = options;

    // Logger.
    app.log = new (winston.Logger)({
        transports: [
            new (winston.transports.Console)({
                level      : app.options.debug ? 'debug' : app.options.verbose ? 'verbose' : 'info',
                silent     : app.options.silent,
                prettyPrint: true,
                colorize   : app.options.colorize,
                timestamp  : false
            }),
        ]
    });

    // Markdown Parser: enable / disable / use a custom parser.
    if(app.options.markdown === true) {
        markdownParser = new Markdown({
            breaks     : false,
            html       : true,
            linkify    : false,
            typographer: false
        });
    } else if(app.options.markdown !== false) {
        // Include custom Parser @see MARKDOWN.md and test/fixtures/custom_markdown_parser.js
        Markdown = require(app.options.markdown); // Overwrite default Markdown.
        markdownParser = new Markdown();
    }
    app.markdownParser = markdownParser;

    try {
        packageInfo = new PackageInfo(app);

        // generator information
        var json = JSON.parse( fs.readFileSync(apidocPath + 'package.json', 'utf8') );
        apidoc.setGeneratorInfos({
            name   : json.name,
            time   : new Date(),
            url    : json.homepage,
            version: json.version
        });
        apidoc.setLogger(app.log);
        apidoc.setMarkdownParser(markdownParser);
        apidoc.setPackageInfos(packageInfo.get());

        api = apidoc.parse(app.options);

        if (api === true) {
            app.log.info('Nothing to do.');
            return true;
        }
        if (api === false)
            return false;

        if (app.options.parse !== true)
            createOutputFiles(api);

        app.log.info('Done.');
        return api;
    } catch(e) {
        app.log.error(e.message);
        if (e.stack)
            app.log.debug(e.stack);
        return false;
    }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.apidoc.package_info"></a>[function <span class="apidocSignatureSpan">apidoc.</span>package_info (_app)](#apidoc.element.apidoc.package_info)
- description and source-code
```javascript
function PackageInfo(_app) {
    // global variables
    app = _app;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.apidoc.package_info"></a>[module apidoc.package_info](#apidoc.module.apidoc.package_info)

#### <a name="apidoc.element.apidoc.package_info.package_info"></a>[function <span class="apidocSignatureSpan">apidoc.</span>package_info (_app)](#apidoc.element.apidoc.package_info.package_info)
- description and source-code
```javascript
function PackageInfo(_app) {
    // global variables
    app = _app;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.apidoc.package_info.prototype"></a>[module apidoc.package_info.prototype](#apidoc.module.apidoc.package_info.prototype)

#### <a name="apidoc.element.apidoc.package_info.prototype._getHeaderFooter"></a>[function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_getHeaderFooter (json)](#apidoc.element.apidoc.package_info.prototype._getHeaderFooter)
- description and source-code
```javascript
_getHeaderFooter = function (json) {
    var result = {};
    var self = this;

    ['header', 'footer'].forEach(function(key) {
        if (json[key] && json[key].filename) {
//            var filename = path.join(app.options.src, json[key].filename);
            var dir = self._resolveSrcPath();
            var filename = path.join(dir, json[key].filename);

            if ( ! fs.existsSync(filename))
                filename = path.join('./', json[key].filename);

            try {
                app.log.debug('read header file: ' + filename);
                var content = fs.readFileSync(filename, 'utf8');
                result[key] = {
                    title  : json[key].title,
                    content: app.markdownParser ? app.markdownParser.render(content) : content
                };
            } catch (e) {
                throw new Error('Can not read: ' + filename + '.');
            }
        }
    });

    return result;
}
```
- example usage
```shell
...
    // apidoc.json has higher priority
    _.extend(result, apidocJson);

    // options.packageInfo overwrites packageInfo
    _.extend(result, app.options.packageInfo);

    // replace header footer with file contents
    _.extend(result, this._getHeaderFooter(result));

    if (Object.keys(apidocJson).length === 0 && ! packageJson.apidoc)
        app.log.warn('Please create an apidoc.json configuration file.');

    return result;
};
...
```

#### <a name="apidoc.element.apidoc.package_info.prototype._readPackageData"></a>[function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_readPackageData (filename)](#apidoc.element.apidoc.package_info.prototype._readPackageData)
- description and source-code
```javascript
_readPackageData = function (filename) {
    var result = {};
    var dir = this._resolveSrcPath();
    var jsonFilename = path.join(dir, filename);

    // Read from source dir
    if ( ! fs.existsSync(jsonFilename)) {
        // Read from config dir (default './')
        jsonFilename = path.join(app.options.config, filename);
    }
    if ( ! fs.existsSync(jsonFilename)) {
        app.log.debug(jsonFilename + ' not found!');
    } else {
        try {
            result = JSON.parse( fs.readFileSync(jsonFilename, 'utf8') );
            app.log.debug('read: ' + jsonFilename);
        } catch (e) {
            throw new Error('Can not read: ' + filename + ', please check the format (e.g. missing comma).');
        }
    }
    return result;
}
```
- example usage
```shell
...
/**
 * Read apidoc.json / package.json data
 */
PackageInfo.prototype.get = function() {
var result = {};

// Read package.json
var packageJson = this._readPackageData('package.json');

if (packageJson.apidoc)
    result = packageJson.apidoc;

result = _.defaults({}, result, {
    name       : packageJson.name        || '',
    version    : packageJson.version     || '0.0.0',
...
```

#### <a name="apidoc.element.apidoc.package_info.prototype._resolveSrcPath"></a>[function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>_resolveSrcPath ()](#apidoc.element.apidoc.package_info.prototype._resolveSrcPath)
- description and source-code
```javascript
_resolveSrcPath = function () {
    var dir = './';

    if (app.options.src instanceof Array) {
        if (app.options.src.length === 1) {
            dir = app.options.src[0];
        }
    } else {
        if (app.options.src) {
            dir = app.options.src;
        }
    }

    return dir;
}
```
- example usage
```shell
...
 *
 * @param {String} filename
 * @param {Object} defaults
 * @returns {Object}
 */
PackageInfo.prototype._readPackageData = function(filename) {
var result = {};
var dir = this._resolveSrcPath();
var jsonFilename = path.join(dir, filename);

// Read from source dir
if ( ! fs.existsSync(jsonFilename)) {
    // Read from config dir (default './')
    jsonFilename = path.join(app.options.config, filename);
}
...
```

#### <a name="apidoc.element.apidoc.package_info.prototype.get"></a>[function <span class="apidocSignatureSpan">apidoc.package_info.prototype.</span>get ()](#apidoc.element.apidoc.package_info.prototype.get)
- description and source-code
```javascript
get = function () {
    var result = {};

    // Read package.json
    var packageJson = this._readPackageData('package.json');

    if (packageJson.apidoc)
        result = packageJson.apidoc;

    result = _.defaults({}, result, {
        name       : packageJson.name        || '',
        version    : packageJson.version     || '0.0.0',
        description: packageJson.description || '',
    });

    // read apidoc.json (and overwrite package.json information)
    var apidocJson = this._readPackageData('apidoc.json');

    // apidoc.json has higher priority
    _.extend(result, apidocJson);

    // options.packageInfo overwrites packageInfo
    _.extend(result, app.options.packageInfo);

    // replace header footer with file contents
    _.extend(result, this._getHeaderFooter(result));

    if (Object.keys(apidocJson).length === 0 && ! packageJson.apidoc)
        app.log.warn('Please create an apidoc.json configuration file.');

    return result;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

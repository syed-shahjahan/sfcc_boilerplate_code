# SFCC Boiler Plate Code

This extension provides a Salesforce Commerce Cloud B2C BoilerPlate Code for easier development.

## Installation

SFCC Boiler Plate Code can be [installed from the Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=novacode.sfccboilerplate) or by [searching within VS Code](https://code.visualstudio.com/docs/editor/extension-gallery#_search-for-an-extension).

## Working
![Demo](https://raw.githubusercontent.com/syed-shahjahan/sfcc_boilerplate_code/master/images/preference_gif.gif)
## Release Notes

Find the release notes in CHANGELOG.md file.

## 🧩 Snippets
Below are the list of few snippets and the keywords of each one.

### 🧩 Controller Snippets

**Keyword:** `newsrv`

**Snippet:**
```
'use strict';

var server = require('server');

server.${1|get,post,use|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});

module.exports = server.exports();
```

**Keyword:** `newroute`

**Snippet:**
```
server.${1|get,post,use|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```

**Keyword:** `extsrv`

**Snippet:**
```
'use strict';

var server = require('server');
server.extend(module.superModule);

server.${1|append,prepend,append|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});

module.exports = server.exports();
```

**Keyword:** `extroute`

**Snippet:**
```
server.${1|append,prepend,replace|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```

**Keyword:** `expmodule, module.exports, mexpo`

**Snippet:**
```
module.exports = server.exports();
```
---
### 🧩 Script
**Keyword:** `expmodule, module.exports, mexpo`

**Snippet:**
```
module.exports = {
    ${1:member}
};
```
---
### 🧩 ISML


**Keyword:** sitepref

|Shortcut | Code|
-------|---------
|`sitepref`|`${dw.system.Site.getCurrent().getCustomPreferenceValue('${1}')}`|
|`globalpref`|`${'${pref}' in dw.system.System.getPreferences().getCustom() ? dw.system.System.getPreferences().getCustom()['${pref}'] : ''}`|

---
### Packages


---
### 🧩 Registry Snippet

**Keyword:** `lcr`

**Snippet:**
```
var LocalServiceRegistry = require('dw/svc/LocalServiceRegistry');
var $service = LocalServiceRegistry.createService(\$2\, {
    mockCall : function(service, params) {
        return {};
    },
    createRequest: function (service, params) {
        if (params.URL && !empty(params.URL)) {
            service.URL = params.URL;
        }
        if (params.body) {
             return params.body;
        }
        return service;
    },
    parseResponse: function (service, serviceResponse) {
        return serviceResponse;
    },
    getRequestLogMessage: function(serviceRequest) {
        return serviceRequest;
    },
    getResponseLogMessage: function(serviceResponse) {
        return serviceResponse;
    }
});
```
---
### 🧩 Javascript snippets


|Shortcut | Code|
-------|---------
|`objectCreate, objcreate, objc`|`var ${1} = Object.create(null);`|
|`object.define, objectdefine, objdef`|`Object.defineProperty(object, '${1}', {enumerable: true,value: ${2}});`|
|`object.define, objectdefine, objdef`|`Object.defineProperty(object, '${1}', {enumerable: true,value: (function () {${2}}()));`|
|`require`|`const ${1:module} = require('${1:module}');`|
|`typeof, to`|`typeof ${1:source} === '${2:undefined}'`|
|`instanceof, io`|`${1:source} instanceof ${2:Object}`|
|`oa, object.assign, objectassign`|`Object.assign({}, ${1:original}, ${2:source})`|

---

## 👋 Author
Syed Shahjahan

## © LICENSE (MIT)

See LICENSE.md in the root directory

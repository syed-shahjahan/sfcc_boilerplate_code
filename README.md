# SFCC Boiler Plate Code

This extension provides a Salesforce Commerce Cloud B2C BoilerPlate Code for easier development.

## Installation

SFCC Boiler Plate Code can be [installed from the Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=Dart-Code.dart-code) or by [searching within VS Code](https://code.visualstudio.com/docs/editor/extension-gallery#_search-for-an-extension).


## Release Notes

### 1.1.0
* Updated README.md file
### 1.0.0

Initial release, contains the following features,
* Create a new Server/Controller JS
* Extend a Server/Controller JS
* Create a New Route
* Extend a Route
* Packages
* ISML custom preferences

## Snippets
Below is a list of all available snippets and the keywords of each one.

### Controller Snippets

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
---
### ISML


**Keyword:** sitepref

**Snippet:**
```
```

|Shortcut | Code|
-------|---------
|`sitepref`|`${dw.system.Site.getCurrent().getCustomPreferenceValue('${1}')}`|
|`globalpref`|`${'${pref}' in dw.system.System.getPreferences().getCustom() ? dw.system.System.getPreferences().getCustom()['${pref}'] : ''}`|

---
### Packages


---
### Registry Snippet

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
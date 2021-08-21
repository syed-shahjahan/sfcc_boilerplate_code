## Controller

**Keyword:** newsrv

**Code:**
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

**Keyword:** newroute

**Code:**
```
server.${1|get,post,use|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```

**Keyword:** extsrv

**Code:**
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

**Keyword:** extroute

**Code:**
```
server.${1|append,prepend,replace|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```
---
## ISML


**Keyword:** sitepref

**Code:**
```
```

|Shortcut | Code|
-------|---------
|sitepref|`${dw.system.Site.getCurrent().getCustomPreferenceValue('${1}')}`|
|globalpref|`${'${pref}' in dw.system.System.getPreferences().getCustom() ? dw.system.System.getPreferences().getCustom()['${pref}'] : ''}`|

---
## Packages


---
## Registry

**Keyword:** lcr

**Code:**
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
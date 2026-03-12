# SFCC BoilerPlate
## VS Code Extension by NovaCode

---

## Overview

**SFCC BoilerPlate** is a Visual Studio Code extension designed specifically for Salesforce Commerce Cloud (SFCC) B2C developers. It provides a comprehensive collection of code snippets and boilerplate templates to accelerate development workflows by eliminating repetitive coding tasks and reducing syntax errors .

---

## Installation

### From VS Code Marketplace
1. Open Visual Studio Code
2. Navigate to **Extensions** (Ctrl+Shift+X / Cmd+Shift+X)
3. Search for **"SFCC BoilerPlate"** by NovaCode
4. Click **Install**

### Manual Installation
Download the extension directly from the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=novacode.sfccboilerplate) .

### Demo
![Demo](https://raw.githubusercontent.com/syed-shahjahan/sfcc_boilerplate_code/master/images/preference_gif.gif)
---

## Available Snippets

### 🎮 Controller Snippets

Controllers are the backbone of SFCC storefront development. These snippets help you quickly scaffold server-side JavaScript controllers.

#### `newsrv` — New Server Route
Creates a complete controller file with a single route handler.

**Usage:** Type `newsrv` and press Tab

**Generated Code:**
```javascript
'use strict';

var server = require('server');

server.${1|get,post,use|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});

module.exports = server.exports();
```

**Features:**
- Dropdown selection for HTTP methods (GET, POST, USE)
- Route path placeholder
- Response method selection with common SFCC response types
- Proper module exports structure

---

#### `newroute` — Add Route to Existing Controller
Adds a new route handler within an existing controller file.

**Usage:** Type `newroute` and press Tab

**Generated Code:**
```javascript
server.${1|get,post,use|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```

---

#### `extsrv` — Extend Super Module
Creates a controller that extends a parent module using `module.superModule`.

**Usage:** Type `extsrv` and press Tab

**Generated Code:**
```javascript
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

**Features:**
- Dropdown for extension methods (append, prepend, replace)
- Inherits functionality from parent controller

---

#### `extroute` — Extend Existing Route
Adds route extension logic to an existing extended controller.

**Usage:** Type `extroute` and press Tab

**Generated Code:**
```javascript
server.${1|append,prepend,replace|}('${2:route}', function(req, res, next) {
    ${4};
    res.${5|render,json,xml,page,redirect,getViewData,setViewData,log,print|}(${6});
    next();
});
```

---

#### `expmodule`, `module.exports`, `mexpo` — Module Export
Quickly add the standard SFCC module export statement.

**Usage:** Type any of the three keywords and press Tab

**Generated Code:**
```javascript
module.exports = server.exports();
```

---

### 📜 Script Snippets

#### Module Export for Scripts
For non-controller script files that need module exports.

**Usage:** Type `expmodule`, `module.exports`, or `mexpo` in a `.js` file

**Generated Code:**
```javascript
module.exports = {
    ${1:member}
};
```

---

### 🏷️ ISML Snippets

ISML (Internet Store Markup Language) templates are used for rendering storefront pages.

#### `sitepref` — Site Preference Value
Quickly access custom site preferences.

**Usage:** Type `sitepref` in an `.isml` file

**Generated Code:**
```isml
${dw.system.Site.getCurrent().getCustomPreferenceValue('${1}')}
```

---

#### `globalpref` — Global System Preference
Access global system preferences with existence checking.

**Usage:** Type `globalpref` in an `.isml` file

**Generated Code:**
```isml
${'${pref}' in dw.system.System.getPreferences().getCustom() ? dw.system.System.getPreferences().getCustom()['${pref}'] : ''}
```

---

### 🔌 Service Registry Snippets

#### `lcr` — Local Service Registry
Creates a complete service registry configuration for external API calls.

**Usage:** Type `lcr` and press Tab

**Generated Code:**
```javascript
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

**Features:**
- Complete service lifecycle methods
- Mock call implementation for testing
- Request/response logging support
- Dynamic URL and body parameter handling

---

### ⚡ JavaScript Utility Snippets

| Shortcut | Description | Generated Code |
|----------|-------------|----------------|
| `objectCreate`, `objcreate`, `objc` | Create null object | `var ${1} = Object.create(null);` |
| `object.define`, `objectdefine`, `objdef` | Define property with value | `Object.defineProperty(object, '${1}', {enumerable: true,value: ${2}});` |
| `object.define`, `objectdefine`, `objdef` | Define property with IIFE | `Object.defineProperty(object, '${1}', {enumerable: true,value: (function () {${2}}()));` |
| `require` | Module require statement | `const ${1:module} = require('${1:module}');` |
| `typeof`, `to` | Type checking | `typeof ${1:source} === '${2:undefined}'` |
| `instanceof`, `io` | Instance checking | `${1:source} instanceof ${2:Object}` |
| `oa`, `object.assign`, `objectassign` | Object.assign shallow copy | `Object.assign({}, ${1:original}, ${2:source})` |

---

## Usage Workflow

1. **Create a new controller file** (e.g., `Product.js`)
2. Type `newsrv` and press Tab to scaffold the basic structure
3. Use Tab to navigate through placeholders:
   - Select HTTP method from dropdown
   - Enter route path
   - Add business logic
   - Select response type
4. Add additional routes using `newroute` snippet
5. For extending existing controllers, use `extsrv` instead

---

## Best Practices

### Controller Development
- Always use `'use strict';` at the top (included in snippets)
- Extend controllers rather than override when possible
- Use `module.superModule` to inherit parent functionality
- Properly call `next()` to continue middleware chain

### Service Integration
- Use `lcr` snippet for all external service calls
- Implement proper error handling in `parseResponse`
- Use `mockCall` for unit testing without external dependencies
- Always log requests and responses for debugging

### ISML Templates
- Use `sitepref` for configurable values that vary by site
- Use `globalpref` for system-wide configuration values
- Cache preference lookups when used multiple times in a template

---

## File Type Support

| File Extension | Available Snippets |
|---------------|-------------------|
| `.js` (Controllers) | `newsrv`, `newroute`, `extsrv`, `extroute`, `expmodule`, `mexpo`, `lcr` |
| `.js` (Scripts) | `expmodule`, `objectCreate`, `object.define`, `require`, `typeof`, `instanceof`, `object.assign` |
| `.isml` | `sitepref`, `globalpref` |

---

## Keyboard Shortcuts

All snippets support VS Code's IntelliSense:
- **Trigger:** Type the shortcut keyword
- **Accept:** Press `Tab` or `Enter`
- **Navigate:** Press `Tab` to move to next placeholder
- **Select:** Use arrow keys for dropdown options in `${1|option1,option2|}` syntax

---

## Troubleshooting

### Snippets Not Appearing
1. Check file extension matches snippet type (.js or .isml)
2. Verify extension is enabled in VS Code
3. Reload window if recently installed (Ctrl+Shift+P → "Reload Window")

### Placeholder Navigation Issues
- Use `Tab` to move forward through placeholders
- Use `Shift+Tab` to move backward
- Use `Esc` to

# api documentation for  [homebridge-mqtt (v0.4.2)](https://github.com/cflurin/homebridge-mqtt#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-homebridge-mqtt.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-homebridge-mqtt) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-homebridge-mqtt.svg)](https://travis-ci.org/npmdoc/node-npmdoc-homebridge-mqtt)
#### MQTT Plugin for Homebridge

[![NPM](https://nodei.co/npm/homebridge-mqtt.png?downloads=true)](https://www.npmjs.com/package/homebridge-mqtt)

[![apidoc](https://npmdoc.github.io/node-npmdoc-homebridge-mqtt/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-homebridge-mqtt_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-homebridge-mqtt/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-homebridge-mqtt/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-homebridge-mqtt/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "flurin"
    },
    "bugs": {
        "url": "http://github.com/cflurin/homebridge-mqtt/issues"
    },
    "dependencies": {
        "mqtt": ">=2.4.0",
        "request": ">=2.79.0"
    },
    "description": "MQTT Plugin for Homebridge",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "5925a65d5beee6454e577187c17dda45eddd270c",
        "tarball": "https://registry.npmjs.org/homebridge-mqtt/-/homebridge-mqtt-0.4.2.tgz"
    },
    "engines": {
        "homebridge": ">=0.4.16",
        "node": ">=4.3.2"
    },
    "gitHead": "2cda67c6a4df84149b93dcbfdf336b68ffb61bef",
    "homepage": "https://github.com/cflurin/homebridge-mqtt#readme",
    "keywords": [
        "homebridge",
        "homebridge-plugin",
        "homekit",
        "siri",
        "mqtt",
        "node-RED"
    ],
    "license": "ISC",
    "maintainers": [
        {
            "name": "cflurin",
            "email": "flurin.npm@gmail.com"
        }
    ],
    "name": "homebridge-mqtt",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/cflurin/homebridge-mqtt.git"
    },
    "scripts": {},
    "version": "0.4.2"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module homebridge-mqtt](#apidoc.module.homebridge-mqtt)
1.  object <span class="apidocSignatureSpan">homebridge-mqtt.</span>accessory
1.  object <span class="apidocSignatureSpan">homebridge-mqtt.</span>controller
1.  object <span class="apidocSignatureSpan">homebridge-mqtt.</span>model
1.  object <span class="apidocSignatureSpan">homebridge-mqtt.</span>utils

#### [module homebridge-mqtt.accessory](#apidoc.module.homebridge-mqtt.accessory)
1.  [function <span class="apidocSignatureSpan">homebridge-mqtt.accessory.</span>Accessory (params)](#apidoc.element.homebridge-mqtt.accessory.Accessory)

#### [module homebridge-mqtt.controller](#apidoc.module.homebridge-mqtt.controller)
1.  [function <span class="apidocSignatureSpan">homebridge-mqtt.controller.</span>Controller (params)](#apidoc.element.homebridge-mqtt.controller.Controller)

#### [module homebridge-mqtt.model](#apidoc.module.homebridge-mqtt.model)
1.  [function <span class="apidocSignatureSpan">homebridge-mqtt.model.</span>Model (params)](#apidoc.element.homebridge-mqtt.model.Model)

#### [module homebridge-mqtt.utils](#apidoc.module.homebridge-mqtt.utils)
1.  [function <span class="apidocSignatureSpan">homebridge-mqtt.utils.</span>Utils ()](#apidoc.element.homebridge-mqtt.utils.Utils)



# <a name="apidoc.module.homebridge-mqtt"></a>[module homebridge-mqtt](#apidoc.module.homebridge-mqtt)



# <a name="apidoc.module.homebridge-mqtt.accessory"></a>[module homebridge-mqtt.accessory](#apidoc.module.homebridge-mqtt.accessory)

#### <a name="apidoc.element.homebridge-mqtt.accessory.Accessory"></a>[function <span class="apidocSignatureSpan">homebridge-mqtt.accessory.</span>Accessory (params)](#apidoc.element.homebridge-mqtt.accessory.Accessory)
- description and source-code
```javascript
function Accessory(params) {

  this.log = params.log;
  Service = params.Service;
  Characteristic = params.Characteristic;
  platform_name = params.platform_name;
  get = params.get;
  set = params.set;
  identify = params.identify;

  this.name;          // assigned by this.configureAccessory

  this.i_value = {};
  this.i_label = {};
  this.i_props = {};

  this.reachable = true;

  this.services = {};
  this.service_types = {};
  this.service_names = {};
  this.service_namesList = [];

  this.set_timeout;
  this.prec_c;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.homebridge-mqtt.controller"></a>[module homebridge-mqtt.controller](#apidoc.module.homebridge-mqtt.controller)

#### <a name="apidoc.element.homebridge-mqtt.controller.Controller"></a>[function <span class="apidocSignatureSpan">homebridge-mqtt.controller.</span>Controller (params)](#apidoc.element.homebridge-mqtt.controller.Controller)
- description and source-code
```javascript
function Controller(params) {

  config = params.config;
  this.log = params.log;
  plugin_name = params.plugin_name;
  plugin_version = params.plugin_version;
  platform_name = params.platform_name;
  api = params.api;
  HapAccessory = params.HapAccessory;
  Service = params.Service;
  Characteristic = params.Characteristic;
  UUIDGen = params.UUIDGen;

  this.accessories = {};
  this.hap_accessories = {};

  var model_parameters = {
    "config": config,
    "log": this.log,
    "plugin_name": plugin_name,
    "Characteristic": Characteristic,
    "addAccessory": this.addAccessory.bind(this),
    "addService": this.addService.bind(this),
    "removeAccessory": this.removeAccessory.bind(this),
    "removeService": this.removeService.bind(this),
    "setValue": this.setValue.bind(this),
    "getAccessories": this.getAccessories.bind(this),
    "updateReachability": this.updateReachability.bind(this),
    "setAccessoryInformation": this.setAccessoryInformation.bind(this)
  };

  this.createModel(model_parameters);

  accessory_parameters = {
    "log": this.log,
    "platform_name": platform_name,
    "Service": Service,
    "Characteristic": Characteristic,
    "get": this.get.bind(this),
    "set": this.set.bind(this),
    "identify": this.identify.bind(this)
  };
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.homebridge-mqtt.model"></a>[module homebridge-mqtt.model](#apidoc.module.homebridge-mqtt.model)

#### <a name="apidoc.element.homebridge-mqtt.model.Model"></a>[function <span class="apidocSignatureSpan">homebridge-mqtt.model.</span>Model (params)](#apidoc.element.homebridge-mqtt.model.Model)
- description and source-code
```javascript
function Model(params) {

  this.config = params.config;
  this.log = params.log;
  plugin_name = params.plugin_name;
  Characteristic = params.Characteristic;

  addAccessory = params.addAccessory;
  addService = params.addService;
  removeAccessory = params.removeAccessory;
  removeService = params.removeService;
  setValue = params.setValue;
  getAccessories = params.getAccessories;
  updateReachability = params.updateReachability;
  setAccessoryInformation = params.setAccessoryInformation;
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.homebridge-mqtt.utils"></a>[module homebridge-mqtt.utils](#apidoc.module.homebridge-mqtt.utils)

#### <a name="apidoc.element.homebridge-mqtt.utils.Utils"></a>[function <span class="apidocSignatureSpan">homebridge-mqtt.utils.</span>Utils ()](#apidoc.element.homebridge-mqtt.utils.Utils)
- description and source-code
```javascript
function Utils() {
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)

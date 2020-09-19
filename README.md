ReftabNode
=============

This is a quick and dirty module to interact with the Reftab API via Node.js.

# Instructions

### Download repository

run 'npm install' in directory to install all dependencies

Use the [Reftab API documentation](https://www.reftab.com/api-docs) to find endpoints to access.

### Methods
The Reftab client has 4 methods available, get, post, put, delete, corresponding to the HTTP methods.

Parameters each take:
* get(endpoint, id)
  * endpoint (e.g. assets, optional parameters may be added such as ?limit=200 to get additional assets)
  * id (default None)
* post(endpoint, body)
  * endpoint (e.g. assets)
  * body (a js object which will be converted to json)
* put(endpoint, id, body)
  * endpoint (e.g. assets)
  * id (required)
  * body (a js object which will be converted to json)
* delete(endpoint, id)
  * endpoint (e.g. assets)
  * id (required)

### Prerequisites

* Node.js
* A valid API key pair from Reftab
  * Generate one in Reftab Settings
  
# Examples

### Get an Asset and Update It

```javascript
/*This example shows how to get an asset and update it*/

const reftab = require('./lib/reftab');

const api = new reftab({
  publicKey: [publicKey],
  secretKey: [secretKey]
});

api.get('assets', 'NY00')
  .then((asset) => {
    asset.title = 'New Title';
    api.put('assets', 'NY00', asset)
      .then((updatedAsset) => console.log(updatedAsset))
      .catch((err) => console.error(err))
  })
  .catch((err) => console.log(err));
```
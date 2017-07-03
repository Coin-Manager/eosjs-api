[![Build Status](https://travis-ci.org/eosjs/api.svg?branch=master)](https://travis-ci.org/eosjs/api)
[![NPM](https://img.shields.io/npm/v/eosjs-api.svg)](https://www.npmjs.org/package/eosjs-api)

# Eos API

Application programming interface to EOS blockchain nodes.  This is mostly for read-only API calls.  If you decide you need to sign transactions, your better off using this API in the [eosjs](https://github.com/eosjs/eosjs) package.

Status: Beta

## Usage

```javascript
Testnet = require('eosapi/testnet') // Or Testnet = require('./testnet')
assert = require('assert')

testnet = Testnet() // See ./testnet.js for configuration

// Any API call without a callback parameter will print documentation: description,
// parameters, return value, and possible errors.  All methods and documentation
// are created from JSON files in eosjs/json/api/v1..
testnet.getInfo()

// General callback for these examples
callback = (err, res) => {err ? console.error(err) : console.log(res)}

// The server does not expect any parameters only the callback is needed
testnet.getInfo(callback)

// Parameters are added before the callback
testnet.getBlock(1, callback)

// Parameters can be an object
testnet.getBlock({block_num_or_id: 1}, callback)

// All methods work under promisifyAll
let {promisifyAll} = require('sb-promisify')
testnet = promisifyAll(testnet)
testnet.getInfoAsync().catch(error => { console.error(error) })
// returns: Promise
```

## API Documentation

The API methods and documentation are stored in JSON files in this [folder](https://github.com/eosjs/json/tree/master/api).

## Environment

Node 6+ and browser (browserify, webpack, etc)

## TODO

Automate code-coverage after a public testnet is available.

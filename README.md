# sauce-connect-tunnel
[![Build Status](https://travis-ci.org/bytbil/sauce-connect-tunnel.svg)](https://travis-ci.org/bytbil/sauce-connect-tunnel)

A Node.js wrapper around the Saucelabs connect proxy binaries.

## Install

```
npm install --save-dev sauce-connect-tunnel
```

## Usage

### Simple Usage
```javascript
var sauceConnectTunnel = require('sauce-connect-tunnel');
var tunnel = new sauceConnectTunnel(process.env.SAUCE_USERNAME, process.env.SAUCE_ACCESSKEY);

tunnel.start(function(status) {
    if (!status) {
        console.error('Something went wrong starting the tunnel');
    }

    console.log('Sauce Connect Tunnel ready');

    tunnel.stop(function() {
        console.log('Sauce Connect Tunnel destroyed');
    });
});
```

## Options

```javascript
new sauceConnectTunnel(username, accessKey, tunnelId, enableTunnel, args);
```

#### `username`
Username to saucelabs

#### `accessKey`
Accesskey for saucelabs

#### `tunnelId`
Unique identifier for the tunnel. It's optional and automatically generated when not specified. Note that the tunnel identifier may have to be passed in with the browsers object as a desired capability to enable traffic to use the tunnel. More details [here](https://saucelabs.com/docs/additional-config#tunnel-identifier)

#### `enableTunnel`
Boolean value to indicate if the tunnel is to be created or not. This value can be set to `false` to mock a tunnel creation if the site tested is publicly accessible. This value is optional and defaults to `true`.

#### `args`
An array of option flags (see [here](https://saucelabs.com/docs/connect)). Example: ``['--debug', '--direct-domains', 'www.google.com']``. It's optional.


## Contribution
Forked from https://github.com/jmreidy/sauce-tunnel

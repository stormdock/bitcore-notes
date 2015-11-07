
If bitcore is not installed:

```
npm install -g bitcore
```

This will install the latest versions of

```
"bitcore-lib": "^0.13.8"
"bitcore-node": "^1.0.0"
"insight-api": "^0.3.1"
"insight-ui": "^0.3.0"
```

Make sure that the configuration file **bitcore-node.json**
is located in the same directory that you run bitcore

```
bitcore start
```

And then bring up your browser
[here].
(http://localhost:3001/insight)

To uninstall an older version

```
npm uninstall -g bitcore
```

##### bitcore-node.json

```
{
  "datadir": "/miabitcore/testnet/data",
  "network": "testnet",
  "port": 3001,
  "services": [
    "address",
    "bitcoind",
    "db",
    "insight-api",
    "insight-ui",
    "web"
  ]
}
```
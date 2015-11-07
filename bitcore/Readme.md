
If bitcore is not installed:

```
npm install -g bitcore
```

Then fire up bitcore

```
bitcore start
```

To uninstall an older version

```
npm uninstall -g bitcore
```

##### Configuration file bitcore-node.json

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
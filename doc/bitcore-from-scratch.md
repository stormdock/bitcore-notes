
##### bitcore

Add
[this configuration file]
(https://github.com/stormasm/bitcore-notes/blob/master/bitcore/bitcore-node.json)
to the bitcore repo so that when

```
./bin/bitcore start
```

gets fired up this configuration file is used.

Remove the following dependencies in package.json of the **bitcore** repo.

```
"bitcore-lib": "^0.13.8",
"bitcore-node": "^1.0.0",
"insight-api": "^0.3.1",
```

leaving only

```
 "insight-ui": "^0.3.0"
```

Then run the following command inside the bitore repo.

```
npm install
```

##### bitcore-node-btcd1128

No changes needed for this repo.

To see what modifications where made to the
[bitcore-node]
(https://github.com/bitpay/bitcore-node)
to produce **bitcore-node-btcd1128** read the top portion of this
[Readme file]
(https://github.com/stormasm/bitcore-node-btcd1128/blob/master/README.md)

##### bitcore-lib

No changes needed for this repo.

##### insight-api

No changes needed for this repo.

* bitcore-node
* bitcore-lib
* insight-api

all get set up individually from instructions (see above)

Go to each of the above 3 repos and run these 2 commands.

```
npm install
npm link
```

Then go to the bitcore repo and

```
npm link bitcore-node
npm link bitcore-lib
npm link insight-api
```

##### Check to make sure your links are there

Find where your node is installed from this command

```
npm config ls -l | grep prefix
```

and then go to lib/node_modules...

There you will see all of the links you made above.

```
bitcore-node -> /tmp31/bitcore-node-btcd1127
bitcore-lib -> /tmp31/bitcore-lib
insight-api -> /tmp31/insight-api
```

For more details on setting up the links go
[here]
(./npmlink.md)

##### Fire up bitcore

```
./bin/bitcore start
```

gets called and from there you can test your api...

[http://localhost:3001/insight-api/block-index/100]
(http://localhost:3001/insight-api/block-index/100)

```
{
blockHash: "000000002ce019cc4a8f2af62b3ecf7c30a19d29828b25268a0194dbac3cac50"
}
```

[http://localhost:3001/insight-api/block-index/90]
(http://localhost:3001/insight-api/block-index/90)

```
{
blockHash: "000000009836d06cf1068dfdd4c41d85849b96f3be0b8696cdade4fa9b134ec6"
}
```

[http://localhost:3001/insight-api/block-index/95]
(http://localhost:3001/insight-api/block-index/95)

```
{
blockHash: "00000000d7cd1c7906017b9024528f0beb2abd526d4fd9c71e39b67b0cc3751c"
}
```

[http://test.webbtc.com/?height=100]
(http://test.webbtc.com/?height=100)

And this data can be compared to the same **test** bitcoin blockchain
at the **webbtc** website links above.

#### bitcore-lib code removal

You need to remove these lines of code from your repo according to
the stack trace after starting up bitcore.

* filename: index.js

Otherwise you get the warning message below and **bitcore** will not start.

##### bitcore.versionGuard

```
bitcore.versionGuard = function(version) {
  if (version !== undefined) {
    var message = 'More than one instance of bitcore-lib found. ' +
      'Please make sure to require bitcore-lib and check that submodules do' +
      ' not also include their own bitcore-lib dependency.';
    throw new Error(message);
  }
};
bitcore.versionGuard(global._bitcore);
```

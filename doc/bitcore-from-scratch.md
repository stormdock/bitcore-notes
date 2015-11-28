
##### bitcore

Add
[this file]
(https://github.com/stormasm/bitcore-notes/blob/master/bitcore/bitcore-node.json)
to the bitcore directory so that when

```
./bin/bitcore start
```

gets fired up this configuration file is used.

The package.json file should remove the following dependencies
that you are going to modify by hand...  If the dependency is not
changed in any way then it can be left untouched and remain in
this file...

```
"bitcore-lib": "^0.13.8",
"bitcore-node": "^1.0.0",
"insight-api": "^0.3.1",
```

leaving only

```
 "insight-ui": "^0.3.0"
```

##### bitcore-node-btcd1127

Grab this repo and do the npm link dance.

##### bitcore-lib

Remove the version guard code (see below) in the file **index.js**

##### insight-api

In package.json remove the dependency **bitcore-lib**

Find where your node is installed from this command

```
npm config ls -l | grep prefix
```

and then go to lib/node_modules...

There you will see all of the links you need to make sure that things
are set up correctly.

```
bitcore-node -> /tmp31/bitcore-node-btcd1127
bitcore-lib -> /tmp31/bitcore-lib
insight-api -> /tmp31/insight-api
```

For more details on setting up the links go
[here]
(./npmlink.md)

* bitcore-node
* bitcore-lib
* insight-api
* insight-ui

all get set up individually and then

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

[http://localhost:3001/insight-api/block-index/80]
(http://localhost:3001/insight-api/block-index/80)

{
blockHash: "00000000beaf2091cc7b1637fb228e481d82de09d0f895092e00a105e2ed0606"
}

##### bitcore.versionGuard

You need to remove these lines of code from bitcore-lib...

Otherwise you get the warning message below and **bitcore** will not start.

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
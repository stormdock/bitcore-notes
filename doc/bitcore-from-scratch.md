
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


So I am came up with a simple solution to run the bitcore-node tests.

Edit the **package.json** and remove the install entry
so that bin/install does **NOT** get triggered.

Also remove

```
 "aws-sdk": "~2.0.0-rc.15"
 "bitcoin": "^2.3.2"
 "bitcoind-rpc": "^0.3.0"
 "bitcore-p2p": "~1.0.0"
```

Also remove the file

```
binding.gyp
```

grab a **build** directory from an installed bitcore-node to get the **bindings** file.

```
ls -lR build
total 0
drwxr-xr-x  4 ma  wheel  136 Nov  4 11:22 Release

build/Release:
total 50400
-rwxr-xr-x  1 ma  wheel  25798232 Oct 21 18:44 bitcoind.node
-rw-r--r--  1 ma  wheel       287 Oct 21 18:44 bitcoind.node.sig
```

Then run the standard

```
npm install
```

The tests are now ready to run :

```
npm test
```

or to run an individual test

```
mocha test/services/db.unit.js
```

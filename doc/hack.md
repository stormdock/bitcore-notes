
So I am came up with a simple solution to run the bitcore-node tests..

Clone the repo
[bitcore-node]
(https://github.com/bitpay/bitcore-node)

Edit the **bin/install** script and remove these last 2 lines:

```
echo "Prebuild binary could not be downloaded, building from source..."
./bin/build
```

Also remove the file

```
binding.gyp
```

Then run the standard

```
npm install
```

##### Running the tests

The tests are now ready to run :

```
npm test
```

or to run an individual test

```
mocha test/services/db.unit.js
```

##### Trouble Shooting

If

```
libbitcoind-1.0.0-node14-darwin-x64.tgz
```

does NOT download properly from its Amazon bucket

Another way to get this file is to go to a separate directory
and run this command

```
npm install bitcore-node
```

Grab this file and untar it in the top level repo.

You will find it down in the *node_modules* directory

A successful download will show the above file along with the contents
of the build directory:

```
ls -lR build
total 0
drwxr-xr-x  4 ma  wheel  136 Nov  4 11:22 Release

build/Release:
total 50400
-rwxr-xr-x  1 ma  wheel  25798232 Oct 21 18:44 bitcoind.node
-rw-r--r--  1 ma  wheel       287 Oct 21 18:44 bitcoind.node.sig
```

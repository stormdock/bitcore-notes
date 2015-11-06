
So I am came up with a simple solution to run the bitcore-node tests.

Edit the **package.json** and remove the install entry
so that bin/install does **NOT** get triggered.

Then run the standard

```
npm install
```

Go to *bitcore-notes/test*

and move the

node_modules/bitcore-node/build

* Release/bitcoind.node
* Release/bitcoind.node.sig

directory which contains the bindings file to the top level

bitcore-node repo

So it will now contain the 2 above files

Now you can run this command:

```
mocha node_modules/bitcore-node/test/services/db.unit.js
```

and modify and add tests accordingly...

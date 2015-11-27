
[npm link]
(https://docs.npmjs.com/cli/link)
allows you to do local development on the core bitcore packages.

In this example we are doing local development on
[bitcore-node]
(https://github.com/bitpay/bitcore-node)
and want to be able to reference my local development from
[bitcore]
(https://github.com/bitpay/bitcore)

##### bitcore-node

In summary these are the 2 commands

```
npm link [inside the bitcore-node directory]
npm link bitcore-node [inside the bitcore directory]
```

In your local bitcore repo remove bitcore-node from package.json

go to the directory where your local **bitcore-node** is located and

```
npm link
```

go the directory where your local **bitcore** is located and

```
npm link bitcore-node
```

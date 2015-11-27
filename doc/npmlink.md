
[npm link]
(https://docs.npmjs.com/cli/link)
allows you to do local development on the core bitcore packages.

In this example we are doing local development on
[bitcore-node]
(https://github.com/bitpay/bitcore-node)
and want to be able to reference my local development from
[bitcore]
(https://github.com/bitpay/bitcore)

```
npm link [inside the **bitcore-node** package]
npm link bitcore-node
```

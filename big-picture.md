
This is an attempt to outline the big picture of
[Bitpay's Bitcore Ecosystem]
(https://github.com/bitpay)

### Bitcore

The bitcore repo is simply a **pointer** to the other important repos
that is part of bitcore.

* bitcore-lib
* bitcore-node
* insight-api
* insight

The only 2 significant files in this repo are in the **bin** directory.
And those 2 files are identical except what they call into.

##### bitcore

```
var bitcore = require('bitcore-node/lib/cli/bitcore');
```

##### bitcored

```
var bitcored = require('bitcore-node/lib/cli/bitcored');
```

##### Introduction

So what exactly is going on here ?  It appears that bitcore is a way to abstract
the tools going into the future development of bitcore.  People will get used
to using the bitcore command line and its associated functionality and not have
to worry about the implementation of the functionality.  So lets say 3 months
from now Bitpay wants to swap out the insight-api for a new blockchain api.

To the end user nothing will change, they will simply call into the new
blockchain api and not have to worry about the implementation details.

---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Oracle APIs

This is the API documentation for Oracle

## Post a new order

> inputs: userOrderDetailsObject(signed)
            arbiterOrderDetailsObject(signed)

```json
[
  {
    "pubkey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
    "expiration": "1479161129742",
    "pair": "BTC_ETH",
    "amountIn": "1",
    "rate": "0.02",
    "returnAddress": "1NvWJhWoMtXe16KLemyTq3ZMoyLipN8EKu",
    "withdrawalAddress": "0x81ca1263c188a0a1679f63eaef92e54cf8c7ccbe",
    "signature": ""
  },
  {
    "orderID": "c7d856f6-ceb8-4e23-aae0-9905e3036927",
    "arbiterPubKey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
    "encDerivationPath": "??",
    "multiSigAddr": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE"
  }
]
```

> outputs:

```json
{
    "oraclePubkey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
    "oracleMultisigAddress": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE",
}
```

User hits this endpoint.

### HTTP Request

`POST '/api/v1/newOrder'`

### Passed-in Parameters

Parameter | Description
--------- | -----------
userOrderDetailsObject |
arbiterOrderDetailsObject  |


## Get tx when bitcoin client sees deposit

> input: ??

```json
{
    "??": "??"
}
```

> outputs: ??

```json
{
    "??": "??"
}
```


This endpoint retrieves transaction details


### HTTP Request

`POST 'api/v1/received'`

### URL Parameters

Parameter | Description
--------- | -----------
?? | ??


## Post a fulfilled order

> inputs:

```json
{
  "orderId": "c7d856f6-ceb8-4e23-aae0-9905e3036927",
  "tx": "010000000175e1769813db8418fea17576694af1ff31cb2b512\
                      b7333e6eb42f030d0d7787200000000b5004830450221008d5e\
                      c57d362ff6ef6602e4e756ef1bdeee12bd5c5c72697ef1455b3\
                      79c90531002202ef3ea04dfbeda043395e5bc701e4878c15baa\
                      b9c6ba5808eb3d04c91f641a0c014c69522103310188e911026\
                      cf18c3ce274e0ebb5f95b007f230d8cb7d09879d96dbeab1aff\
                      210243930746e6ed6552e03359db521b088134652905bd2d154\
                      1fa9124303a41e95621029e03a901b85534ff1e92c43c74431f\
                      7ce72046060fcf7a95c37e148f78c7725553aeffffffff01c0b\
                      c973b000000001976a914b6f64f5bf3e38f25ead28817df7929\
                      c06fe847ee88ac00000000",
  "inputs": "[c7d856f6-ceb8-4e23-aae0-9905e3036927, a7d856f6-ceb8-4e23-aae0-9905e3036927, b7d856f6-ceb8-4e23-aae0-9905e3036927]"
}
```

> outputs:

```json
{
    "oraclePubkey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
    "oracleMultisigAddress": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE",
}
```


Arbiter sends this request for Oracle for co-sign request


### HTTP Request

`POST 'api/v1/fulfillOrder'`

### URL Parameters

Parameter | Description
--------- | -----------
orderId | orderId
tx | partially signed tx
inputs | array of matched orders' orderIds


## Post a returned order

> inputs:

```json
{
  "orderId": "c7d856f6-ceb8-4e23-aae0-9905e3036927",
  "tx": "010000000175e1769813db8418fea17576694af1ff31cb2b512\
                               b7333e6eb42f030d0d7787200000000b5004830450221008d5e\
                               c57d362ff6ef6602e4e756ef1bdeee12bd5c5c72697ef1455b3\
                               79c90531002202ef3ea04dfbeda043395e5bc701e4878c15baa\
                               b9c6ba5808eb3d04c91f641a0c014c69522103310188e911026\
                               cf18c3ce274e0ebb5f95b007f230d8cb7d09879d96dbeab1aff\
                               210243930746e6ed6552e03359db521b088134652905bd2d154\
                               1fa9124303a41e95621029e03a901b85534ff1e92c43c74431f\
                               7ce72046060fcf7a95c37e148f78c7725553aeffffffff01c0b\
                               c973b000000001976a914b6f64f5bf3e38f25ead28817df7929\
                               c06fe847ee88ac00000000"
}
```

> outputs: signed tx

```json
{
    "tx": "??"
}
```


Arbiter/User sends this request for Oracle for co-sign request


### HTTP Request

`POST 'api/v1/returnedOrder'`

### URL Parameters

Parameter | Description
--------- | -----------
orderId | orderId
tx | partially signed tx

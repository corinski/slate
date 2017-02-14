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

> inputs: userOrderDetailsObject(signed) and arbiterOrderDetailsObject(signed)

```json
[
  {
    "pubkey": "??",
    "expiration": "??",
    "pair": "??",
    "amountIn": "??",
    "rate": "??",
    "returnAddress": "??",
    "withdrawalAddress": "??",
    "signature": "??"
  },
  {
    "orderID": "??",
    "arbiterPubKey": "??",
    "encDerivationPath": "??",
    "multiSigAddr": "??"
  }
]
```

> outputs:

```json
{
    "oraclePubkey": "??",
    "oracleMultisigAddress": "??",
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


## Get transaction for when bitcoin client sees deposit

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
  "orderId": "",
  "tx": "",
  "inputs": ""
}
```

> outputs:

```json
{
    "oraclePubkey": "??",
    "oracleMultisigAddress": "??",
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
  "orderId": "",
  "tx": ""
}
```

> outputs: signed tx

```json
{
    "tx": "??",
}
```


Arbiter sends this request for Oracle for co-sign request


### HTTP Request

`POST 'api/v1/returnedOrder'`

### URL Parameters

Parameter | Description
--------- | -----------
orderId | orderId
tx | partially signed tx

---
title: API Reference

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Arbiter APIs

This is the API documentation for Arbiter


## Get coins

> successful outputs:

```json
[
    "btc",
    "ltc",
    "eth"
]
```

> failed outputs:

```json
{
    "success": false,
    "error": e
}
```

This endpoint retrieves a list of coins

### HTTP Request

`GET 'api/v1/coins'`



## Get pairs

> successful outputs:

```json
[
    "BTC_LTC",
    "LTC_BTC"
]
```

> failed outputs:

```json
{
    "success": false,
    "error": e
}
```

This endpoint retrieves a list of coin pairs

### HTTP Request

`GET 'api/v1/pairs'`



## Get markets

> successful outputs:

```json
[
    {
        "id": 1,
        "pair1": "BTC_LTC",
        "pair2": "LTC_BTC",
        "base_currency": "LTC",
        "quote_currency": "BTC",
        "base_min_size": "0.00000001",
        "base_max_size": "21000000",
        "quote_increment": "0.0001"
    }
]
```

> failed outputs:

```json
{
    "success": false,
    "error": e
}
```

This endpoint retrieves a list of markets

### HTTP Request

`GET 'api/v1/markets'`







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

> successful outputs:

```json
{
    "success": true,
    "response": {
        "oraclePubkey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
        "oracleMultisigAddress": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE"
        }
}
```

> failed outputs:

```json
{
    "success": false,
    "error": e
}
```

User hits this endpoint.

### HTTP Request

`POST '/api/v1/newOrder'`

### URL Parameters

Parameter | Description
--------- | -----------
userOrderDetailsObject |
arbiterOrderDetailsObject  |


## Get tx when bitcoin client sees deposit

> input:

```json
{
    "??": "??"
}
```

> successful outputs:

```json
{
    "success": true,
    "??": "??"
}
```

> failed outputs:

```json
{
    "success": false,
    "error": e
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
  "tx": {
        "txid": "5154a0bac0a6688a522e442119d0c7c6f4fa44d1669960d81858ed76a8a0baad",
         "hash": "5154a0bac0a6688a522e442119d0c7c6f4fa44d1669960d81858ed76a8a0baad",
         "size": 223,
         "vsize": 223,
         "version": 1,
         "locktime": 1088130,
         "vin":
             [ { "txid": "79f8d0bc26605a9bc7dc59b2ce43c290947e33120fca6b3e946588086d26276f",
                 "vout": 1,
                 "scriptSig": [Object],
                 "sequence": 4294967294 } ],
         "vout":
             [ { "value": 40000, "n": 0, "scriptPubKey": [Object] },
                 { "value": 249337401, "n": 1, "scriptPubKey": [Object] } ]",
  "inputs": "["c7d856f6-ceb8-4e23-aae0-9905e3036927", "a7d856f6-ceb8-4e23-aae0-9905e3036927", "b7d856f6-ceb8-4e23-aae0-9905e3036927"]"
}
```

> successful outputs:

```json
{
    "success": true,
    "response": {
        "oraclePubkey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
        "oracleMultisigAddress": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE"
    }
}
```

> failed outputs:

```json
{
    "success": false,
    "error": e
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
  "tx": {
        "txid": "5154a0bac0a6688a522e442119d0c7c6f4fa44d1669960d81858ed76a8a0baad",
         "hash": "5154a0bac0a6688a522e442119d0c7c6f4fa44d1669960d81858ed76a8a0baad",
         "size": 223,
         "vsize": 223,
         "version": 1,
         "locktime": 1088130,
         "vin":
             [ { "txid": "79f8d0bc26605a9bc7dc59b2ce43c290947e33120fca6b3e946588086d26276f",
                 "vout": 1,
                 "scriptSig": [Object],
                 "sequence": 4294967294 } ],
         "vout":
             [ { "value": 40000, "n": 0, "scriptPubKey": [Object] },
                 { "value": 249337401, "n": 1, "scriptPubKey": [Object] } ]"
}
```

>successful outputs: (signed tx)

```json
{
    "success": true,
    "response": {
        "tx": "??"
    }
}
```

> failed outputs:

```json
{
    "success": false,
    "error": e
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

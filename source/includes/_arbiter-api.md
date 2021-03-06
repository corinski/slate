
# Arbiter APIs

This is the API documentation for Arbiter


## Get global info for a coin pair

> inputs:

```json
"BTC_ETH"
```

> successful outputs:

```json
???
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

`POST '/api/v1/globals/:pair'`

### URL Parameters

Parameter | Description
--------- | -----------
coin pair | coin pair







## Get last price for a coin pair

> inputs:

```json
"BTC_ETH"
```

> successful outputs:

```json
{
    "success": true,
    "response": {
        price: 0.1
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

`GET '/api/v1/lastprice'`

### URL Parameters

Parameter | Description
--------- | -----------
coin pair | coin pair












## Get a list of coins

> inputs:

```
none
```

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


### URL Parameters

Parameter | Description
--------- | -----------
none







## Get pairs

> inputs:

```
none
```

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

### URL Parameters

Parameter | Description
--------- | -----------
none








## Get markets

> inputs:

```
none
```

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

### URL Parameters

Parameter | Description
--------- | -----------
none






## Get the orderbook of a pair

> inputs:

```json
"BTC_LTC"
```

> successful outputs:

```json
{
    "bids": [
       {
            "quantity": 3.59944722,
            "price": 0.01889002,
            "orders": [
                {
                    "id": "211d44ee-772a-4919-9239-cf63e8b35671",
                    "qty": 3.59944722
                }
            ]
       }
    ],
    "offers": [
        {
            "quantity": 2.63090184,
            "price": 0.01900489,
            "orders": [
                {
                    "id": "813d00dd-f89a-41dd-96e5-565e1b979b9c",
                    "qty": 2.63090184
                }
            ]
        }
    ]
}
```

> failed outputs:

```json
{
    "success": false,
    "error": e
}
```

This endpoint retrieves the orderbook of a pair

### HTTP Request

`GET 'api/v1/orderbook/:pair'`

### URL Parameters

Parameter | Description
--------- | -----------
coin pair | a pair of coin




## Get the order list of an account

> inputs:

```json
"xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp"
```

> successful outputs:

```json
[
  {
    "orderID": "c7d856f6-ceb8-4e23-aae0-9905e3036927",
    "arbiterPubKey": "xpub661MyMwAqRbcGEuCBm3UEh4bc6r3iVRhcHsg6hmphFYM9Gg5kFLAZSMCjVpWWDug6hjU1MMs2ZZr6xuN6eUXc88FixnQXm5y7bgJCi3vTzp",
    "encDerivationPath": "??",
    "multiSigAddr": "2MundrzJqMjj6dwrJXiarbnXQbMPt1iWfaE"
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

User hits this endpoint.

### HTTP Request

`POST '/api/v1/orderlist/:account'`

### URL Parameters

Parameter | Description
--------- | -----------
account | user's BTC pubkey or address ??





## Get the latest trade info on a coin pair

> inputs:

```json
"BTC_LTC"
```

> successful outputs:

```json
???
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

`POST '/api/v1/getLatestPairTrades/:pair'`

### URL Parameters

Parameter | Description
--------- | -----------
coin pair | coin pair






## Get the order info for an orderId

> inputs:

```json
"orderId"
```

> successful outputs:

```json
{
  withdrawalAddress: 'mrVH2AMLph7FbZWQbFLcBrm57zajzWRxeu',
  timeCreation: '1521572056148',
  status: 'live',
  coin: '1',
  depositAddress: '2Mxy6Fp13GQC1dopbZhpd9N7BsWgdBt4wsq',
  rate: '0.0175',
  isBuy: 'true',
  BTC: '40000',
  owner: 'customer',
  expiration: '1521572086148',
  returnAddress: 'n3Nb6QnV13js7uhYZMMRyxAVH1wGzScUo8',
  pubkeyOracle: '036e98602c209d4cab2f20a626b3166b7332fe7378f035629896b31b21c0add4a1',
  amountOut: '0.022857142857142857',
  quantity: '0.0004',
  price: '0.0175',
  userkey: '03b45603b704bc46f63243e4ff933d8d0ed32de23f328db99a13dc208ecf2afde0',
  orderId: 'e8fa783a-7777-4492-a1f8-80452eb38c42',
  coinOut: 'LTC',
  pubkeyArbiter: '037df3728c03e1a86c0a387d5ee364f0a1eb7f55c7a2bfbdee6da9565bec82d5f3',
  amountIn: '0.0004',
  arbiterPubKey: '037df3728c03e1a86c0a387d5ee364f0a1eb7f55c7a2bfbdee6da9565bec82d5f3',
  coinIn: 'BTC'
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

`POST '/api/v1/order/:orderId'`

### URL Parameters

Parameter | Description
--------- | -----------
order id | order id





## Post a new limit order

> inputs: user order object

```json
{
  "expiration": 0.5,
  "pair": "BTC_LTC",
  "amountIn": 0.0004,
  "rate": 0.0175,
  "pubkey": "03b45603b704bc46f63243e4ff933d8d0ed32de23f328db99a13dc208ecf2afde0",
  "signingPub": "1H7za8vEu6MWeE44oz1yJ5oaDySu9Sdopn",
  "signingPriv": "L1vdhBUkoVkec6Qcc6quxaaimB5VCvS9hk6ppuypNWcbzW8bNn8P",
  "returnAddress": "mhMXrSoD5KQ9sS1WmHzTXQPzHEQAAerpDJ",
  "withdrawalAddress": "mfvPcPLx2DKLjrj1FrxmVsPeicHciWDWHF"
}
```

> successful outputs:

```json
{
  "orderId": "4a2ecf4c-0aab-4ef1-b930-545113ce23cc",
  "pubkeyCustomer": "03b45603b704bc46f63243e4ff933d8d0ed32de23f328db99a13dc208ecf2afde0",
  "pubkeyArbiter": "030e1ae752642f7d1d101f4df72e6495d71abc625a3869bad8d9f36bfa9c02a91e",
  "depositAddress": "2N47cxQbvku1iFV4fJ7VjCbfNqYPzy5dcRA",
  "returnAddress": "mhMXrSoD5KQ9sS1WmHzTXQPzHEQAAerpDJ",
  "withdrawalAddress": "mfvPcPLx2DKLjrj1FrxmVsPeicHciWDWHF",
  "maxDeposit": "Not set",
  "minDeposit": "Not set",
  "coinIn": "BTC",
  "coinOut": "LTC",
  "amountIn": 0.0004,
  "rate": 0.0175,
  "pair": "BTC_LTC"
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

`POST '/api/v1/limitorder'`

### URL Parameters

Parameter | Description
--------- | -----------
order object | order object






## Post a cancel order

> inputs:


```json
"28136c90-835e-4769-b94e-8946387fa091"
```

> successful outputs:

```json
???
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

`POST '/api/v1/cancel'`

### URL Parameters

Parameter | Description
--------- | -----------
order id | order id






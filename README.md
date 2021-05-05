# GDOGE | REST API

The GDOGE REST API is a set of endpoints used by market aggregators (e.g. coinmarketcap.com). 


The API is designed around the CoinMarketCap 
[requirements document](https://docs.google.com/document/d/1S4urpzUnO2t7DmS_1dc4EL4tgnnbTObPYXvDeBnukCg).


The API is designed by following JustLiquidity/swapliquidity-api guide

# Endpoints

All pairs consist of two different tokens GDOGE / WBNB pairs.

The canonical WBNB address is `0xbb4CdB9CBd36B01bD1cBaEBF2De08d9173bc095c`.

## [`/summary`](https://api.gdoge.finance/api/v1/summary)



### Request

`GET https://api.gdoge.finance/api/v1/summary`

### Response

```json5
{
  "0x..._0x...": {                  // the asset ids of the BEP20 tokens (i.e. token addresses), joined by an underscore
    "last_price": "1.234",          // denominated in token0/token1
    "base_volume": "123.456",       // last 24h volume denominated in token0
    "quote_volume": "1234.56"       // last 24h volume denominated in token1
    "pair_liquidity": "1234.56"     // Pair liquidity in USD
  },
  // ...
}
```

## [`/totalliquidity`](https://api.gdoge.finance/api/v1/totalliquidity)

Returns the total liquidity in USD value.
Results are edge cached for 24 hours.

### Request

`GET https://api.gdoge.finance/api/v1/totalliquidity`

### Response

```json5
{
  "result": {
    "totalLiquidityUSD": "...", // Total liquidity in USD
  }
}
```

## [`/assets`](https://api.gdoge.finance/api/v1/assets)


### Request

`GET https://api.gdoge.finance/api/v1/assets`

### Response

```json5
{
  // ...,
  "0x...": {              // the address of the BEP20 token
    "name": "...",        // not necesssarily included for BEP20 tokens
    "symbol": "...",      // not necesssarily included for BEP20 tokens
    "id": "0x...",        // the address of the BEP20 token
    "maker_fee": "0",     // always 0
    "taker_fee": "0.003", // always 0.003 i.e. .3%
  },
  // ...
}
```

## [`/tickers`](https://api.gdoge.finance/api/v1/tickers)

Results are edge cached for 1 minute.

### Request

`GET https://api.gdoge.finance/api/v1/tickers`

### Response

```json5
{
  "0x..._0x...": {                    // the asset ids of BNB and BEP20 tokens, joined by an underscore
    "base_name": "...",             // token0 name
    "base_symbol": "...",           // token0 symbol
    "base_id": "0x...",             // token0 address
    "quote_name": "...",            // token1 name
    "quote_symbol": "...",          // token1 symbol
    "quote_id": "0x...",            // token1 address
    "last_price": "1.234",          // the mid price as token1/token0
    "base_volume": "123.456",       // denominated in token0
    "quote_volume": "1234.56"       // denominated in token1
  },
  // ...
}
```

## [`/trades`](https://api.gdoge.finance/api/v1/trades)

Returns last 10 trades on the Pancake DEX

Results are edge cached for 15 minutes.



### Request

`GET https://api.gdoge.finance/api/v1/trades`

```
```

## [`/circulation`](https://api.gdoge.finance/api/v1/circulation)

Returns circulation supply of the token based on burned tokens.

Burn Address: https://bscscan.com/token/0xc35f46aAEb8aD17bCbAa78c03540FEffa44790Cb?a=0x000000000000000000000000000000000000dead

Results are edge cached for 15 minutes.



### Request

`GET https://api.gdoge.finance/api/v1/circulation`

```

### Response

```json5
{
  "circulation": "amount_of_tokens"     
}
```

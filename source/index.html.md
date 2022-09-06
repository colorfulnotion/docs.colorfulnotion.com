---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://polkaholic.io/apikeys'>Sign Up for a Developer Key</a>

includes:
  - sampleObject
  - errorcode

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Polkaholic API
---

# Introduction

Welcome to [Polkaholic](http://polkaholic.io) API!

Polkaholic API gives you powerful access to over 40+ networks in Polkadot and Kusama ecosystem. Get a [free API key](https://polkaholic.io/apikeys) today and start building your own dApps!

Got any questions? Find us on [Matrix](https://matrix.to/#/#polkaholic:matrix.org): `#polkaholic:matrix.org`


<aside class="success">
All pages on the polkaholic.io web site have API call information displayed at the bottom, and are documented here.
</aside>

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request,
# such as https://api.polkaholic.io/<Endpoint>/<Parameters>
curl "https://api.polkaholic.io/" \
  -H "Authorization: YOUR-API-KEY"
```

> Make sure to replace `YOUR-API-KEY` with your API key.

Polkaholic uses API keys to allow access to the API. You can obtain a free Polkaholic API key at the [Developer Portal](https://polkaholic.io/apikeys). We expect all API requests to the server include an API key in the header:

`Authorization: YOUR-API-KEY`

<aside class="notice">
You must replace <code>YOUR-API-KEY</code> with your personal API key.
</aside>



# Chains

## Supported Chains

As of 2022-06-27, Polkaholic supports Polkadot & 17 polkadot-parachains, plus Kusama & 28 kusama-parachains - 47 chains in total.

<aside class="success">
We coined the "ChainID" as a convenient way to identify any given chain using the following rule:  
</aside>

| Chain               | ChainID       | ChainID Description|
|---------------------|:-------------:|--------------------|
|Polkadot (Mainnet)   |  0            | For Polkadot Mainnet (or the relaychain), use Polkadot's prefix as chainID (Prefix: 0)
|Kusama (Mainnet)     |  2            | For Kusama Mainnet (or the relaychain), use Kusama's prefix as chainID (Prefix: 2)
|Polkadot - parachain |  paraID       | Use its Polkadot paraID as chainID. A valid chainID for polkadot-parachain should be 4-digits long and in the range of [1000-2xxx]
|Kusama - parachain   |  20000+paraID | Use its Kusama paraID *Plus* 20000 as chainID. A valid chainID for kusama-parachain should be 5-digits long and in the range of [21000-22xxx]

You can query any supported chain either by its id or chainID.

### Supported Polkadot Chains

| Chain              | id          | chainID | Polkaholic Explorer                                            | Prefix |
|--------------------|-------------|---------|----------------------------------------------------------------|--------|
| Polkadot           | polkadot    |       0 | [polkadot.polkaholic.io](https://polkadot.polkaholic.io)       |      0 |
| Statemint          | statemint   |    1000 | [statemint.polkaholic.io](https://statemint.polkaholic.io)     |      0 |
| Acala              | acala       |    2000 | [acala.polkaholic.io](https://acala.polkaholic.io)             |     10 |
| Clover             | clover      |    2002 | [clover.polkaholic.io](https://clover.polkaholic.io)           |    128 |
| Moonbeam           | moonbeam    |    2004 | [moonbeam.polkaholic.io](https://moonbeam.polkaholic.io)       |   1284 |
| Astar              | astar       |    2006 | [astar.polkaholic.io](https://astar.polkaholic.io)             |      5 |
| Kapex*             | kapex       |    2007 | [kapex.polkaholic.io](https://kapex.polkaholic.io)             |   2007 |
| Equilibrium        | equilibrium |    2011 | [equilibrium.polkaholic.io](https://equilibrium.polkaholic.io) |     68 |
| Parallel           | parallel    |    2012 | [parallel.polkaholic.io](https://parallel.polkaholic.io)       |    172 |
| Litentry           | litentry    |    2013 | [litentry.polkaholic.io](https://litentry.polkaholic.io)       |     31 |
| Composable Finance | composable  |    2019 | [composable.polkaholic.io](https://composable.polkaholic.io)   |     50 |
| Efinity           | efinity     |    2021 | [efinity.polkaholic.io](https://efinity.polkaholic.io)         |   1110 |
| Nodle              | nodle       |    2026 | [nodle.polkaholic.io](https://nodle.polkaholic.io)             |     37 |
| Ares*              | ares        |    2028 | [ares.polkaholic.io](https://ares.polkaholic.io)               |     34 |
| Bifrost-Polkadot*  | bifrost-dot |    2030 | [bifrost-dot.polkaholic.io](https://bifrost-dot.polkaholic.io) |      6 |
| Centrifuge         | centrifuge  |    2031 | [centrifuge.polkaholic.io](https://centrifuge.polkaholic.io)   |     36 |
| Interlay           | interlay    |    2032 | [interlay.polkaholic.io](https://interlay.polkaholic.io)       |   2032 |
| HydraDX            | hydradx     |    2034 | [hydradx.polkaholic.io](https://hydradx.polkaholic.io)         |     63 |
| Phala              | phala       |    2035 | [phala.polkaholic.io](https://phala.polkaholic.io)             |     30 |
| Unique             | unique      |    2037 | [unique.polkaholic.io](https://unique.polkaholic.io)           |   7391 |
| Polkadex*          | polkadex    |    2040 | [polkadex.polkaholic.io](https://polkadex.polkaholic.io)       |     88 |
| Origin Trail*      | origintrail |    2043 | [origintrail.polkaholic.io](https://origintrail.polkaholic.io) |    101 |

### Supported Kusama Chains

| Chain               | id                | chainID | Polkaholic Explorer                                                        | Prefix |
|---------------------|-------------------|---------|----------------------------------------------------------------------------|--------|
| Kusama              | kusama            |       2 | [kusama.polkaholic.io](https://kusama.polkaholic.io)                       |      2 |
| Statemine           | statemine         |   21000 | [statemine.polkaholic.io](https://statemine.polkaholic.io)                 |      2 |
| Encointer           | encointer         |   21001 | [encointer.polkaholic.io](https://encointer.polkaholic.io)                 |      2 |
| Karura              | karura            |   22000 | [karura.polkaholic.io](https://karura.polkaholic.io)                       |      8 |
| Bifrost-Kusama      | bifrost-ksm       |   22001 | [bifrost-ksm.polkaholic.io](https://bifrost-ksm.polkaholic.io)             |      6 |
| Khala               | khala             |   22004 | [khala.polkaholic.io](https://khala.polkaholic.io)                         |     30 |
| Shiden              | shiden            |   22007 | [shiden.polkaholic.io](https://shiden.polkaholic.io)                       |      5 |
| Mars*               | mars              |   22008 | [mars.polkaholic.io](https://mars.polkaholic.io)                           |     42 |
| Sora Kusama*        | sora              |   22011 | [sora.polkaholic.io](https://sora.polkaholic.io)                           |     69 |
| Crust Shadow*       | shadow            |   22012 | [shadow.polkaholic.io](https://shadow.polkaholic.io)                       |     66 |
| Integritee          | integritee        |   22015 | [integritee.polkaholic.io](https://integritee.polkaholic.io)               |     13 |
| SubGame Gamma*      | subgame-gamma     |   22018 | [subgame-gamma.polkaholic.io](https://subgame-gamma.polkaholic.io)         |     27 |
| Moonriver           | moonriver         |   22023 | [moonriver.polkaholic.io](https://moonriver.polkaholic.io)                 |   1285 |
| Robonomics          | robonomics        |   22048 | [robonomics.polkaholic.io](https://robonomics.polkaholic.io)               |     32 |
| Calamari            | calamari          |   22084 | [calamari.polkaholic.io](https://calamari.polkaholic.io)                   |     78 |
| Parallel Heiko      | parallel-heiko    |   22085 | [parallel-heiko.polkaholic.io](https://parallel-heiko.polkaholic.io)       |    110 |
| KILT Spiritnet      | spiritnet         |   22086 | [spiritnet.polkaholic.io](https://spiritnet.polkaholic.io)                 |     38 |
| Picasso             | picasso           |   22087 | [picasso.polkaholic.io](https://picasso.polkaholic.io)                     |     49 |
| Altair              | altair            |   22088 | [altair.polkaholic.io](https://altair.polkaholic.io)                       |    136 |
| Basilisk            | basilisk          |   22090 | [basilisk.polkaholic.io](https://basilisk.polkaholic.io)                   |  10041 |
| Kintsugi            | kintsugi          |   22092 | [kintsugi.polkaholic.io](https://kintsugi.polkaholic.io)                   |   2092 |
| Unorthodox*         | unorthodox        |   22094 | [unorthodox.polkaholic.io](https://unorthodox.polkaholic.io)               |     42 |
| Quartz              | quartz            |   22095 | [quartz.polkaholic.io](https://quartz.polkaholic.io)                       |    255 |
| Bit.Country Pioneer | bitcountrypioneer |   22096 | [bitcountrypioneer.polkaholic.io](https://bitcountrypioneer.polkaholic.io) |    268 |
| SubsocialX*         | subsocialx        |   22100 | [subsocialx.polkaholic.io](https://subsocialx.polkaholic.io)               |     28 |
| Zeitgeist           | zeitgeist         |   22101 | [zeitgeist.polkaholic.io](https://zeitgeist.polkaholic.io)                 |     73 |
| Pichiu              | pichiu            |   22102 | [pichiu.polkaholic.io](https://pichiu.polkaholic.io)                       |     42 |
| Darwinia Crab       | crab              |   22105 | [crab.polkaholic.io](https://crab.polkaholic.io)                           |     42 |
| Litmus              | litmus            |   22106 | [litmus.polkaholic.io](https://litmus.polkaholic.io)                       |    131 |
| Kico                | kico              |   22107 | [kico.polkaholic.io](https://kico.polkaholic.io)                           |     42 |
| Mangata*            | mangatax          |   22110 | [mangatax.polkaholic.io](https://mangatax.polkaholic.io)                   |     42 |
| Turing              | turing            |   22114 | [turing.polkaholic.io](https://turing.polkaholic.io)                       |     51 |
| Dora Factory        | dorafactory       |   22115 | [dorafactory.polkaholic.io](https://dorafactory.polkaholic.io)             |    128 |
| Tanganika*          | tanganika         |   22116 | [tanganika.polkaholic.io](https://tanganika.polkaholic.io)                 |     33 |
| Listen*             | listen            |   22118 | [listen.polkaholic.io](https://listen.polkaholic.io)                       |     42 |

*_Unstable Chain_: These chains are unstable/unreachable; therefore API services are limited for these chains.

(Last updated: 2022-06-27)

<aside class="notice">
Didn't find the chain you are looking for? Send us an email <a href = "mailto:info@polkaholic.io">info@polkaholic.io</a> or find us on <a href = "https://matrix.to/#/#polkaholic:matrix.org">Matrix</a>. We will index it!
</aside>

## Get All Chains

```shell
curl "https://api.polkaholic.io/chains" \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (chainInfo)

```json
[
  {
    "id": "polkadot",
    "prefix": 0,
    "chainID": 0,
    "chainName": "Polkadot",
    "symbol": "DOT",
    "lastFinalizedTS": 1656359324,
    "iconUrl": "https://cdn.polkaholic.io/polkadot.png",
    "numExtrinsics": 27523464,
    "numSignedExtrinsics": 9679985,
    "numTransfers": 7890948,
    "numEvents": 116538632,
    "numHolders": 2101379,
    "relayChain": "polkadot",
    "totalIssuance": 1167630208,
    "isEVM": 0,
    "blocksCovered": 10924487,
    "blocksFinalized": 10924484,
    "crawlingStatus": ""
  },
  {
    "id": "statemint",
    "prefix": 0,
    "chainID": 1000,
    "chainName": "Statemint",
    "symbol": "DOT",
    "lastFinalizedTS": 1656359324,
    "iconUrl": "https://cdn.polkaholic.io/statemint.svg",
    "numExtrinsics": 2853812,
    "numSignedExtrinsics": 157,
    "numTransfers": 39,
    "numEvents": 2855459,
    "numHolders": 52,
    "relayChain": "polkadot",
    "totalIssuance": 0,
    "isEVM": 0,
    "blocksCovered": 1581649,
    "blocksFinalized": 1581647,
    "crawlingStatus": ""
  },
  {
    "id": "acala",
    "prefix": 10,
    "chainID": 2000,
    "chainName": "Acala",
    "symbol": "ACA",
    "lastFinalizedTS": 1656359324,
    "iconUrl": "https://cdn.polkaholic.io/acala.png",
    "numExtrinsics": 3769800,
    "numSignedExtrinsics": 1135331,
    "numTransfers": 2223553,
    "numEvents": 16680798,
    "numHolders": 174983,
    "relayChain": "polkadot",
    "totalIssuance": 1000000000,
    "isEVM": 0,
    "blocksCovered": 1315579,
    "blocksFinalized": 1315577,
    "crawlingStatus": ""
  },
  ...
]  
```

This endpoint returns all supported chains.

### HTTP Request

`GET http://api.polkaholic.io/chains`

### Query Parameters

None


### Response Description

Attribute       | Description
--------------- | -----------
id              | The "Human-readble" identifier of the give chain (same as Talisman's chain id)    
chainID         | The Alternative identifiers of the given chain
relayChain      | The corresponding relaychain of the given parachain
isEVM           | Whether the chain supports Ethereum Pallet
prefix          | The Chain prefix for SS58 address    |  
blocksCovered   | The most recent block (including unfinalized block)
blocksFinalized | The most recent finalized block
crawlingStatus  | The Crawling Exception Status, if any.


## Get ChainInfo and Recent Blocks


```shell
# querying ChainIdentifier "2004" is equivalent to querying "moonbeam"

curl "https://api.polkaholic.io/chain/2004" \
  -H "Authorization: YOUR-API-KEY"

curl "https://api.polkaholic.io/chain/moonbeam" \
  -H "Authorization: YOUR-API-KEY"  
```

> Example Response (chainInfo + recentBlocks meta)

```json
{
  "chain": {
    "id": "moonbeam",
    "chainID": 2004,
    "chainName": "Moonbeam",
    "blocksCovered": 1183920,
    "blocksFinalized": 1183918,
    "symbol": "GLMR",
    "lastCrawlDT": "2022-06-07T02:11:23.000Z",
    "lastFinalizedDT": "2022-06-07T02:11:18.000Z",
    "iconUrl": "https://cdn.polkaholic.io/moonbeam.png",
    "numHolders": 258441,
    "totalIssuance": 1008444352,
    "numExtrinsics": 10219073,
    "numExtrinsics7d": 376230,
    "numExtrinsics30d": 1898693,
    "numSignedExtrinsics": 78388,
    "numSignedExtrinsics7d": 1817,
    "numSignedExtrinsics30d": 10579,
    "numTransfers": 2844554,
    "numTransfers7d": 113064,
    "numTransfers30d": 412976,
    "numEvents": 96357429,
    "numEvents7d": 3859386,
    "numEvents30d": 19047660,
    "numXCMTransferIncoming": 10,
    "numXCMTransferIncoming7d": 1,
    "numXCMTransferIncoming30d": 9,
    "numXCMTransferOutgoing": 2596,
    "numXCMTransferOutgoing7d": 775,
    "numXCMTransferOutgoing30d": 1833,
    "valXCMTransferIncomingUSD": 7.22012,
    "valXCMTransferIncomingUSD7d": 0.126401,
    "valXCMTransferIncomingUSD30d": 7.13134,
    "valXCMTransferOutgoingUSD": 8687910,
    "valXCMTransferOutgoingUSD7d": 4127010,
    "valXCMTransferOutgoingUSD30d": 6099510,
    "isEVM": 1,
    "numTransactionsEVM": 6379471,
    "numTransactionsEVM7d": 227816,
    "numTransactionsEVM30d": 1217181,
    "numReceiptsEVM": 24959951,
    "numReceiptsEVM7d": 966777,
    "numReceiptsEVM30d": 4846247,
    "gasUsed": 633024,
    "gasUsed7d": 649128,
    "gasUsed30d": 751764,
    "gasLimit": 14642739,
    "gasLimit7d": 14995937,
    "gasLimit30d": 14678751
  },
  "blocks": [
    {
      "blockNumber": 1183920,
      "finalized": 0,
      "blockHash": [
        "0xa0f7ebebb33c22290d2b2d55ba977b58665d0027eeb1e498917bd9d51beb598f",
        "0xce4a2c4697af5a31745d80fcdd6ffe94d34935f165232428031ea6fdb6ac4f83"
      ],
      "blockDT": null,
      "blockTS": null,
      "numExtrinsics": 3,
      "numEvents": 3,
      "numTransfers": 0,
      "numSignedExtrinsics": 0
    },
    {
      "blockNumber": 1183919,
      "finalized": 0,
      "blockHash": [
        "0x7df10bd19c59b89d0c0d3a74604aa3cf5985f347c585867afa510e00fb8a5037",
        "0xe2152dc362325f050a0cb2d8397db120372b3725415735f4c28301d0bb1eff84"
      ],
      "blockDT": null,
      "blockTS": null,
      "numExtrinsics": 6,
      "numEvents": 44,
      "numTransfers": 2,
      "numSignedExtrinsics": 0
    },
    {
      "blockNumber": 1183918,
      "finalized": 1,
      "blockHash": "0xc5e166c8566fec4b2cc88728d2547d181bc156056a6b62e72ff18e8f9bc4d7fd",
      "blockDT": "2022-06-07T02:10:49.000Z",
      "blockTS": 1654542649,
      "numExtrinsics": 6,
      "numEvents": 35,
      "numTransfers": 0,
      "numSignedExtrinsics": 0
    }]
}


// Note: (numTransactionsEVM, numReceiptsEVM, gasUsed, gasLimit) are only available for EVM Chain

```

This endpoint retrieves the target chain's basicInfo and its recent blockHashes (both finalized and unfinalized).

<aside class="notice">The list of supported chains can be retrieved from the <code>/chains</code> endpoint. </aside>

### HTTP Request

`GET https://api.polkaholic.io/chain/<ChainIdentifier>`

### Path Parameters

Parameter | Description
--------- | -----------
ChainIdentifier | The identifier of the chain to retrieve data about

### Response Description

Attribute | Description
--------- | -----------
chain | Basic ChainInfo (i.e. Total Issuance, symbol and # of {extrinsics, event, transfers, xcmtransfers} over the {last 7days, last 30days, all time)  
blocks  |  latest blockHashes (both finalized and unfinalized) |  

# Block

## Get Block

```shell
curl "https://api.polkaholic.io/block/moonbeam/453100" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"

# querying ChainIdentifier "moonbeam" is equivalent to querying 2004
curl "https://api.polkaholic.io/block/2004/453100" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"

```

> Example Response (block)

```json
{
  "header": {
    "parentHash": "0x662e1d038b6549c4bfa6e00e35674ec373844fb40be20703b581663aeb723cf6",
    "number": 453100,
    "stateRoot": "0x818c89ee2e339969ed9c614c164c8412f7ae6086cdcd34ab6e0622ea8a576a38",
    "extrinsicsRoot": "0x812e43ce0ef4058e016546652abcd42e4ef66462b6095c34d6a6f5454ecd51e2",
    "digest": {
      "logs": [...]
    }
  },
  "extrinsics": [...],
  "number": 453100,
  "hash": "0x946176c181e19cf6160a3c91496cc80e7b444d380286e02b074a4ef0e9aec0e9",
  "blockTS": 1645420248,
  "finalized": true,
  "specVersion": 1103,
  "evmBlock": {
    "author": "0x1dc2ae28998dcbcd496a96883552bd0febc4af32",
    "difficulty": "0",
    "extraData": "0x",
    "gasLimit": 15000000,
    "gasUsed": 3818582,
    "hash": "0x753a7314e132d55cc0f13769f65326f3e8010a0c8d1f3ed0bf7940670291bba6",
    "logsBloom": "...",
    "miner": "0x1Dc2Ae28998dcBcD496a96883552bd0fEBC4af32",
    "number": 453100,
    "parentHash": "0xa8a0cd9e557ed568cc2a56cdfb66c0fbc379d8555b735c5c27421d6458972321",
    "receiptsRoot": "0x6e6eb45c343e5940da3c41f0f82a061f7df1d8ae0de7db87a4f681fe205519bf",
    "sealFields": [...],
    "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
    "size": 3339,
    "stateRoot": "0x882936cd0cc9185d53da9459da056914ac14bef16c2e1508bc8067ffd13dc5a7",
    "timestamp": 1645420248,
    "totalDifficulty": "0",
    "transactions": [...],
    "transactionsRoot": "0xf67c9ba94e41500a41e31a3619a0a52a4a1610eb94f3931e4c7908b1a37755cd",
    "uncles": []
  }
}
```

This endpoint accesses a specific account.

### HTTP Request

`GET https://api.polkaholic.io/block/<ChainIdentifier>/<BlockNumber>`

### Path Parameters

Parameter | Description
--------- | -----------
ChainIdentifier | The identifier of the chain to retrieve data about
BlockNumber | The Block Number to retrieve data about


### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description

Attribute | Description | Sample Object |
--------- | ----------- | :-:
header | The substrate block header| - |
extrinsics  |  a list of decorated extrinsics (including unsigned and signed) | [decoratedExtrinsics](#get-transaction-substratetx)
finalized   |  whether the block is finalized | -
specVersion  | The specVersion at the time when the block is proposed  |  -
evmBlock  | The evm block included at this block height (only available if the chain has enabled ethereum pallet)  |  [decoratedEvmBlock](#evmblock)


# Transaction

## Get Transaction (substrateTX)

```shell
# query substrateTx
curl "https://api.polkaholic.io/tx/0x044e63a8548c51bac4f3cdf71cc3bc31e63b460f7652030604aee4361f1b1878" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (SubstrateTx)

```json
{
  "chainID": 2,
  "id": "kusama",
  "chainName": "Kusama",
  "extrinsicHash": "0x044e63a8548c51bac4f3cdf71cc3bc31e63b460f7652030604aee4361f1b1878",
  "extrinsicID": "10363322-3",
  "blockNumber": 10363322,
  "ts": 1638562530,
  "blockHash": "0xea65c222481f4cb998dd9a65105ea2d6f56efcd015f0df3d94dc660d960cb5b9",
  "signer": "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
  "fromAddress": "0x74df9177b1360bf0c07952ffb2d37817366adf8900e3bb90287b9784fda3e045",
  "signature": {
    "sr25519": "0xd6bc93598c48c8def0f6852d8263b2f5c3a0b7d2c368ee3c0310c17d99925845acc55e2b52ca2b6325b1e6e3a7a8d88af36afc560c0818441af0be3957a77084"
  },
  "lifetime": {
    "isImmortal": 0,
    "birth": 10363317,
    "death": 10363381
  },
  "nonce": 375,
  "tip": 0,
  "fee": 0.000115998897,
  "chainSymbol": "KSM",
  "feeUSD": 0.014009882784072,
  "priceUSD": 120.776,
  "priceUSDCurrent": 69.8233,
  "result": 1,
  "status": "finalized",
  "section": "utility",
  "method": "batchAll",
  "params": {
    "calls": [
      {
        "callIndex": "0x4901",
        "section": "crowdloan",
        "method": "contribute",
        "args": {
          "index": 2101,
          "value": 8300000000000,
          "signature": null
        }
      },
      {
        "callIndex": "0x0001",
        "section": "system",
        "method": "remark",
        "args": {
          "remark": "0x526c56466332314363574a6864586c6a526d6c714e6c6c48524452724d3364425a324a57546e5130616d466f6358633056574e6164307477643235615445343d2d333232663464653630336538336435663735316332383361346138646664316239366230633932383362393562626664376665653938656130393035383464642d492068617665207265616420616e6420616772656520746f20746865207465726d7320666f756e642061742068747470733a2f2f7a65697467656973742e706d2f43726f77646c6f616e5465726d732e706466"
        }
      }
    ]
  },
  "events":[...],
  "decodedParams": [
    {
      "section": "crowdloan",
      "method": "contribute",
      "para": {
        "paraId": 2101,
        "name": "Zeitgeist",
        "relayChain": "Kusama",
        "relayChainSymbol": "KSM"
      },
      "value": "8.3"
    },
    {
      "section": "system",
      "method": "remark",
      "remark": "RlVFc21CcWJhdXljRmlqNllHRDRrM3dBZ2JWTnQ0amFocXc0VWNad0twd25aTE4=-322f4de603e83d5f751c283a4a8dfd1b96b0c9283b95bbfd7fee98ea090584dd-I have read and agree to the terms found at https://zeitgeist.pm/CrowdloanTerms.pdf"
    }
  ],
  "specVersion": 9122
}
```

This endpoint accesses a specific transaction using the TxHash.

### Glossary

Attribute | Description
--------- | -----------
TxHash | The 32 bytes hash that identify a Substrate extrinsic or EVM transaction |
extrinsicHash | The 32 bytes Blake2 hash of SCALE encoded Substrate extrinsic |
transactionHash | The 32 bytes keccak256 hash of RLP encoded EVM Transaction |
extrinsicID | The 'blockHeight-extrinsicIndex' that uniquely identity an Substrate extrinsic on a chain  |

<aside class="notice">
Both Substrate Extrinsic and EVM transactions are searchable by its TxHash; to avoid confusion, we use <code>extrinsicHash</code> and <code>transactionHash</code>to differentiate these two in the doc.
</aside>

### HTTP Request

`GET https://api.polkaholic.io/tx/<TxHash>`

### Path Parameters

Parameter | Description |
--------- | -----------
TxHash | The Transaction Hash to retrieve data about, can be either Substrate's extrinsicHash or EVM's transactionHash

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description (Decorated SubStrate Extrinsic)

Attribute | Description | Sample Object |
--------- | ----------- | :-: |
status  |  Current extrinsic status {pending, unfinalized, finalized, false} | -
evm  |  The corresponding {from, to, transactionHash} that are directly linked to this extrinsic [only available for ethereum(Transact) call] | [EVMInfo](#evminfo)  
section  | The module_section or pallet called by the extrinsics  | ex: "utility"
method  |  The module_function or method called by the extrinsics | ex: "batchAll"
params | The input parameters of the extrinsics *Note: may include recursive calls | -
decodedParams  |  The auto-decorated params based on available info on chain  | [DecodedParams](#decodedparams)
events  | A list of decorated events attached to this extrinsic | [DecoratedEvents](#decoratedevents)
specVersion  | The runtime verison at the time of the extrinsic |  -

<aside class="notice">
Function like <code>utility:batchAll</code>,<code>proxy:proxy</code>,<code>multisig:asMulti</code>,<code>sudo:sudo</code>, <code>sudo:sudoAs</code> and etc are recursive calls - which will have recursive {section, method, callIndex} within the params.
</aside>

## Get Transaction (evmTX)

```shell
# query evmTx
curl "https://api.polkaholic.io/tx/0x8b91d038421d5aba4b3a651d70923fb0d41423b914d6dad910637aa2c9a2ad70" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (evmTx)

```json
{
  "chainID": 2004,
  "transactionHash": "0x8b91d038421d5aba4b3a651d70923fb0d41423b914d6dad910637aa2c9a2ad70",
  "substrate": {
    "extrinsicID": "805873-6",
    "extrinsicHash": "0x514fbbb8dc531c4ef9adda34f3d50586e2b345f35012ce1dc5a3c9c34a42b6f1"
  },
  "status": "finalized",
  "blockHash": "0x2bf090452522c4b29fc86ee38ff14116c9606951dc503c9074522c993bb49c89",
  "blockNumber": 805873,
  "transactionIndex": 3,
  "timestamp": 1649793690,
  "from": "0xf3521DE8b160Bf2EFb71840638C146Ba6d4dc495",
  "to": "0x96b244391D98B62D19aE89b1A4dCcf0fc56970C7",
  "creates": null,
  "transfers": [
    {
      "type": "ERC20",
      "from": "0xf3521de8b160bf2efb71840638c146ba6d4dc495",
      "to": "0x61b4cec9925b1397b64dece8f898047eed0f7a07",
      "value": 180,
      "tokenAddress": "0xcd3B51D98478D53F4515A306bE565c6EebeF1D58",
      "assetInfo": {
        "assetType": "ERC20",
        "assetName": "Beamswap Token",
        "numHolders": 17323,
        "asset": "0xcd3b51d98478d53f4515a306be565c6eebef1d58",
        "symbol": "GLINT",
        "decimals": 18,
        "chainID": 2004,
        "chainName": "Moonbeam",
        "assetChain": "0xcd3b51d98478d53f4515a306be565c6eebef1d58~2004",
        "isUSD": 0,
        "priceUSDpaths": [
          [
            {
              "dest": "0x818ec0a7fe18ff94269904fced6ae3dae6d6dc0b",
              "symbol": "USDC"
            },
            {
              "route": "0x61b4cec9925b1397b64dece8f898047eed0f7a07",
              "dest": "0xcd3b51d98478d53f4515a306be565c6eebef1d58",
              "symbol": "BEAM-LP",
              "token0Symbol": "USDC",
              "token1Symbol": "GLINT",
              "s": 1
            }
          ]
        ],
        "nativeAssetChain": null
      },
      "valueUSD": 0.8568918,
      "priceUSD": 0.00476051,
      "priceUSDCurrent": 0.00103048
    },
    ...
  ],
  "swaps": [
    {
      "type": "swapV2",
      "maker": "0x96b244391d98b62d19ae89b1a4dccf0fc56970c7",
      "taker": "0xb929914b89584b4081c7966ac6287636f7efd053",
      "amount0In": "0",
      "amount1In": "180000000000000000000",
      "amount0Out": "890638",
      "amount1Out": "0",
      "path": "token1 -> token0",
      "lpTokenAddress": "0x61B4cec9925B1397B64dEcE8F898047eEd0F7A07"
    },
    ...
  ],
  "value": 0,
  "fee": 0.016547941,
  "gasLimit": 253394,
  "gasUsed": 163841,
  "gasPrice": 101,
  "nonce": 576,
  "input": "0x18cbafe5000000000000000000000000000000000000000000000009c2007651b2500000000000000000000000000000000000000000000000000000036c6ee6f4008c0300000000000000000000000000000000000000000000000000000000000000a0000000000000000000000000f3521de8b160bf2efb71840638c146ba6d4dc495000000000000000000000000000000000000000000000000000000006255e1720000000000000000000000000000000000000000000000000000000000000003000000000000000000000000cd3b51d98478d53f4515a306be565c6eebef1d58000000000000000000000000818ec0a7fe18ff94269904fced6ae3dae6d6dc0b000000000000000000000000acc15dc74880c9944775448304b263d191c6077f",
  "decodedInput": {
    "decodeStatus": "success",
    "methodID": "0x18cbafe5",
    "signature": "swapExactTokensForETH(uint256 amountIn, uint256 amountOutMin, address[] path, address to, uint256 deadline)",
    "params": [
      {
        "name": "amountIn",
        "value": "180000000000000000000",
        "type": "uint256"
      },
      {
        "name": "amountOutMin",
        "value": "246694017813744643",
        "type": "uint256"
      },
      {
        "name": "path",
        "value": [
          "0xcd3b51d98478d53f4515a306be565c6eebef1d58",
          "0x818ec0a7fe18ff94269904fced6ae3dae6d6dc0b",
          "0xacc15dc74880c9944775448304b263d191c6077f"
        ],
        "type": "address[]"
      },
      {
        "name": "to",
        "value": "0xf3521de8b160bf2efb71840638c146ba6d4dc495",
        "type": "address"
      },
      {
        "name": "deadline",
        "value": "1649795442",
        "type": "uint256"
      }
    ]
  },
  "decodedLogs": [...],
  "chainName": "Moonbeam",
  "valueUSD": 0,
  "priceUSD": 3.44377,
  "priceUSDCurrent": 1.33467,
  "symbol": "GLMR",
  "feeUSD": 0.056987302777570005,
  "result": true
}
```

This endpoint accesses a specific transaction using the TxHash.

### HTTP Request

`GET https://api.polkaholic.io/tx/<TxHash>`

### Path Parameters

Parameter | Description |
--------- | -----------
TxHash | The Transaction Hash to retrieve data about, can be either Substrate's extrinsicHash or EVM's transactionHash

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description (Decorated EVM Transaction)

Attribute | Description | Sample Object
--------- | ----------- | :----:
status  |  unfinalized/finalized | - |
substrate  |  the corresponding SubStrate extrinsicID, extrinsicHash that initiate this transaction | [SubstrateInfo](#substrateinfo)
transfers | a list of ERC20/ERC721/ERC1155 transfer events found in the transaction | [Transfer](#transfers)
swaps  | a list of swap events found in the transaction (currently only support uniswapV2 format) | [Swap](#swaps)
decodedInput  | the auto-decorated txInput from this evm transaction | [DecodedInput](#decodedinput)
decodedLogs  | a list of auto-decorate logs from this evm transaction | [DecodedLogs](#decodedlogs)
result | whether the evmTx is successful

# Account

## Get Account

```shell
curl "https://api.polkaholic.io/account/0x74df9177b1360bf0c07952ffb2d37817366adf8900e3bb90287b9784fda3e045" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"

# with optional url params
curl "https://api.polkaholic.io/account/13eEyAEkyazXwKnh51DPgdBdTWB8FWm4bPpsCB17RJ3K5LNV?groups=realtime" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"  
```

> Example Response (account-realtime)

```json
[
  {
    "assetChain": "[{\"Token\":\"KAR\"},{\"Token\":\"KSM\"}]~22000",
    "assetInfo": {
      "assetType": "LiquidityPair",
      "assetName": "KAR/KSM",
      "numHolders": 4059,
      "asset": "[{\"Token\":\"KAR\"},{\"Token\":\"KSM\"}]",
      "symbol": "KAR/KSM",
      "decimals": 12,
      "token0": "{\"Token\":\"KAR\"}",
      "token0Symbol": "KAR",
      "token0Decimals": 12,
      "token1": "{\"Token\":\"KSM\"}",
      "token1Symbol": "KSM",
      "token1Decimals": 12,
      "chainID": 22000,
      "chainName": "Karura",
      "assetChain": "[{\"Token\":\"KAR\"},{\"Token\":\"KSM\"}]~22000",
      "isUSD": 0,
      "priceUSDpaths": false,
      "nativeAssetChain": null
    },
    "state": {
      "free": 26.369332612416,
      "freeUSD": 25.529846811135446,
      "rate": 0.9681643136889524,
      "balance": 26.369332612416,
      "balanceUSD": 25.529846811135446
    }
  },
  {
    "assetChain": "{\"Token\":\"DOT\"}~0",
    "assetInfo": {
      "assetType": "Token",
      "assetName": "DOT",
      "numHolders": 2060504,
      "asset": "{\"Token\":\"DOT\"}",
      "symbol": "DOT",
      "decimals": 10,
      "chainID": 0,
      "chainName": "Polkadot",
      "assetChain": "{\"Token\":\"DOT\"}~0",
      "isUSD": 0,
      "priceUSDpaths": false,
      "nativeAssetChain": null
    },
    "state": {
      "free": 2.3005476847,
      "freeUSD": 21.9165816168778,
      "rate": 9.52668,
      "transferable": 2.3005476847,
      "transferableUSD": 21.9165816168778,
      "balance": 2.3005476847,
      "balanceUSD": 21.9165816168778
    }
  },
  {
    "assetChain": "{\"Loan\":{\"Token\":\"LKSM\"}}~22000",
    "assetInfo": {
      "assetType": "Loan",
      "assetName": "Loan:LKSM",
      "numHolders": 3745,
      "asset": "{\"Loan\":{\"Token\":\"LKSM\"}}",
      "symbol": "Loan:LKSM",
      "decimals": 12,
      "chainID": 22000,
      "chainName": "Karura",
      "assetChain": "{\"Loan\":{\"Token\":\"LKSM\"}}~22000",
      "isUSD": 0,
      "priceUSDpaths": false,
      "nativeAssetChain": null
    },
    "state": {
      "debit": 0,
      "borrowedAsset": {
        "Token": "KUSD"
      },
      "exchangeRate": 0.10220861852460247,
      "exchangeRateCurrent": 0.10220861852460247
    }
  },
  {
    "assetChain": "{AssetKey}~chainID",
    "assetInfo" : {...},
    "state" : {...}
  },
  ...
]
```

This endpoint accesses a specific account.

<aside class="notice">The address input is the public key (64 hex characters, 66 with <code>0x</code> prefixed.</aside>

### HTTP Request

`GET https://api.polkaholic.io/account/<Address>`

### Path Parameters

Parameter | Description
--------- | -----------
Address | The Address (public key, SS58 address or nativeH160 address) to retrieve data about

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
group     | The group type to return by the API (see below) | Yes | 'realtime'
lookbackWindow     | TBA | Yes | 180
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Supported Query Group
Currently `/account` endpoint supprts [`realtime`,`balances`, `xcmtransfers`, `history`,`extrinsics`,`transfers`,`crowdloans`,`rewards`, `feed`] group type. Only *one* group type will be returned by the API at a time.


| Group Type | Description | Paginated | Return Sample |
| ---------  | ----------- | :-----------: |:-----------: |
| realtime  | Current account snapshot  | - | [e1]()  
| balances  | Historical Account Balance snapshots over the last N days (in USD)| - | [e2]()
| xcmtransfer | cross-chain transfers initiated by the account. | - | [e3]()
| history  | Historical account snapshots  | Yes | [e4]()
| extrinsics  | Extrinsics (including both substrateTX and evmTX) initiated by the account | Yes | [e5]()
| transfers  |Incoming transfers to the account  | Yes | [e6]()
| crowdloans  | direct crowdloans contributions made by the account   | Yes | [e7]()
| rewards  | staking rewards/panalties received by the account | Yes | [e8]()
| feed  | Extrinsics initiate by the accounts which an account follows | Yes |[e9]()



## Get Account (realtime)

Return all assets that are held by an account (realtime)

### HTTP Request

`GET https://api.polkaholic.io/account/realtime/<Address>`

```shell
curl "https://api.polkaholic.io/account/realtime/13Dh9XPwREhog65gkg2a2humtNhaaYRqgMp4Mf9jS7A6GK8m" \
  -H "Authorization: YOUR-API-KEY"
```

```json
[
  {
    "assetChain": "{\"Loan\":{\"LiquidCrowdloan\":\"13\"}}~2000",
    "assetInfo": {
      "assetType": "Loan",
      "assetName": "Loan:lcDOT",
      "numHolders": 3943,
      "asset": "{\"Loan\":{\"LiquidCrowdloan\":\"13\"}}",
      "symbol": "Loan:lcDOT",
      "decimals": 10,
      "chainID": 2000,
      "chainName": "Acala",
      "assetChain": "{\"Loan\":{\"LiquidCrowdloan\":\"13\"}}~2000",
      "isUSD": 0,
      "priceUSDpaths": false,
      "nativeAssetChain": null
    },
    "state": {
      "suppliedAsset": {
        "LiquidCrowdloan": "13"
      },
      "collateral": 98,
      "debit": 509.128962326125,
      "borrowedAsset": {
        "Token": "AUSD"
      },
      "collateralUSD": 610.19602,
      "collateralAssetRate": 6.22649,
      "rate": 6.22649,
      "exchangeRate": 0.10095082523777825,
      "exchangeRateCurrent": 0.10095082523777825,
      "borrowed": 51.39698889927603,
      "debitUSD": 51.39698889927603,
      "borrowedAssetRate": 1
    }
  },
  {
    "assetChain": "{AssetKey}~chainID",
    "assetInfo" : {...},
    "state" : {...}
  },
  ...
]
```

## Get Account (balances)

Return a list of balance snapshots for an account

### HTTP Request

`GET https://api.polkaholic.io/account/balances/<Address>`

```shell
curl "https://api.polkaholic.io/account/balances/13eEyAEkyazXwKnh51DPgdBdTWB8FWm4bPpsCB17RJ3K5LNV" \
  -H "Authorization: YOUR-API-KEY"
```

```json
[
  [
    1639003944000,
    795.5957981675581
  ],
  [
    1639090344000,
    854.8046148118644
  ],
  [
    1639176744000,
    843.1547779258111
  ],
  [
    1639263144000,
    859.7872766212897
  ],
  [
    unix_timestamp,
    accountBalanceUSD
  ],
  ...
]
```

## Get Account (XCM)

Return a list of XCM initiated by an account

### HTTP Request

`GET https://api.polkaholic.io/account/xcmtransfers/<Address>`

```shell
curl "https://api.polkaholic.io/account/xcmtransfers/13eEyAEkyazXwKnh51DPgdBdTWB8FWm4bPpsCB17RJ3K5LNV" \
  -H "Authorization: YOUR-API-KEY"
```

```json
[
  {
    "extrinsicHash": "0x424fb0b5e055b616795f687ecaf64feccc100958dacd065a8ac83097db557565",
    "extrinsicID": "1859804-2",
    "incomplete": 0,
    "status": "NonFinalizedSource",
    "sectionMethod": "polkadotXcm:limitedReserveTransferAssets",
    "section": "polkadotXcm",
    "method": "limitedReserveTransferAssets",
    "fromAddress": "0x74df9177b1360bf0c07952ffb2d37817366adf8900e3bb90287b9784fda3e045",
    "id": "statemine",
    "chainID": 21000,
    "chainName": "Statemine",
    "blockNumber": 1859804,
    "sourceTS": 1647826188,
    "destAddress": "0x74df9177b1360bf0c07952ffb2d37817366adf8900e3bb90287b9784fda3e045",
    "idDest": "karura",
    "chainIDDest": 22000,
    "chainDestName": "Karura",
    "blockNumberDest": 1662518,
    "destTS": 1647826201,
    "asset": "{\"Token\":\"ARIS\"}",
    "rawAsset": "{\"Token\":\"16\"}",
    "amountSent": 50000,
    "amountSentUSD": 0,
    "amountReceived": 49999.9936,
    "amountReceivedUSD": 0,
    "priceUSD": 0,
    "priceUSDCurrent": 0
  },
  ...
]    
```

## Get Account (history)

Return all assets that are held by an account at various snapshots (historical, paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/history/<Address>`

```shell
curl "https://api.polkaholic.io/account/history/0xd226e11422246c5211a79628246b114673e69c890bd5deca8f008e43f2b35743" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {
      "assetInfo": {
        "assetType": "CDP_Supply",
        "assetName": "CDP_Supply:sDOT",
        "numHolders": 2354,
        "asset": "{\"CDP_Supply\":{\"Token\":\"1001\"}}",
        "symbol": "CDP_Supply:sDOT",
        "decimals": 10,
        "chainID": 2012,
        "chainName": "Parallel",
        "assetChain": "{\"CDP_Supply\":{\"Token\":\"1001\"}}~2012",
        "isUSD": 0,
        "priceUSDpaths": false,
        "nativeAssetChain": null
      },
      "states": [
        [
          1651794972,
          {
            "isCollateral": 1,
            "adjustedVoucher": 2495.7600615601,
            "supplied": 49.91540524718345,
            "adjustedVoucherUSD": 728.0161855301707,
            "rate": 14.585,
            "balanceUSD": 728.0161855301707
          },
          {
            "chainID": 2012,
            "blockNumber": 899692,
            "extrinsicHash": "0x3d9aece2f3abe90f7364a29ef56465032108b219d57e17f72b3e10e29b2f7b41",
            "extrinsicID": "899692-2",
            "section": "loans",
            "method": "collateralAsset"
          }
        ],
        [
          1651794723,
          {
            "isCollateral": 0,
            "adjustedVoucher": 2495.7600615601,
            "supplied": 49.91540524718345,
            "adjustedVoucherUSD": 728.0161855301707,
            "rate": 14.585,
            "balanceUSD": 728.0161855301707
          },
          {
            "chainID": 2012,
            "blockNumber": 899672,
            "extrinsicHash": "0x18f3e75153bdffd547f6dbe41897fc085cde27e540eafc964fd5c61ea500b415",
            "extrinsicID": "899672-3",
            "section": "loans",
            "method": "mint"
          }
        ]
      ]
    },
    {
      assetInfo: {...},
      states: {...},
    },
    ...
  ],
  "nextPage": null
}         
```

## Get Account (extrinsics)

Return a list of extrinsics initiated by an account (paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/extrinsics/<Address>`

```shell
curl "https://api.polkaholic.io/account/extrinsics/16DWzViTodXg48SJzRRcqTQbSvFBxJEQ9Y2F4pNsrXueH4Nz" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {
          "chainID": 22001,
          "id": "bifrost-ksm",
          "chainName": "Bifrost",
          "extrinsicHash": "0xba848f7c29869dfd2b803da78d4881914060270c320c69e7589a5bf74264a228",
          "extrinsicID": "1867614-2",
          "blockNumber": 1867614,
          "ts": 1654485816,
          "blockHash": "0xf3ade114cc288ced40a8066134ecf954dbb432b938ad3cb0cffebe918f026d67",
          "signer": "dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU",
          "fromAddress": "0x62268ef984602bd656ee3f4ffd59ee4f91fb1b8dacc81561165acf09cb04b437",
          "signature": {
            "sr25519": "0xd6ac73a672697db70dc9eab9b3b5dd87272b3489cfbb78019468af821db05833d78bfe6fab3aeb23888d3ca72bf0db3089201be6a2b057e151beb0c27765c282"
          },
          "lifetime": {
            "isImmortal": 0,
            "birth": 1867610,
            "death": 1867642
          },
          "nonce": 542,
          "tip": 0,
          "fee": 0.002349333333,
          "chainSymbol": "BNC",
          "feeUSD": 0.0007885560825547829,
          "priceUSD": 0.335651,
          "priceUSDCurrent": 0.335225,
          "result": 1,
          "section": "vtokenMinting",
          "method": "redeem",
          "params": {
            "vtoken_id": {
              "vToken": "KSM"
            },
            "vtoken_amount": 2987766227425
          },
          "events": [...],
          "decodedParams": [
            {
              "section": "vtokenMinting",
              "method": "redeem",
              "vtoken_id": "{\"vToken\":\"KSM\"}",
              "vtoken_amount": "2987766227425"
            }
          ]
        },
        {extrinsics},
        ...
  ],
  "nextPage": null
}         
```

## Get Account (transfers)
Return a list of incoming transfers to an account (paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/transfers/<Address>`

```shell
curl "https://api.polkaholic.io/account/transfers/dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {
      "chainID": 22001,
      "blockNumber": 1872165,
      "blockHash": "0xc8e23468228bd9da929a3b7c98b30d6f0c51729cea2a452edefa54165b8b1372",
      "ts": 1654547634,
      "eventID": "22001-1872165-0-12",
      "extrinsicID": "1872165-0",
      "extrinsicHash": "0x695cb21066360699c677cdd8d4a25af2f6af98a50a7b182ef361890ef5925503",
      "from": "eCSrvbA5gGNQr7VZ48fkCX5vkt1H16F8Np9g2hYssRXHZJF",
      "to": "dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU",
      "amount": 53612057699,
      "data": [
        "eCSrvbA5gGNQr7VZ48fkCX5vkt1H16F8Np9g2hYssRXHZJF",
        "dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU",
        53612057699
      ],
      "genTS": 1654550411,
      "source": "astar",
      "chainName": "Bifrost",
      "decodedData": {
        "symbol": "BNC",
        "dataRaw": 0.053612057699,
        "dataUSD": 0.018170466655633575,
        "priceUSD": 0.338925,
        "priceUSDCurrent": 0.335258
      }
    },
    {
      "chainID": 22001,
      "blockNumber": 1871565,
      "blockHash": "0x32f3a90d78d523b863fc5d094fbebc0995c65e54f247e88932a2f1fd9fc4159d",
      "ts": 1654539372,
      "eventID": "22001-1871565-0-12",
      "extrinsicID": "1871565-0",
      "extrinsicHash": "0x789fa2b6cfa5c1d94a0b2f2d01fde70407cb3679b407a120433cb80f363eca8d",
      "from": "eCSrvbA5gGNQr7VZ48fkCX5vkt1H16F8Np9g2hYssRXHZJF",
      "to": "dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU",
      "amount": 56765708820,
      "data": [
        "eCSrvbA5gGNQr7VZ48fkCX5vkt1H16F8Np9g2hYssRXHZJF",
        "dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU",
        56765708820
      ],
      "genTS": 1654545577,
      "source": "kusama",
      "chainName": "Bifrost",
      "decodedData": {
        "symbol": "BNC",
        "dataRaw": 0.05676570882,
        "dataUSD": 0.01894226290756344,
        "priceUSD": 0.333692,
        "priceUSDCurrent": 0.335258
      }
    },
    {transfer},
    ...
  ],
  "nextPage": null
}
```

## Get Account (crowdloans)
Return a list of crowdloan contributions make by an account (paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/crowdloans/<Address>`

```shell
curl "https://api.polkaholic.io/account/crowdloans/FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {
      "chainID": 2,
      "blockNumber": 10591440,
      "blockHash": "0x270376baa8d9dedaaa6688978b78868ad4b3da618785e3e82d52052f9842218a",
      "ts": 1639935444,
      "eventID": "2-10591440-2-18",
      "extrinsicID": "10591440-2",
      "extrinsicHash": "0xacc0cfa6be0dd5937b7b326101c326b0a48b9f22c6df375d470dc30d9452f7e3",
      "action": "crowdloan(Contributed)",
      "account": "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
      "paraID": 2012,
      "amount": 1.1,
      "genTS": 1654403976,
      "source": "moonbeam",
      "chainName": "Kusama",
      "asset": "{\"Token\":\"KSM\"}",
      "amountUSD": 132.8536,
      "priceUSD": 120.776,
      "priceUSDCurrent": 70.2642,
      "chainIDDest": 22012,
      "chainDestName": "Crust Shadow"
    },
    {
      "chainID": 2,
      "blockNumber": 10363322,
      "blockHash": "0xea65c222481f4cb998dd9a65105ea2d6f56efcd015f0df3d94dc660d960cb5b9",
      "ts": 1638562530,
      "eventID": "2-10363322-3-25",
      "extrinsicID": "10363322-3",
      "extrinsicHash": "0x044e63a8548c51bac4f3cdf71cc3bc31e63b460f7652030604aee4361f1b1878",
      "action": "crowdloan(Contributed)",
      "account": "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
      "paraID": 2101,
      "amount": 8.3,
      "remark": "0x526c56466332314363574a6864586c6a526d6c714e6c6c48524452724d3364425a324a57546e5130616d466f6358633056574e6164307477643235615445343d2d333232663464653630336538336435663735316332383361346138646664316239366230633932383362393562626664376665653938656130393035383464642d492068617665207265616420616e6420616772656520746f20746865207465726d7320666f756e642061742068747470733a2f2f7a65697467656973742e706d2f43726f77646c6f616e5465726d732e706466",
      "genTS": 1654419116,
      "source": "parallel",
      "chainName": "Kusama",
      "asset": "{\"Token\":\"KSM\"}",
      "amountUSD": 1002.4408000000001,
      "priceUSD": 120.776,
      "priceUSDCurrent": 70.2642,
      "chainIDDest": 22101,
      "chainDestName": "Zeitgeist"
    },
    {crowdloans},
    ...
  ],
  "nextPage": null
}

```


## Get Account (rewards)
Return a list of staking rewards distributed to an account (paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/rewards/<Address>`

```shell
curl "https://api.polkaholic.io/account/rewards/13eEyAEkyazXwKnh51DPgdBdTWB8FWm4bPpsCB17RJ3K5LNV" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {
      "chainID": 2,
      "blockNumber": 10587766,
      "blockHash": "0x74711448efa85ef94e502e08d2b95a095b1d5e46a2db98d4f319510a70503ea0",
      "ts": 1639913370,
      "eventID": "2-10587766-4-296",
      "extrinsicID": "10587766-4",
      "extrinsicHash": "0x5b8f3a519166fc7172765560bd4c692c1d1def6e863647a7c3fb67ee2797b1a0",
      "action": "staking(Rewarded)",
      "account": "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
      "amount": 2.949002e-06,
      "era": 3124,
      "genTS": 1654403942,
      "source": "moonbeam",
      "chainName": "Kusama",
      "asset": "{\"Token\":\"KSM\"}",
      "amountUSD": 0.000356168665552,
      "priceUSD": 120.776,
      "priceUSDCurrent": 70.2642
    },
    {rewards},
    ...
  ],
  "nextPage": null
}
```





## Get Account (feed)

Return a list of extrinsics from all accounts that an address is following (paginated)

### HTTP Request

`GET https://api.polkaholic.io/account/feed/<Address>`

```shell
curl "https://api.polkaholic.io/account/balances/dwehUeMiyxAcSWUBsJiJ7WKmHZLueCxp18r3m1YDEj1xSKU" \
  -H "Authorization: YOUR-API-KEY"
```

```json
{
  "data": [
    {extrinsic},
    ...
  ],
  "nextPage": null
}

```

# XCM

## Get XCM Transfers

```shell
curl "https://api.polkaholic.io/xcmtransfers" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"

```

> Example Response (last 1000 xcmtransfers)

```json
[
  {
      "extrinsicHash": "0x9d4b548d4764988fbfc73a500c92792ce157b8bb356648338deb3b8ffbeb17c1",
      "extrinsicID": "2018879-4",
      "incomplete": 0,
      "status": "NonFinalizedSource",
      "section": "xTokens",
      "method": "transferMulticurrencies",
      "fromAddress": "0xcc1ba006a1715e894b621a36169165cb72343b1c6ad4ba2230d394be4033a645",
      "id": "karura",
      "chainID": 22000,
      "chainName": "Karura",
      "blockNumber": 2018879,
      "sourceTS": 1654270152,
      "destAddress": "0xcc1ba006a1715e894b621a36169165cb72343b1c6ad4ba2230d394be4033a645",
      "idDest": "statemine",
      "chainIDDest": 21000,
      "chainDestName": "Statemine",
      "blockNumberDest": 2213841,
      "destTS": 1654270172,
      "asset": "{\"Token\":\"RMRK\"}",
      "rawAsset": "{\"ForeignAsset\":\"0\"}",
      "amountSent": 238.5455268637,
      "amountSentUSD": 1080.7734476508283,
      "amountReceived": 238.5455268637,
      "amountReceivedUSD": 1080.7734476508283,
      "priceUSD": 4.53068,
      "priceUSDCurrent": 4.80811
  },
  {
      "extrinsicHash": "0x291a9de305db0cffa1961d08b32102ab6c348a47dab34d9f23a67ec3bbb5a8b2",
      "extrinsicID": "10589459-2",
      "incomplete": 0,
      "status": "NonFinalizedSource",
      "section": "xcmPallet",
      "method": "reserveTransferAssets",
      "fromAddress": "0xfc1df3d0aadb175f478e7d6aa79c31e25c685988e0714c7a0ff9de38f70dcf2f",
      "id": "polkadot",
      "chainID": 0,
      "chainName": "Polkadot",
      "blockNumber": 10589459,
      "sourceTS": 1654287090,
      "destAddress": "0xfc1df3d0aadb175f478e7d6aa79c31e25c685988e0714c7a0ff9de38f70dcf2f",
      "idDest": "parallel",
      "chainIDDest": 2012,
      "chainDestName": "Parallel",
      "blockNumberDest": 1099628,
      "destTS": 1654287091,
      "asset": "{\"Token\":\"DOT\"}",
      "rawAsset": "{\"Token\":\"DOT\"}",
      "amountSent": 103.5773,
      "amountSentUSD": 968.4581127299999,
      "amountReceived": 103.5677,
      "amountReceivedUSD": 968.36835177,
      "priceUSD": 9.3501,
      "priceUSDCurrent": 9.38238
  },
...
]
```

Return the latest 1000 xcm tranfers from all supported networks.

### HTTP Request

`GET https://api.polkaholic.io/xcmtransfers/`

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description

Attribute | Description
--------- | -----------
fromAddress  | Sender's pubkey |  
destAddress    | Recipient's pubkey|   
sectionMethod | The extrinsic's module_call that initiated the xcm (i.e. `xcmPallet:limitedReserveTransferAssets`, `xTokens:transfer`)
relayChain | The relayChain that facilitates the message passing (polkadot or kusama)
chainID   | The initiated chain where the xcm is sending from |
chainIDDest   | The destination chain where the xcm is going to |
incomplete | whether the xcm is successfully sent by the sender (NOTE: A successfully sent xcm does not guarantee it has been successfully processed by the destChain without errors )
asset | The "human-readble" representation of the sent asset
rawAsset | The "raw" representation of the sent asset. (NOTE: Sometimes different parachains represent the same asset differently. We will automatically any known assets)

<aside class="information">
This API is in alpha development!
</aside>

# Search (tx, events, xcms...)

Search API returns a list of {extrinsics, evmtxs, events, xcmtransfers, xcmmessages} given certain user-specified criteria.

## Search Extrinsics

This endpoint returns a list of extrinsic meta given certain user-specified criteria.

```shell
curl https://api.polkaholic.io/search/extrinsics \
-X POST \
-H "Content-Type: application/json" \
-d '{
    "chainIdentifier": "parallel",
    "section": "balances",
    "method": "transferKeepAlive",
    "dateStart": "2022-05-01",
    "dateEnd": "2022-05-31",
    "fromAddress": "0xe6b912626c9dfa3cd9e65b4412b19eb9d123edb1aa22d492a58a88091c483a7a"
}'
```

> Example Response (Extrinsic meta)

```json
[
  {
    "chainID": 2012,
    "blockNumber": 968329,
    "extrinsicID": "968329-2",
    "extrinsicHash": "0xdf8d1d1a94088c30d99357971a21960221ab7994b5afe4649503c5ed736e8571",
    "section": "balances",
    "method": "transferKeepAlive",
    "fromAddress": "0xe6b912626c9dfa3cd9e65b4412b19eb9d123edb1aa22d492a58a88091c483a7a",
    "blockTS": 1652656272,
    "result": 0
  },
  ...
]
```

### HTTP Request

`POST https://api.polkaholic.io/search/extrinsics`

### Input Parameters

Attribute | Type | Description | Optional?
--------- | -----|----- | :---------:
chainIdentifier | String or Int | The identifier of the chain to retrieve data about  | Required
fromAddress | String | The signer pubkey | Optional
section | String | The "section" of the extrinsic (aka. The "Module")  | Optional
method |  String | The "method" of the extrinsic (aka. The "Call")  | Optional
dateStart | `"YYYY-MM-DD"` | The Starting Date(inclusive). ex: "2022-05-01" | Optional
dateEnd | `"YYYY-MM-DD"` |  The Ending Date(inclusive). ex: "2022-05-31" | Optional
blockNumberStart | Int | The Starting BlockNumber(inclusive) | Optional
blockNumberEnd | Int| The Ending BlockNumber(inclusive) | Optional

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description

Attribute | Description
--------- | -----------
chainID | The Alternative identifiers of the given chain  |    
section | The "section" of the extrinsic (aka. the "Module")  |
method |  The "method" of the extrinsic (aka. the "Call")  |
fromAddress | The signer pubkey (if signed)  |
result | Whether the extrinsic is successful  |



## Search EVM Transactions

This endpoint returns a list of evm transaction meta given certain user-specified criteria.

```shell
curl https://api.polkaholic.io/search/evmtxs \
-X POST \
-H "Content-Type: application/json" \
-d '{
    "chainIdentifier": "moonbeam",
    "methodID": "0xa9059cbb",
    "toAddress": "0x085416975fe14c2a731a97ec38b9bf8135231f62",
    "blockNumberStart": 945500,
    "blockNumberEnd": 946000
}'
```

> Example Response (EVM Transaction meta)

```json
[
  {
      "chainID": 2004,
      "blockNumber": 945879,
      "transactionHash": "0xac3d6757fc3d7fafc4ad97a0454d93fc3931708ebf0268d3783e90d383750162",
      "method": "transfer",
      "methodID": "0xa9059cbb",
      "blockTS": 1651535946,
      "result": 1,
      "fromAddress": "0x623eb92cea59948fb52d8abdfbfe097ac0d8bd36",
      "toAddress": "0x085416975fe14c2a731a97ec38b9bf8135231f62",
      "substrate": {
        "extrinsicID": "945879-3",
        "extrinsicHash": "0x2113913089fbb0949c06ddc442fd17c1c3f9018111db298d04dd4fcae41093dd"
      }
  },
  ...
]    
```

### HTTP Request

`POST https://api.polkaholic.io/search/evmtxs`

### Input Parameters

Attribute | Type | Description | Optional?
--------- | -----|----- | :---------:
chainIdentifier | String or Int | The identifier of the chain to retrieve data about  | Required
fromAddress | hexString | The 20 bytes Ethereum-style sender address| Optional
toAddress | hexString | The 20 bytes Ethereum-style recipient address| Optional  
isContractCreation | Int | 1: filtering on contract creation tx; ignored otherwise | Optional  
method | String | The function called by transaction. ex: 'transfer'| Optional
methodID |  hexString | The 4 byte "signatureID" of function ex: '0xa9059cbb'  | Optional
dateStart | `"YYYY-MM-DD"` | The Starting Date(inclusive). ex: "2022-05-01" | Optional
dateEnd | `"YYYY-MM-DD"` |  The Ending Date(inclusive). ex: "2022-05-31" | Optional
blockNumberStart | Int | The Starting BlockNumber(inclusive) | Optional
blockNumberEnd | Int| The Ending BlockNumber(inclusive) | Optional
result | Int | 0: Failure, 1: Success. If unspecified: including both | Optional

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description

Attribute | Description
--------- | -----------
chainID | The Alternative identifiers of the given chain  |    
transactionHash | The evm tx transactionHash  |
substrate |  The [SubstrateInfo](#substrateinfo) directly linked to the evmTx   |


## Search Events

This endpoint returns a list of event meta given certain user-specified criteria.

```shell
curl https://api.polkaholic.io/search/events \
-X POST \
-H "Content-Type: application/json" \
-d '{
    "chainIdentifier": 2012,
    "section": "xTokens",
    "blockNumberStart": 1050000,
    "blockNumberEnd": 1051000
}'
```

> Example Response (events meta)

```json
[
  {
    "chainID": 2012,
    "blockNumber": 1050860,
    "eventID": "2012-1050860-4-15",
    "extrinsicHash": "0x4a22eb3bed70c00bb603d895e46a8c0928d36062db721840aee6e9b11715bebb",
    "section": "xTokens",
    "method": "TransferredMultiAssets",
    "blockTS": 1653677562
  },
  ...
]  
```

### HTTP Request

`POST https://api.polkaholic.io/search/events`

### Input Parameters

Attribute | Type | Description | Optional?
--------- | -----|----- | :---------:
chainIdentifier | String or Int | The identifier of the chain to retrieve data about  | Required
section | String | The "section" of the extrinsic (aka. The "Module")  | Optional
method |  String | The "method" of the extrinsic (aka. The "Call")  | Optional
dateStart | `"YYYY-MM-DD"` | The Starting Date(inclusive). ex: "2022-05-01" | Optional
dateEnd | `"YYYY-MM-DD"` |  The Ending Date(inclusive). ex: "2022-05-31" | Optional
blockNumberStart | Int | The Starting BlockNumber(inclusive) | Optional
blockNumberEnd | Int| The Ending BlockNumber(inclusive) | Optional
result | Int | 0: Failure, 1: Success. If unspecified: including both | Optional


### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description

Attribute | Description
--------- | -----------
chainID | The Alternative identifiers of the given chain  |    
eventID | The identifier of an event, in the form of `chainID-blockNumber-extrinsicIndex-eventIndex`
section | The "section" part of the event. Ex: "balances"  |
method  | The "method" part of the event. Ex: "Transfer"  |


## Search XCM Transfers

This endpoint returns a list of xcm transfers given certain user-specified criteria.


```shell
curl https://api.polkaholic.io/search/xcmtransfers \
-X POST \
-H "Content-Type: application/json" \
-d '{
    "chainID": "polkadot",
    "chainIDDest": "acala",
    "complete": 0,
    "toAddress":"0x9e992a944acb1efa30bcd3275aedf7218bac369ca62dc0269ccec2f36db65c6f"
}'
```

> Example Response (array of xcm tranfers)

```json
[
  {
    "extrinsicHash": "0x625e023ecb994fdf71c1b86e933cd747e529706e9e826a7de801d708c2a82f93",
    "extrinsicID": "10530678-3",
    "chainID": 0,
    "chainIDDest": 2000,
    "blockNumber": "10530678",
    "fromAddress": "0x9e992a944acb1efa30bcd3275aedf7218bac369ca62dc0269ccec2f36db65c6f",
    "destAddress": "0x9e992a944acb1efa30bcd3275aedf7218bac369ca62dc0269ccec2f36db65c6f",
    "sectionMethod": "xcmPallet:reserveTransferAssets",
    "asset": "{\"Token\":\"DOT\"}",
    "rawAsset": "{\"Token\":\"DOT\"}",
    "nativeAssetChain": null,
    "blockNumberDest": 1125835,
    "sourceTS": 1653927474,
    "destTS": 1653927474,
    "amountSent": 2.7,
    "amountReceived": 2.6997573809,
    "status": "NonFinalizedSource",
    "relayChain": "polkadot",
    "incomplete": 0,
    "amountSentUSD": 25.9353,
    "amountReceivedUSD": 25.933,
    "chainName": "Polkadot",
    "id": "polkadot",
    "idDest": "acala",
    "chainDestName": "Acala"
  }
]
```

### HTTP Request

`POST https://api.polkaholic.io/search/xcmtransfers`

### Input Parameters

Attribute | Type | Description | Optional?
--------- | -----|----- | :---------:
chainID | String or Int | The identifier of the chain to retrieve data about  | Optional
chainIDDest | String or Int | The identifier of the chain to retrieve data about  | Optional  
fromAddress | String | The XCM sender pubkey | Optional
toAddress | String | The XCM beneficiary pubkey | Optional  
dateStart | `"YYYY-MM-DD"` | The Starting Date(inclusive). ex: "2022-05-01" | Optional
dateEnd | `"YYYY-MM-DD"` |  The Ending Date(inclusive). ex: "2022-05-31" | Optional
blockNumberStart | Int | The Starting BlockNumber at sending chain (inclusive) | Optional
blockNumberEnd | Int| The Ending BlockNumber at sending chain (inclusive) | Optional
complete | Int | 1: Complete(xcm successfully initiated), 0: Incomplete. If Unspecified: Including both | Optional

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decroate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data

### Response Description
Return an list of (xcmtransfer)[#xcmtransfers]

## Search XCM Messages

This endpoint returns a list of channelMsg {dmp, ump, xcmp} given certain user-specified criteria.


```shell
curl https://api.polkaholic.io/search/xcmmessages \
-X POST \
-H "Content-Type: application/json" \
-d '{
    "startDate": "2022-06-27",
    "endDate": "2022-06-30",
    "relayChain":"polkadot"
}'
```

> Example Response (array of xcm message)

```json
[
  {
    "xcmID": "1334065-1-dmp-2000-0-0",
    "chainID": 0,
    "id": "polkadot",
    "chainName": "Polkadot",
    "chainIDDest": 2000,
    "idDest": "acala",
    "chainDestName": "Acala",    
    "msgType": "dmp",
    "msgHash": "a6fd9ca31c18b44d64cdfed29c90eebeb89548f294cf2389ca76e56b79f4f367",
    "msgHex": "0x02100104000100000700e87648170a13000100000700e8764817010300286bee0d010004000101006642ee28fc1b7d1a01ea2bc956bfe5fde1c7121cae33afe51a83cc683785a81f",
    "msgStr": "{\"v2\":[{\"reserveAssetDeposited\":[{\"id\":{\"concrete\":{\"parents\":1,\"interior\":{\"here\":null}}},\"fun\":{\"fungible\":100000000000}}]},{\"clearOrigin\":null},{\"buyExecution\":{\"fees\":{\"id\":{\"concrete\":{\"parents\":1,\"interior\":{\"here\":null}}},\"fun\":{\"fungible\":100000000000}},\"weightLimit\":{\"limited\":4000000000}}},{\"depositAsset\":{\"assets\":{\"wild\":{\"all\":null}},\"maxAssets\":1,\"beneficiary\":{\"parents\":0,\"interior\":{\"x1\":{\"accountId32\":{\"network\":{\"any\":null},\"id\":\"0x6642ee28fc1b7d1a01ea2bc956bfe5fde1c7121cae33afe51a83cc683785a81f\"}}}}}}]}",
    "ts": 1656594360,
    "blockNumber": 1334065,
    "relayChain": "Polkadot",
    "sentAt": 10962759
  },
  {
    "xcmID": "10962787-1-ump-0-2006-0",
    "chainID": 2006,
    "id": "astar",
    "chainName": "Astar",
    "chainIDDest": 0,
    "idDest": "polkadot",
    "chainDestName": "Polkadot",    
    "msgType": "ump",
    "msgHash": "f85d75771ed2b88c5ecfe9d9d9bb3255a650eb33512d1e6b8bf49c2ae8a1e700",
    "msgHex": "0x02100004000000000700aea68f020a13000000000700aea68f02010300286bee0d010004000101006877a0db00acc7da104aa11b05cf091254843468189c8b13808567eead2c8e57",
    "msgStr": "{\"v2\":[{\"withdrawAsset\":[{\"id\":{\"concrete\":{\"parents\":0,\"interior\":{\"here\":null}}},\"fun\":{\"fungible\":11000000000}}]},{\"clearOrigin\":null},{\"buyExecution\":{\"fees\":{\"id\":{\"concrete\":{\"parents\":0,\"interior\":{\"here\":null}}},\"fun\":{\"fungible\":11000000000}},\"weightLimit\":{\"limited\":4000000000}}},{\"depositAsset\":{\"assets\":{\"wild\":{\"all\":null}},\"maxAssets\":1,\"beneficiary\":{\"parents\":0,\"interior\":{\"x1\":{\"accountId32\":{\"network\":{\"any\":null},\"id\":\"0x6877a0db00acc7da104aa11b05cf091254843468189c8b13808567eead2c8e57\"}}}}}}]}",
    "ts": 1656594528,
    "blockNumber": 10962787,
    "relayChain": "Polkadot",
    "sentAt": 10962786
  },
  {
    "xcmID": "1334166-1-xcmp-2000-2004-0",
    "chainID": 2004,
    "id": "moonbeam",
    "chainName": "Moonbeam",
    "chainIDDest": 2000,
    "idDest": "acala",
    "chainDestName": "Acala",
    "msgType": "xcmp",
    "msgHash": "e4da9547a5c2977713b7c9277b26a77e8ea65e2c07ea177b125c359e72728f00",
    "msgHex": "0x0210000400000106080000000b08b6957fbd430a1300000106080000000b08b6957fbd43010300286bee0d01000400010100d0c696806e3f6020040241eefddbbbb6ef5bf870f4c77feaac4775d26e7a662c",
    "msgStr": "{\"v2\":[{\"withdrawAsset\":[{\"id\":{\"concrete\":{\"parents\":0,\"interior\":{\"x1\":{\"generalKey\":\"0x0000\"}}}},\"fun\":{\"fungible\":74481168397832}}]},{\"clearOrigin\":null},{\"buyExecution\":{\"fees\":{\"id\":{\"concrete\":{\"parents\":0,\"interior\":{\"x1\":{\"generalKey\":\"0x0000\"}}}},\"fun\":{\"fungible\":74481168397832}},\"weightLimit\":{\"limited\":4000000000}}},{\"depositAsset\":{\"assets\":{\"wild\":{\"all\":null}},\"maxAssets\":1,\"beneficiary\":{\"parents\":0,\"interior\":{\"x1\":{\"accountId32\":{\"network\":{\"any\":null},\"id\":\"0xd0c696806e3f6020040241eefddbbbb6ef5bf870f4c77feaac4775d26e7a662c\"}}}}}}]}",
    "ts": 1656595609,
    "blockNumber": 1334166,
    "relayChain": "Polkadot",
    "sentAt": 10962961,
  },
  ...
]
```

### HTTP Request

`POST https://api.polkaholic.io/search/xcmmessages`

### Input Parameters

Attribute | Type | Description | Optional?
--------- | -----|----- | :---------:
chainID | String or Int | The identifier of the source chain to retrieve data about  | Optional
chainIDDest | String or Int | The identifier of the dest chain to retrieve data about  | Optional  
dateStart | `"YYYY-MM-DD"` | The Starting Date(inclusive). ex: "2022-05-01" | Optional
dateEnd | `"YYYY-MM-DD"` |  The Ending Date(inclusive). ex: "2022-05-31" | Optional
msgType | String | Filter based on channel msg type ['ump','dmp','xcmp'] | Optional
relayChain | String| relayChain of the msg. ex: 'polkadot' or 'kusama' | Optional

### URL Parameters

NONE

### Response Description
Return an list of xcmmessage

Attribute    | Description
-------------|------------
xcmID        | The xcm identifiers in the form of: <br /> `blockNumber-txIdx-mpType-sourceChainID-destChainID-msgIdx` |
msgType      | _ump_  - upward msg send from parachain to relaychain.<br />_dmp_  - downard msg send from relaychain to parachain. <br />_xcmp_ - horizontal msg (hrmp) send from parachain to parachain
msgHex       | The hexEncoded msg. _Note:_ First byte is effectively removed from the raw xcmp msg |
msgHash      | The blake256(msgHex)   |
msgStr       | The undecorated Channel Msg   |
blockNumber  | The BN where the msg is received by dest chain  |
sentAt       | The hrmpWatermark BN  |

# Hash

## Hash Lookup

<aside class="notice">
Not sure what hashType it is? Get an authoritative answer with this API!
</aside>

```shell
# lookup substrate Blockhash
curl "https://api.polkaholic.io/hash/0x4a42752a0b54b859961c1858eb0c591a579ca7bc864b79b37adee3dcb082b391" \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (substrate Blockhash)

```json
{
    "hash": "0x4a42752a0b54b859961c1858eb0c591a579ca7bc864b79b37adee3dcb082b391",
    "hashType": "substrateBlockHash",
    "status": "finalized",
    "chainID": 2004,
    "blockNumber": 808508
}
```

```shell
# lookup evm Blockhash
curl "https://api.polkaholic.io/hash/0xd62500cbc13a6d68aa3ad9131b54951a11bed3bc19ba8aebfda933fca6f443a2" \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (evm Blockhash)

```json
{
    "hash": "0xd62500cbc13a6d68aa3ad9131b54951a11bed3bc19ba8aebfda933fca6f443a2",
    "hashType": "evmBlockHash",
    "status": "finalized",
    "chainID": 2004,
    "blockNumber": 808508
}
```

```shell
# lookup extrinsicHash
curl "https://api.polkaholic.io/hash/0x4a9d94960923f796eb1100fe7b8587ae6e30d2e0b1295900605c8e38156ac154" \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (extrinsicHash)

```json
{
    "hash": "0x4a9d94960923f796eb1100fe7b8587ae6e30d2e0b1295900605c8e38156ac154",
    "hashType": "extrinsicHash",
    "status": "finalized",
    "chainID": 2004,
    "blockNumber": "808508"
}
```

```shell
# lookup evm transactionHash
curl "https://api.polkaholic.io/hash/0x972b7b456ddec41fcc437702f72e163bf0e8d916da2487b4252c5059e72a1343" \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (evm transactionHash)

```json
{
    "hash": "0x972b7b456ddec41fcc437702f72e163bf0e8d916da2487b4252c5059e72a1343",
    "hashType": "transactionHash",
    "status": "finalized",
    "chainID": 2004,
    "blockNumber": 808508
}
```

```shell
# lookup unmatched/unidentifiable hash
curl "https://api.polkaholic.io/hash/0xe5b17b7515813b54826b7231dd8be079e3bbf64c72d00c8567b475cc3a19277d" \
  -H "Authorization: YOUR-API-KEY"
```
> Example Response (unknown hash)

```json
{
    "hash": "0xe5b17b7515813b54826b7231dd8be079e3bbf64c72d00c8567b475cc3a19277d",
    "hashType": "NotFound",
    "status": "NotFound",
    "chainID": null,
    "blockNumber": null
}
```
### HTTP Request

`GET https://api.polkaholic.io/hash/<Hash>`

### Query Parameters

Parameter | Description
--------- | -----------
Hash | The hash to lookup. If found, the corresponding hashType and relevant info will be returned |  


### Response Description

Attribute | Description
--------- | -----------
hashType  | The matched hashType (notFound, substrateBlockHash, evmBlockHash, extrinsicHash, transactionHash) |  
status    | The hash status (notFound, pending, unfinalized, finalized, finalizeddest) |   
chainID   | The corresponding chainID where the hash was included/found  |
blockNumber | The blockNumber where the hash was included/found

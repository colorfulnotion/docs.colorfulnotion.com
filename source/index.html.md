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

Welcome to [Polkaholic](http://polkaholic.io) API

Polkaholic API gives you powerful access to over 50+ networks in Polkadot and Kusama ecosystem. Get a [free API key](https://polkaholic.io/apikeys) today and start building your own dApps!

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

As of 2022-11-01, Polkaholic supports Polkadot & 22 polkadot-parachains, plus Kusama & 39 kusama-parachains - 63 chains in total.

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

| Chain              | ID               | ChainID | Polkaholic Explorer                                                      | Prefix |
|--------------------|------------------|---------|--------------------------------------------------------------------------|--------|
| Polkadot           | polkadot         |       0 | [polkadot.polkaholic.io](https://polkadot.polkaholic.io)                 |      0 |
| Statemint          | statemint        |    1000 | [statemint.polkaholic.io](https://statemint.polkaholic.io)               |      0 |
| Acala              | acala            |    2000 | [acala.polkaholic.io](https://acala.polkaholic.io)                       |     10 |
| Clover             | clover           |    2002 | [clover.polkaholic.io](https://clover.polkaholic.io)                     |    128 |
| Moonbeam           | moonbeam         |    2004 | [moonbeam.polkaholic.io](https://moonbeam.polkaholic.io)                 |   1284 |
| Astar              | astar            |    2006 | [astar.polkaholic.io](https://astar.polkaholic.io)                       |      5 |
| Kapex*             | kapex            |    2007 | [kapex.polkaholic.io](https://kapex.polkaholic.io)                       |   2007 |
| Equilibrium        | equilibrium      |    2011 | [equilibrium.polkaholic.io](https://equilibrium.polkaholic.io)           |     68 |
| Parallel           | parallel         |    2012 | [parallel.polkaholic.io](https://parallel.polkaholic.io)                 |    172 |
| Litentry           | litentry         |    2013 | [litentry.polkaholic.io](https://litentry.polkaholic.io)                 |     31 |
| Composable Finance | composable       |    2019 | [composable.polkaholic.io](https://composable.polkaholic.io)             |     50 |
| Efinity            | efinity          |    2021 | [efinity.polkaholic.io](https://efinity.polkaholic.io)                   |   1110 |
| Nodle              | nodle            |    2026 | [nodle.polkaholic.io](https://nodle.polkaholic.io)                       |     37 |
| Bifrost-Polkadot   | bifrost-dot      |    2030 | [bifrost-dot.polkaholic.io](https://bifrost-dot.polkaholic.io)           |      6 |
| Centrifuge         | centrifuge       |    2031 | [centrifuge.polkaholic.io](https://centrifuge.polkaholic.io)             |     36 |
| Interlay           | interlay         |    2032 | [interlay.polkaholic.io](https://interlay.polkaholic.io)                 |   2032 |
| HydraDX            | hydradx          |    2034 | [hydradx.polkaholic.io](https://hydradx.polkaholic.io)                   |     63 |
| Phala              | phala            |    2035 | [phala.polkaholic.io](https://phala.polkaholic.io)                       |     30 |
| Unique             | unique           |    2037 | [unique.polkaholic.io](https://unique.polkaholic.io)                     |   7391 |
| Integritee Shell*  | integritee-shell |    2039 | [integritee-shell.polkaholic.io](https://integritee-shell.polkaholic.io) |     13 |
| Origin Trail*      | origintrail      |    2043 | [origintrail.polkaholic.io](https://origintrail.polkaholic.io)           |    101 |
| Darwinia*          | darwinia         |    2046 | [darwinia.polkaholic.io](https://darwinia.polkaholic.io)                 |     18 |
| Kylin*             | kylin            |    2052 | [kylin.polkaholic.io](https://kylin.polkaholic.io)                       |     42 |

### Supported Kusama Chains

| Chain               | ID                | ChainID | Polkaholic Explorer                                                        | Prefix |
|---------------------|-------------------|---------|----------------------------------------------------------------------------|--------|
| Kusama              | kusama            |       2 | [kusama.polkaholic.io](https://kusama.polkaholic.io)                       |      2 |
| Statemine           | statemine         |   21000 | [statemine.polkaholic.io](https://statemine.polkaholic.io)                 |      2 |
| Encointer           | encointer         |   21001 | [encointer.polkaholic.io](https://encointer.polkaholic.io)                 |      2 |
| Karura              | karura            |   22000 | [karura.polkaholic.io](https://karura.polkaholic.io)                       |      8 |
| Bifrost-Kusama      | bifrost-ksm       |   22001 | [bifrost-ksm.polkaholic.io](https://bifrost-ksm.polkaholic.io)             |      6 |
| Khala               | khala             |   22004 | [khala.polkaholic.io](https://khala.polkaholic.io)                         |     30 |
| Shiden              | shiden            |   22007 | [shiden.polkaholic.io](https://shiden.polkaholic.io)                       |      5 |
| Sora Kusama         | sora              |   22011 | [sora.polkaholic.io](https://sora.polkaholic.io)                           |     69 |
| Crust Shadow*       | shadow            |   22012 | [shadow.polkaholic.io](https://shadow.polkaholic.io)                       |     66 |
| Integritee          | integritee        |   22015 | [integritee.polkaholic.io](https://integritee.polkaholic.io)               |     13 |
| Moonriver           | moonriver         |   22023 | [moonriver.polkaholic.io](https://moonriver.polkaholic.io)                 |   1285 |
| Genshiro            | genshiro          |   22024 | [genshiro.polkaholic.io](https://genshiro.polkaholic.io)                   |     67 |
| Robonomics          | robonomics        |   22048 | [robonomics.polkaholic.io](https://robonomics.polkaholic.io)               |     32 |
| Calamari            | calamari          |   22084 | [calamari.polkaholic.io](https://calamari.polkaholic.io)                   |     78 |
| Parallel Heiko      | parallel-heiko    |   22085 | [parallel-heiko.polkaholic.io](https://parallel-heiko.polkaholic.io)       |    110 |
| KILT Spiritnet      | spiritnet         |   22086 | [spiritnet.polkaholic.io](https://spiritnet.polkaholic.io)                 |     38 |
| Picasso             | picasso           |   22087 | [picasso.polkaholic.io](https://picasso.polkaholic.io)                     |     49 |
| Altair              | altair            |   22088 | [altair.polkaholic.io](https://altair.polkaholic.io)                       |    136 |
| Basilisk            | basilisk          |   22090 | [basilisk.polkaholic.io](https://basilisk.polkaholic.io)                   |  10041 |
| Kintsugi            | kintsugi          |   22092 | [kintsugi.polkaholic.io](https://kintsugi.polkaholic.io)                   |   2092 |
| Quartz              | quartz            |   22095 | [quartz.polkaholic.io](https://quartz.polkaholic.io)                       |    255 |
| Bit.Country Pioneer | bitcountrypioneer |   22096 | [bitcountrypioneer.polkaholic.io](https://bitcountrypioneer.polkaholic.io) |    268 |
| SubsocialX*         | subsocialx        |   22100 | [subsocialx.polkaholic.io](https://subsocialx.polkaholic.io)               |     28 |
| Zeitgeist           | zeitgeist         |   22101 | [zeitgeist.polkaholic.io](https://zeitgeist.polkaholic.io)                 |     73 |
| Pichiu              | pichiu            |   22102 | [pichiu.polkaholic.io](https://pichiu.polkaholic.io)                       |     42 |
| Darwinia Crab       | crab              |   22105 | [crab.polkaholic.io](https://crab.polkaholic.io)                           |     18 |
| Litmus              | litmus            |   22106 | [litmus.polkaholic.io](https://litmus.polkaholic.io)                       |    131 |
| Kico                | kico              |   22107 | [kico.polkaholic.io](https://kico.polkaholic.io)                           |     52 |
| Mangata*            | mangatax          |   22110 | [mangatax.polkaholic.io](https://mangatax.polkaholic.io)                   |     42 |
| Kabocha             | kabocha           |   22113 | [kabocha.polkaholic.io](https://kabocha.polkaholic.io)                     |     27 |
| Turing              | turing            |   22114 | [turing.polkaholic.io](https://turing.polkaholic.io)                       |     51 |
| Dora Factory        | dorafactory       |   22115 | [dorafactory.polkaholic.io](https://dorafactory.polkaholic.io)             |    128 |
| Tanganika*          | tanganika         |   22116 | [tanganika.polkaholic.io](https://tanganika.polkaholic.io)                 |     33 |
| Listen*             | listen            |   22118 | [listen.polkaholic.io](https://listen.polkaholic.io)                       |     42 |
| Bajun Network*      | bajun             |   22119 | [bajun.polkaholic.io](https://bajun.polkaholic.io)                         |   1337 |
| Imbue Network       | imbue             |   22121 | [imbue.polkaholic.io](https://imbue.polkaholic.io)                         |     42 |
| GM Parachain*       | gm                |   22123 | [gm.polkaholic.io](https://gm.polkaholic.io)                               |   7013 |
| InvArch Tinkernet*  | tinkernet         |   22125 | [tinkernet.polkaholic.io](https://tinkernet.polkaholic.io)                 |    117 |
| Snow*               | snow              |   22129 | [snow.polkaholic.io](https://snow.polkaholic.io)                           |   2207 |
| DAO IPCI*           | daoipci           |   22222 | [daoipci.polkaholic.io](https://daoipci.polkaholic.io)                     |     32 |

*_Unstable Chain_: These chains are unstable/unreachable; therefore API services are limited for these chains.

### Supported Moonbase Chains (Testnet)
| Chain          | ID             | ChainID | Polkaholic Explorer                                                  | Prefix |
|----------------|----------------|---------|----------------------------------------------------------------------|--------|
| moonbase-relay | moonbase-relay |   60000 | [moonbase-relay.polkaholic.io](https://moonbase-relay.polkaholic.io) |     42 |
| Moonbase Beta  | moonbase-beta  |   60888 | [moonbase-beta.polkaholic.io](https://moonbase-beta.polkaholic.io)   |   1288 |
| Moonbase Alpha | moonbase-alpha |   61000 | [moonbase-alpha.polkaholic.io](https://moonbase-alpha.polkaholic.io) |   1287 |

*_moonbase_: We are doing active development on Moonbase connected contracts; indexing are partially available and endpoint may change without any notice

(Last updated: 2022-11-01)

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
decrate   | Whether API should return decorated fields | Yes | true
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
decorate  | Whether API should return decorated fields | Yes | true
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
decorate  | Whether API should return decorated fields | Yes | true
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

Parameter      | Description | Optional? | Default |
---------------| ----------- | --------- | ------- |
group          | The group type to return by the API (see below) | Yes | 'realtime'
lookbackWindow | TBA | Yes | 180
decorate       | Whether API should return decorated fields | Yes | true
extra          | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data
chainfilters   | Filter the result by comma-separated chainIdentifiers. i.e. `chainfilters=polkadot,kusama,2000`  | Yes | 'all'


### Supported Query Group
Currently `/account` endpoint supprts [`realtime`,`balances`, `xcmtransfers`, `history`,`extrinsics`,`transfers`,`crowdloans`,`rewards`, `feed`] group type. Only *one* group type will be returned by the API at a time.


| Group Type | Description | Paginated | Chainfilter Support | Return Sample |
| ---------  | ----------- | :-----------: |:-----------: | :-----------: |
| realtime  | Current account snapshot  | - | Yes |[e1]()  
| balances  | Historical Account Balance snapshots over the last N days (in USD)| - | Yes | [e2]()
| xcmtransfer | cross-chain transfers initiated by the account. | - |  Yes | [e3]()
| history  | Historical account snapshots  | Yes |  Yes | [e4]()
| extrinsics  | Extrinsics (including both substrateTX and evmTX) initiated by the account | Yes |  Yes |[e5]()
| transfers  |Incoming transfers to the account  | Yes |  Yes | [e6]()
| crowdloans  | direct crowdloans contributions made by the account   | Yes |  Relaychain Only | [e7]()
| rewards  | staking rewards/panalties received by the account | Yes | Yes | [e8]()
| feed  | Extrinsics initiate by the accounts which an account follows | Yes |Partial |[e9]()



## Get Account (realtime)

Return all assets that are held by an account (realtime)

### HTTP Request

`GET https://api.polkaholic.io/account/realtime/<Address>`

```shell
# get realtime assets on all chains, using default decoration
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

```shell
# get acala asset in realtime, no decoration
curl "https://api.polkaholic.io/account/realtime/13Dh9XPwREhog65gkg2a2humtNhaaYRqgMp4Mf9jS7A6GK8m?chainfilters=acala&decrate=f" \
  -H "Authorization: YOUR-API-KEY"
```
```json
[
    {
        "assetChain": "{\"Loan\":{\"Token\":\"DOT\"}}~2000",
        "assetInfo": {
            "assetType": "Loan",
            "assetName": "Loan:DOT",
            "numHolders": 4910,
            "asset": "{\"Loan\":{\"Token\":\"DOT\"}}",
            "symbol": "Loan:DOT",
            "decimals": 10,
            "chainID": 2000,
            "chainName": "Acala",
            "assetChain": "{\"Loan\":{\"Token\":\"DOT\"}}~2000",
            "isUSD": 0,
            "priceUSDpaths": false,
            "nativeAssetChain": null
        },
        "state": {
            "debit": 0,
            "borrowedAsset": {
                "Token": "AUSD"
            },
            "ts": 1655532486,
            "bn": 1251351,
            "source": "moonbeam",
            "genTS": 1659313994,
            "exchangeRate": 0.10141204925333436,
            "exchangeRateCurrent": 0.10141204925333436
        }
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
# get a list of account's xcmtransfers on kintsugi(22092); decorate it with usd and any onchain identity
curl "https://api.polkaholic.io/account/xcmtransfers/13eEyAEkyazXwKnh51DPgdBdTWB8FWm4bPpsCB17RJ3K5LNV?decorate=t&extra=usd,address&chainfilters=22092" \
  -H "Authorization: YOUR-API-KEY"
```

```json
[
    {
      "xcmInfo": {
        "symbol": "KSM",
        "priceUSD": 175.11842346191406,
        "relayChain": {
          "relayChain": "kusama",
          "relayAt": 12136571
        },
        "origination": {
          "chainName": "Kintsugi",
          "id": "kintsugi",
          "chainID": 22092,
          "paraID": 2092,
          "sender": "a3crPwJ717zKVvpP8MWscjfVoXgwETmLhpAppat6P5fPLqKSb",
          "amountSent": 1.37495,
          "amountSentUSD": 240.77907633895873,
          "txFee": 0,
          "txFeeUSD": 0,
          "blockNumber": 675237,
          "section": "xTokens",
          "method": "transfer",
          "extrinsicID": "675237-2",
          "extrinsicHash": "0x26a5ae999227e6819710952c1da48502655bf686fe00004e19fe583e878c2b6f",
          "msgHash": "0x929df819dd616e2371d8b76795d428663c421af1538ebb1d1335a1f839d188a7",
          "sentAt": 12136571,
          "ts": 1649259492,
          "complete": true
        },
        "destination": {
          "chainName": "Kusama",
          "id": "kusama",
          "chainID": 2,
          "paraID": 0,
          "beneficiary": "J8zgGfZApQQbBNHGNTttqqQaoJqzQMsiFqi57GbXAY9oYJi",
          "amountReceived": 1.37484333334,
          "amountReceivedUSD": 240.7603970416236,
          "teleportFee": 0.00010666665999981007,
          "teleportFeeUSD": 0.018680746560789826,
          "teleportFeeChainSymbol": "KSM",
          "blockNumber": 12136574,
          "extrinsicID": "12136574-1",
          "eventID": "2-12136574-1-28",
          "ts": 1649259510,
          "status": true
        },
        "version": "V2"
      },
      "destAddress_info": {
        "kusamaAddress": "J8zgGfZApQQbBNHGNTttqqQaoJqzQMsiFqi57GbXAY9oYJi",
        "additional": [
          [
            {
              "Raw": "userpic"
            },
            {
              "Raw": "7b8096c637d32a3636b543b747463590"
            }
          ],
          [
            {
              "Raw": "background"
            },
            {
              "Raw": "b0c4ad41ce0b7418d7009c979e587d2a"
            }
          ]
        ],
        "twitter": "@mwmtg3"
      },
      "destAddress_judgements": []
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
curl "https://api.polkaholic.io/account/crowdloans/FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs?chainfilters=kusama" \
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

## XCM Transfers

```shell
# Get one xcmTranfer involving kbtc on moonriver network between unix_timestamp (1667928000,1668028000)
curl "https://api.polkaholic.io/xcmtransfers?xcmType=xcmtransfer&chainIdentifier=moonriver&symbol=kbtc&startTS=1667928000&endTS=1668028000&limit=1" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response

```json
[
  {
    "xcmInfo": {
      "symbol": "KBTC",
      "priceUSD": 18308.31197363603,
      "relayChain": {
        "relayChain": "kusama",
        "relayAt": 15257458
      },
      "origination": {
        "chainName": "Moonriver",
        "id": "moonriver",
        "chainID": 22023,
        "paraID": 2023,
        "sender": "0x27e6a60146c5341d2e5577b219a2961f2d180579",
        "amountSent": 0.00182979,
        "amountSentUSD": 33.50036616623947,
        "txFee": 0.00011918,
        "txFeeUSD": 0.0009637323303706722,
        "txFeeSymbol": "MOVR",
        "blockNumber": 2955080,
        "section": "ethereum",
        "method": "transact",
        "extrinsicID": "2955080-11",
        "extrinsicHash": "0x7add5e6a7027369a2e69d3ceb95f55b870c719fcd9cfb2948608c3fbc499b908",
        "transactionHash": "0x1078fcc8c8aed1906a8f28a42f86faeca4380fc5584910b79c69eb3c2c92c585",
        "msgHash": "0x131e18138789b700f9ca2fb149bf1a09890c3869b02df00d9c5c634b601f3509",
        "sentAt": 15257458,
        "ts": 1668027996,
        "finalized": true
      },
      "destination": {
        "chainName": "Kintsugi",
        "id": "kintsugi",
        "chainID": 22092,
        "paraID": 2092,
        "beneficiary": "a3dhTbe9t95rXK4vt87uqyTrrhtKcGxtmY8uGcGX27TTEnCuR",
        "amountReceived": 0.00182856,
        "amountReceivedUSD": 33.4778469425119,
        "teleportFee": 1.2300000000000678e-06,
        "teleportFeeUSD": 0.02253437151883276,
        "teleportFeeChainSymbol": "KBTC",
        "blockNumber": 1843330,
        "extrinsicID": "1843330-1",
        "eventID": "22092-1843330-1-8",
        "ts": 1668028020,
        "finalized": true,
        "executionStatus": "success"
      },
      "version": "V4"
    }
  }
]
```

Return the latest 1000 xcm tranfers from all supported networks.

### HTTP Request

`GET https://api.polkaholic.io/xcmtransfers/`

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decorate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data
xcmType   | Filter the result by transact Type.(`xcmtransfer`, `xcmtransact`, or both) i.e. `xcmType=xcmtransfer`  | Yes | all  
chainfilters   | Filter the result by comma-separated chainIdentifiers. i.e. `chainfilters=polkadot,moonbeam,2000`  | Yes | 'all'
symbol   | Filter the result by xcAssets (comma-separated). i.e. `symbol=ibtc,kint`  | Yes | -  
startTS  | Filter the result by startTS (unix timestamp). If startTS is set, endTS must also be set | Yes | -
endTS   | Filter the result by endTS (unix timestamp). If endTS is set, startTS must also be set | Yes | -
limit   | Return the last n recent xcmtransfers i.e. | Yes | 1000

### Response Description

Attribute | Description
--------- | -----------
xcmInfo | An info struct containing {`symbol`, `priceUSD`,`relayChain`, `origination`, `destination`}
sender_info  |  Sender info (if onchain identity is set)
beneficiary_info  |  Beneficiary info (if onchain identity is set)

### XcmInfo Struct Overview

Attribute | Description|
--------- | -----------|
symbol   |  The asset symbol for the primary xcm Asset|
priceUSD   |  The estimated asset price at the time of xcm transfer|
origination   |  Contains the transfer info at the origination chain|
destination  |  Contains information about the destination chain|
relay   |  Contains info about the relayChain|

### Origination Struct

Attribute | Description|
--------- | -----------|
chainName | The name of origination chain
id | The identifier of origination chain
chainID | The identifier of origination chain
sender | Sender address - SS58 or Account20 format
paraID | The paraID of  origination chain (relaychain has paraID of 0)
amountSent | The amount of xc asset to be teleported
amountSentUSD | The estimated value of xc asset to be teleported
txFee | The transaction fee for initiating the xcm on origination chain
txFeeUSD | The transaction fee (evaluated at the time of txn)
txFeeSymbol | The fee-paying symbol for initiating
section | The related  module_call detected by our indexer (i.e. `xcmPallet`, `xTokens`, `polkadotXcm`)
method | The related module_func detected by our indexer (i.e. `limitedReserveTransferAssets`, `transfer`,  `TransferredMultiAssets`) etc  |
extrinsicID  | Unique identifier for an extrinsic
extrinsicHash |  The Blake256(rawExtrinsic) identifying an extrinsic
transactionHash | The corresponding evm txhash if the origination chain is an EVM chain, omitted otherwise
msgHash | The Blake256(msgHex) identifying an extrinsic - potentially NOT unique
sentAt | A “synthetic” relaychain bn where the xcm is being sent to relaychain
ts | The timestamp where the xcm is initiated
isMsgSent | In case of errors on origination chain, the xcm transfer is *TERMINATED* at origination. The xcmMsg is *NOT* relayed to nor received by destination. No assets are actually being teleported in this case while the txFee has been deducted from sender's balance
finalized | Whether the xcm is finalized on origination chain

###  Destination Struct

Attribute | Description|
--------- | -----------|
chainName | The name of destination chain
id | The identifier of destination chain
chainID | The identifier of destination chain
paraID | The paraID of  destination chain (relayChain has paraID of 0)
beneficiary | The beneficiary - SS58 or Account20 format
amountReceived | The amount of xc asset received at destination chain
amountReceivedUSD | The estimated value of xc asset received at destination chain
teleportFee | *XCM fee – computed as amountSent -  amountReceived
teleportFeeUSD | XCM fee (evaluated at the time of txn)
teleportFeeSymbol | The fee-paying symbol for xcmFee
extrinsicID | The extrinsicID on destination chain where matching event is found
eventID | The matching eventID at destination chain, linked to either a success or fail event.
blockNumber | The blockNumber where the xcm is processed at destination chain
ts | The timestamp where the xcm is processed at destination chain
finalized | Whether the xcm is finalized on destination chain
executionStatus | The current known xcm execution status on destination chain, such as {`pending`,`success`, `failed`}
error | In case of xcm error, xc assets are not received by the Beneficiary. An errorInfo with {code, errorType, errorDesc} is provided.

###  RelayChain Struct

Attribute | Description|
--------- | -----------|
relaychain | The relayChain that facilitates the message passing
relayAt | [WIP] The estimated relay chain block when xcmmsg is sent from origination chain to destination chain

### XCM Error codes
See official [Parity Doc](https://github.com/paritytech/xcm-format#8-the-types-of-error-in-xcm) for detail:

Code| ErrorType | Description|
--- | --------- | -----------|
0|Overflow|An arithmetic overflow happened.
1|Unimplemented|The instruction is intentionally unsupported.
2|UntrustedReserveLocation|Origin Register does not contain a value value for a reserve transfer notification.
3|failedToTransactAsset|Origin Register does not contain a value value for a teleport notification.
4|MultiLocationFull|`MultiLocation` value too large to descend further.
5|MultiLocationNotInvertible|"Used by `BuyExecution` when the fees declared to purchase weight are insufficient. `Trap(u64) = 21`: Used by the `Trap` instruction to force an error intentionally. Its code is included."
6|BadOrigin|The Origin Register does not contain a valid value for instruction.
7|InvalidLocation|The location parameter is not a valid value for the instruction.
8|AssetNotFound|The given asset is not handled.
9|FailedToTransactAsset|An asset transaction (like withdraw or deposit) failed (typically due to type conversions).
10|NotWithdrawable|An asset cannot be withdrawn, potentially due to lack of ownership, availability or rights.
11|LocationCannotHold|An asset cannot be withdrawn, potentially due to lack of ownership, availability or rights.
12|ExceedsMaxMessageSize|Attempt to send a message greater than the maximum supported by the transport protocol.
13|DestinationUnsupported|The given message cannot be translated into a format supported by the destination.
14|Transport|Destination is routable, but there is some issue with the transport mechanism.
15|Unroutable|Destination is known to be unroutable.
16|UnknownClaim|Used by `ClaimAsset` when the given claim could not be recognized/found.
17|FailedToDecode|Used by `Transact` when the functor cannot be decoded.
18|TooMuchWeightRequired|Used by `Transact` to indicate that the given weight limit could be breached by the functor.
19|NotHoldingFees|Used by `BuyExecution` when the Holding Register does not contain payable fees
20|TooExpensive|Used by `BuyExecution` when the fees declared to purchase weight are insufficient.
21|Trap(u64)|Used by the `Trap` instruction to force an error intentionally. Its code is included.
22|ExpectationFalse|Used by `ExpectAsset`, `ExpectError` and `ExpectOrigin` when the expectation was not true.

### Undocumented Errors/Warnings
The following error code are undocumented by Parity, which is returned without code & desc:

Code| ErrorType | Description|
--- | --------- | -----------|
NA|weightNotComputable.| -
NA|assetsTrapped.| Teleported/fee-paying asset is put into assetTrap when there's an error or surplus remaining after the execution
NA|barrier | -  

## XCM Messages

```shell
# get xcmtransfers from  moonbeam/moonrivers
curl "https://api.polkaholic.io/xcmmessages?chainfilters=moonbeam,moonriver&limit=5" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response (last 1000 xcmmessages)

```json
[
    {
        "msgHash": "0x5ce0ec0b27e0b05642ca3beadda92bd89de55cf68cf2eea105db21776b34f3d6",
        "msg":{"v2":[{"withdrawAsset":[{"id":{"concrete":{"parents":0,"interior":{"here":null}}},"fun":{"fungible":10000000000}}]},{"clearOrigin":null},{"buyExecution":{"fees":{"id":{"concrete":{"parents":0,"interior":{"here":null}}},"fun":{"fungible":10000000000}},"weightLimit":{"limited":4000000000}}},{"depositAsset":{"assets":{"wild":{"all":null}},"maxAssets":1,"beneficiary":{"parents":0,"interior":{"x1":{"accountId32":{"network":{"any":null},"id":"0x32b276633fb2c5cbabef0408a4f1045fc9603889e481310e9938b68d40d3b92e"}}}}}}]},
        "version": "v2",
        "sentAt": 12742754,
        "chainID": 2004,
        "chainIDDest": 0,
        "msgType": "ump",
        "blockNumber": 12742755,
        "incoming": 1,
        "blockTS": 1667355708,
        "extrinsicHash": "0xd16ab32071e475d6767830e3d8938627573f5112a75703e71c20e10d05f8a0f3",
        "extrinsicID": "2208179-6",
        "sectionMethod": "ethereum:transact",
        "sourceTS": 1667355702,
        "destTS": 1667355708,
        "beneficiaries": "0x32b276633fb2c5cbabef0408a4f1045fc9603889e481310e9938b68d40d3b92e",
        "destAddress": "129UQhit3nnkoctkLPNNWEEbpevzjWRoEbrzXEWZm7LRPDWb",
        "assetsReceived": [],
        "amountSentUSD": 6.4867,
        "amountReceivedUSD": 0,
        "matched": 1,
        "matchTS": 1667355734,
        "parentMsgHash": null,
        "parentSentAt": null,
        "parentBlocknumber": null,
        "childMsgHash": null,
        "childSentAt": null,
        "childBlocknumber": null,
        "blockNumberOutgoing": 2208179,
        "blockNumberIncoming": 12742755,
        "executedEventID": null,
        "destStatus": -1,
        "errorDesc": null,
        "relayChain": "polkadot",
        "id": "moonbeam",
        "idDest": "polkadot",
        "chainName": "Moonbeam",
        "chainDestName": "Polkadot"
      },
    ...
]
```

Return the latest 1000 xcm message from all supported networks.

### HTTP Request

`GET https://api.polkaholic.io/xcmmessages/`

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
decorate  | Whether API should return decorated fields | Yes | true
extra     | Decorate the response with fields like ['usd','address', 'related', 'data'] | Yes | usd,address, data
chainfilters   | Filter the result by comma-separated chainIdentifiers. i.e. `chainfilters=polkadot,moonbeam,2000`  | Yes | 'all'
limit   | Return the last n recent xcmtransfers i.e. | Yes | 1000

### Response Description

Attribute | Description
--------- | -----------
fromAddress  | Sender's pubkey |  
destAddress    | Recipient's pubkey|  

<aside class="information">
This API is in alpha development!
</aside>

## XCM MultiLocation

```shell
# get all known xcmV`Multilocation from kusama + it's parachains
curl "https://api.polkaholic.io/xcm/multilocation/kusama" \
  -X GET \
  -H "Authorization: YOUR-API-KEY"
```

> Example Response

```json
[
    {
        "chainID": 2,
        "paraID": 0,
        "relayChain": "kusama",
        "isUSD": 0,
        "decimals": 12,
        "symbol": "KSM",
        "xcmInteriorKey": "here~kusama",
        "xcmV1MultiLocation": {
            "v1": {
                "parents": 1,
                "interior": {
                    "here": null
                }
            }
        },
        "evmMultiLocation": [
            1,
            []
        ],
        "xcContractAddress": {
            "22007": "0xffffffffffffffffffffffffffffffffffffffff",
            "22023": "0xffffffff1fcacbd218edc0eba20fc2308c778080"
        },
        "xcCurrencyID": {
            "22004": "0",
            "22007": "340282366920938463463374607431768211455",
            "22023": "42259045809535163221576417993425387648",
            "22048": "4294967295",
            "22084": "12",
            "22085": "100",
            "22090": "1",
            "22107": "100",
            "22110": "4",
            "22118": "2"
        }
    },
    {
        "chainID": 21000,
        "paraID": 1000,
        "relayChain": "kusama",
        "isUSD": 0,
        "decimals": 8,
        "symbol": "ARIS",
        "xcmInteriorKey": "[{\"parachain\":1000},{\"palletInstance\":50},{\"generalIndex\":16}]~kusama",
        "xcmV1MultiLocation": {
            "v1": {
                "parents": 1,
                "interior": {
                    "x3": [
                        {
                            "parachain": 1000
                        },
                        {
                            "palletInstance": 50
                        },
                        {
                            "generalIndex": 16
                        }
                    ]
                }
            }
        },
        "evmMultiLocation": [
            1,
            [
                "0x00000003e8",
                "0x040000000000000032",
                "0x0510"
            ]
        ],
        "xcContractAddress": {},
        "xcCurrencyID": {
            "21000": "16"
        }
    },
    {
        "chainID": 21000,
        "paraID": 1000,
        "relayChain": "kusama",
        "isUSD": 0,
        "decimals": 6,
        "symbol": "USDT",
        "xcmInteriorKey": "[{\"parachain\":1000},{\"palletInstance\":50},{\"generalIndex\":1984}]~kusama",
        "xcmV1MultiLocation": {
            "v1": {
                "parents": 1,
                "interior": {
                    "x3": [
                        {
                            "parachain": 1000
                        },
                        {
                            "palletInstance": 50
                        },
                        {
                            "generalIndex": 1984
                        }
                    ]
                }
            }
        },
        "evmMultiLocation": [
            1,
            [
                "0x00000003e8",
                "0x040000000000000032",
                "0x0507c0"
            ]
        ],
        "xcContractAddress": {
            "22007": "0xffffffff000000000000000000000001000007c0"
        },
        "xcCurrencyID": {
            "21000": "1984",
            "22007": "4294969280",
            "22085": "102"
        }
    },
    ...
]
```

Return all known xcmV1Multilocation from a relaychain + its parachains

### HTTP Request

`GET https://api.polkaholic.io/xcm/multilocation/chainIdentifier`

### URL Parameters

Parameter | Description | Optional? | Default |
--------- | ----------- | --------- | ------- |
chainIdentifier | The identifier of the chain to retrieve data about  | Required | -

### Response Description

Attribute | Description
--------- | -----------
chainID | The native chainID of the xcAsset (ex. USDt is a native asset on statemint)
paraID | The native paraID of the the xcAsset (ex.  USDt is a native asset on statemint - paraID 1000)
relayChain | The relaychain where the xcAsset can be teleported
symbol | Human readable symbol for the xcAsset
decimals | Decimals of the xcAsset
xcmInteriorKey|A flattened XCMV1Multilocation struct from relaychain’s “perspective”. Polkaholic uses xcmInteriorKeys to uniquely identify xcAssets across parachains.
xcmV1MultiLocation|A multilocation struct from relaychain’s “perspective”, which can be used by substrate pallet like XcmTransactor
xcCurrencyID|An u128 specifying the xcAsset at origination chain
evmMultiLocation|An encoded byte arrays, which can be used by moonbeam’s precompile contract to specify an xcAsset  (This is a Moonbeam specific concept that’s not used by other parachains)
xcContractAddress*|A precompiled XC20 contract address specifying the xcAsset at origination chain

*This is an EVM specific concept that’s currently used by both Moonbeam and Astar

## XCM Websocket

Subscribe to Polkaholic XCM Websocket feed to receive xcmInfo in realtime. A [demo](https://polkaholic.io/xcminfows) can be found on our website.

# Search

Search API returns a list of {extrinsics, evmtxs, events} given certain user-specified criteria. As of 2022 11-24, decorations(`'usd','address', 'related', 'data'`) are no longer supported.

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

### Response Description

Attribute | Description
--------- | -----------
chainID | The Alternative identifiers of the given chain  |    
eventID | The identifier of an event, in the form of `chainID-blockNumber-extrinsicIndex-eventIndex`
section | The "section" part of the event. Ex: "balances"  |
method  | The "method" part of the event. Ex: "Transfer"  |



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

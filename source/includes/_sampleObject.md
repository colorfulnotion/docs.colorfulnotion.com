<aside class="notice">
This section provides a list of sample objects used by Polkaholic api
</aside>

(under construction)

# Sample Objects


## DecoratedEvents
```shell
# From https://polkaholic.io/tx/0x044e63a8548c51bac4f3cdf71cc3bc31e63b460f7652030604aee4361f1b1878
# eventID = 'chainID-blockNumber-transactionIndex-eventIndex'
```
```json

{
  "eventID": "2-10363322-3-25",
  "docs": "[Contributed to a crowd sale. `[who, fund_index, amount]`]",
  "section": "crowdloan",
  "method": "Contributed",
  "data": [
    "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
    2101,
    8300000000000
  ],
  "dataType": [
    {
      "typeDef": "AccountId32",
      "name": ""
    },
    {
      "typeDef": "u32",
      "name": ""
    },
    {
      "typeDef": "u128",
      "name": ""
    }
  ],
  "decodedData": [
    {
      "data": "FDZV9KZkAjzFSbct4ySSRiUkUTiMt26yGw8RYHiM1EHduDs",
      "typeDef": "AccountId32",
      "name": ""
    },
    {
      "data": 2101,
      "typeDef": "u32",
      "name": "",
      "projectName": "Zeitgeist",
      "relayChain": "Kusama"
    },
    {
      "data": 8300000000000,
      "typeDef": "u128",
      "name": "",
      "symbol": "KSM",
      "dataRaw": 8.3,
      "dataUSD": 1002.4408000000001,
      "priceUSD": 120.776,
      "priceUSDCurrent": 69.8233
    }
  ]
}
```
## DecodedParams
```shell
# From https://polkaholic.io/tx/0x044e63a8548c51bac4f3cdf71cc3bc31e63b460f7652030604aee4361f1b1878
```
```json
[
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
]
```

## EVMInfo
If the substrateTx is linked to an evmTx in EVM pallet, the meta for the linked evmTx will also be returned

```shell
# From https://polkaholic.io/tx/0x003cd404c02683a49b2506c844540a5fabf990f3cdb38662acaa26e4d511e84b
```
```json
{
    "from": "0x0ebf42de8f0f8be37f5570d5fdc9b35d55a36de5",
    "to": "0x7a3909c7996efe42d425cd932fc44e3840fcab71",
    "transactionHash": "0xdd73c2c24ab6942b67865d6d5e8ac905ed39686ae59adef01983658217c397b4"
}
```

# Sample Objects (EVM)


## SubstrateInfo
If the evmTx is linked to an subStrateTx, the meta for the linked subStrateTx will also be returned

```shell
# From https://polkaholic.io/tx/0xdd73c2c24ab6942b67865d6d5e8ac905ed39686ae59adef01983658217c397b4
```
```json
{
    "extrinsicID": "806601-5",
    "extrinsicHash": "0x003cd404c02683a49b2506c844540a5fabf990f3cdb38662acaa26e4d511e84b"
}
```

## Swaps
```json
{
    "type": "swapV2",
    "maker": "0x7a3909c7996efe42d425cd932fc44e3840fcab71",
    "taker": "0x0ebf42de8f0f8be37f5570d5fdc9b35d55a36de5",
    "amount0In": "0",
    "amount1In": "291910433727995110062",
    "amount0Out": "1025000000000000000000",
    "amount1Out": "0",
    "path": "token1 -> token0",
    "lpTokenAddress": "0xd341D2191bb0F84E5c29cB301deF5753Dab1ac04"
}
```

## Transfers
```json
{
    "type": "ERC20",
    "from": "0x0ebf42de8f0f8be37f5570d5fdc9b35d55a36de5",
    "to": "0xd341d2191bb0f84e5c29cb301def5753dab1ac04",
    "value": 0,
    "tokenAddress": "0xAcc15dC74880C9944775448304B263D191c6077F",
    "assetInfo": {
        "asset": "0xacc15dc74880c9944775448304b263d191c6077f",
        "chainID": 1284,
        "chainName": "moonbeam",
        "assetType": "ERC20",
        "assetName": "Wrapped GLMR",
        "decimals": 18,
        "symbol": "WGLMR",
        "isUSD": 0,
        "numHolders": 14324,
        "priceUSDpaths": [
            [
                {
                    "dest": "0x818ec0a7fe18ff94269904fced6ae3dae6d6dc0b",
                    "symbol": "USDC"
                },
                {
                    "route": "0x386204aeb4bcf2a849024f88237c251704d0e976",
                    "dest": "0xacc15dc74880c9944775448304b263d191c6077f",
                    "symbol": "BEAM-LP",
                    "token0Symbol": "USDC",
                    "token1Symbol": "WGLMR",
                    "s": 1
                }
            ]
        ],
        "assetChain": "0xacc15dc74880c9944775448304b263d191c6077f#1284"
    },
    "valueUSD": 0,
    "priceUSD": 3.98584
}
```

## DecodedInput
```json
{
    "decodeStatus": "success",
    "methodID": "0x8803dbee",
    "signature": "swapTokensForExactTokens(uint256 amountOut, uint256 amountInMax, address[] path, address to, uint256 deadline)",
    "params": [
        {
            "name": "amountOut",
            "value": "1025000000000000000000",
            "type": "uint256"
        },
        {
            "name": "amountInMax",
            "value": "115792089237316195423570985008687907853269984665640564039457584007913129639935",
            "type": "uint256"
        },
        {
            "name": "path",
            "value": [
                "0xacc15dc74880c9944775448304b263d191c6077f",
                "0x322e86852e492a7ee17f28a78c663da38fb33bfb"
            ],
            "type": "address[]"
        },
        {
            "name": "to",
            "value": "0x0ebf42de8f0f8be37f5570d5fdc9b35d55a36de5",
            "type": "address"
        },
        {
            "name": "deadline",
            "value": "33180822766000",
            "type": "uint256"
        }
    ]
}
```

## DecodedLogs
```json
{
    "decodeStatus": "success",
    "address": "0xd341D2191bb0F84E5c29cB301deF5753Dab1ac04",
    "transactionLogIndex": "0x3",
    "data": "0x000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000fd31230de2b5ae2ae00000000000000000000000000000000000000000000003790bb8551376400000000000000000000000000000000000000000000000000000000000000000000",
    "topics": [
        "0xd78ad95fa46c994b6551d0da85fc275fe613ce37657fb8d5e3d130840159d822",
        "0x0000000000000000000000007a3909c7996efe42d425cd932fc44e3840fcab71",
        "0x0000000000000000000000000ebf42de8f0f8be37f5570d5fdc9b35d55a36de5"
    ],
    "signature": "Swap(index_topic_1 address sender, uint256 amount0In, uint256 amount1In, uint256 amount0Out, uint256 amount1Out, index_topic_2 address to)",
    "events": [
        {
            "name": "sender",
            "type": "address",
            "value": "0x7a3909c7996efe42d425cd932fc44e3840fcab71"
        },
        {
            "name": "amount0In",
            "type": "uint256",
            "value": "0"
        },
        {
            "name": "amount1In",
            "type": "uint256",
            "value": "291910433727995110062"
        },
        {
            "name": "amount0Out",
            "type": "uint256",
            "value": "1025000000000000000000"
        },
        {
            "name": "amount1Out",
            "type": "uint256",
            "value": "0"
        },
        {
            "name": "to",
            "type": "address",
            "value": "0x0ebf42de8f0f8be37f5570d5fdc9b35d55a36de5"
        }
    ]
}
```

## EVMBlock
```json
{
        "author": "0x2185e7531a57c45416c78d2cc3b1c768df6395f0",
        "baseFeePerGas": 100000000000,
        "difficulty": "0",
        "extraData": "0x",
        "gasLimit": 15000000,
        "gasUsed": 89939,
        "hash": "0xf39971e48932d50a7525175cda670e7e648164b65594fd9ad7864451bde57663",
        "logsBloom": "0x00200000000000000000000080000000000000002000000000000000000000000000008000000000000000000000000000000000000000000000200000280000000001000000000000000008000000200000000000000000000000000000000000000000000000000000000000000000000000000008000000000010000000000000000000000000000000000040000000000000008000080000006000000000020000000000000000000000000000000000000000000000000200000000000000002002000000000000000000000000000000000000001000008002000800200010100000000000000000000000004000000000000000000000000000000000",
        "miner": "0x2185e7531A57C45416C78D2cC3B1C768Df6395F0",
        "number": 811999,
        "parentHash": "0x2acf0851dc51e676e1eb417cc4e40c5265bc5e093e8145593d1742c1576ad0cf",
        "receiptsRoot": "0xb28433a275f19973808350dc48bbdef2037894c7caaa97678ce022b4866e04a4",
        "sealFields": [
            "0x0000000000000000000000000000000000000000000000000000000000000000",
            "0x0000000000000000"
        ],
        "sha3Uncles": "0x1dcc4de8dec75d7aab85b567b6ccd41ad312451b948a7413f0a142fd40d49347",
        "size": 898,
        "stateRoot": "0x999a3a2df22e3fa8221cd192ab70c45d08dede7a1fd2bc57fc9eafe52690f077",
        "timestamp": 1649869074,
        "totalDifficulty": "0",
        "transactions": [
            {
                "chainID": 1284,
                "transactionHash": "0x55785d2ee7acea8808005be93a9542cc3e74d6bb0ea8710a4497a1a56f81d170",
                "substrate": {
                    "extrinsicID": "811999-3",
                    "extrinsicHash": "0x0e4e38c19ae0326c07f5f03d04c4844e1bce3a14d40899e13f9306b92a4a722e"
                },
                "status": true,
                "blockHash": "0xf39971e48932d50a7525175cda670e7e648164b65594fd9ad7864451bde57663",
                "blockNumber": 811999,
                "transactionIndex": 0,
                "timestamp": 1649869074,
                "from": "0x2815c10740F4D738b20FDC13167c865380156623",
                "to": "0x7a3909C7996EFE42d425cD932fc44E3840fCAB71",
                "creates": null,
                "transfers": [
                    {
                        "type": "ERC20",
                        "from": "0x2815c10740f4d738b20fdc13167c865380156623",
                        "to": "0x8ca030649720b94b16e8c3b551cc2ab88c681c0f",
                        "value": "0",
                        "tokenAddress": "0x2CC0A9D8047A5011dEfe85328a6f26968C8aaA1C"
                    },
                    {
                        "type": "ERC20",
                        "from": "0x8ca030649720b94b16e8c3b551cc2ab88c681c0f",
                        "to": "0x2815c10740f4d738b20fdc13167c865380156623",
                        "value": "0",
                        "tokenAddress": "0x322E86852e492a7Ee17f28a78c663da38FB33bfb"
                    }
                ],
                "swaps": [
                    {
                        "type": "swapV2",
                        "maker": "0x7a3909c7996efe42d425cd932fc44e3840fcab71",
                        "taker": "0x2815c10740f4d738b20fdc13167c865380156623",
                        "amount0In": "100000000000000000000",
                        "amount1In": "0",
                        "amount0Out": "0",
                        "amount1Out": "3169878293381724177344",
                        "path": "token0 -> token1",
                        "lpTokenAddress": "0x8ca030649720b94b16e8C3B551cc2ab88c681C0F"
                    }
                ],
                "value": 0,
                "fee": 0.018167678,
                "gasLimit": 132037,
                "gasUsed": 89939,
                "gasPrice": 202,
                "nonce": 25,
                "input": "0x38ed17390000000000000000000000000000000000000000000000056bc75e2d631000000000000000000000000000000000000000000000000000aafc09c3a3335c276400000000000000000000000000000000000000000000000000000000000000a00000000000000000000000002815c10740f4d738b20fdc13167c86538015662300000000000000000000000000000000000000000000000000001e2d832781b000000000000000000000000000000000000000000000000000000000000000020000000000000000000000002cc0a9d8047a5011defe85328a6f26968c8aaa1c000000000000000000000000322e86852e492a7ee17f28a78c663da38fb33bfb",
                "decodedInput": {
                    "decodeStatus": "success",
                    "methodID": "0x38ed1739",
                    "signature": "swapExactTokensForTokens(uint256 amountIn, uint256 amountOutMin, address[] path, address to, uint256 deadline)",
                    "params": [
                        {
                            "name": "amountIn",
                            "value": "100000000000000000000",
                            "type": "uint256"
                        },
                        {
                            "name": "amountOutMin",
                            "value": "3154107754608680773476",
                            "type": "uint256"
                        },
                        {
                            "name": "path",
                            "value": [
                                "0x2cc0a9d8047a5011defe85328a6f26968c8aaa1c",
                                "0x322e86852e492a7ee17f28a78c663da38fb33bfb"
                            ],
                            "type": "address[]"
                        },
                        {
                            "name": "to",
                            "value": "0x2815c10740f4d738b20fdc13167c865380156623",
                            "type": "address"
                        },
                        {
                            "name": "deadline",
                            "value": "33180822766000",
                            "type": "uint256"
                        }
                    ]
                },
                "decodedLogs": [
                    {
                        "decodeStatus": "success",
                        "address": "0x2CC0A9D8047A5011dEfe85328a6f26968C8aaA1C",
                        "transactionLogIndex": "0x0",
                        "data": "0x0000000000000000000000000000000000000000000000056bc75e2d63100000",
                        "topics": [
                            "0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef",
                            "0x0000000000000000000000002815c10740f4d738b20fdc13167c865380156623",
                            "0x0000000000000000000000008ca030649720b94b16e8c3b551cc2ab88c681c0f"
                        ],
                        "signature": "Transfer(index_topic_1 address from, index_topic_2 address to, uint256 value)",
                        "events": [
                            {
                                "name": "from",
                                "type": "address",
                                "value": "0x2815c10740f4d738b20fdc13167c865380156623"
                            },
                            {
                                "name": "to",
                                "type": "address",
                                "value": "0x8ca030649720b94b16e8c3b551cc2ab88c681c0f"
                            },
                            {
                                "name": "tokenId",
                                "type": "uint256",
                                "value": "0"
                            }
                        ]
                    },
                    {
                        "decodeStatus": "success",
                        "address": "0x2CC0A9D8047A5011dEfe85328a6f26968C8aaA1C",
                        "transactionLogIndex": "0x1",
                        "data": "0x0000000000000000000000000000000000000000033b2dfa1c788bd1c43bfc00",
                        "topics": [
                            "0x8c5be1e5ebec7d5bd14f71427d1e84f3dd0314c0f7b2291e5b200ac8c7c3b925",
                            "0x0000000000000000000000002815c10740f4d738b20fdc13167c865380156623",
                            "0x0000000000000000000000007a3909c7996efe42d425cd932fc44e3840fcab71"
                        ],
                        "signature": "Approval(index_topic_1 address owner, index_topic_2 address spender, uint256 value)",
                        "events": [
                            {
                                "name": "owner",
                                "type": "address",
                                "value": "0x2815c10740f4d738b20fdc13167c865380156623"
                            },
                            {
                                "name": "approved",
                                "type": "address",
                                "value": "0x7a3909c7996efe42d425cd932fc44e3840fcab71"
                            },
                            {
                                "name": "tokenId",
                                "type": "uint256",
                                "value": "0"
                            }
                        ]
                    },
                    {
                        "decodeStatus": "success",
                        "address": "0x322E86852e492a7Ee17f28a78c663da38FB33bfb",
                        "transactionLogIndex": "0x2",
                        "data": "0x0000000000000000000000000000000000000000000000abd6e5f9187f2303c0",
                        "topics": [
                            "0xddf252ad1be2c89b69c2b068fc378daa952ba7f163c4a11628f55a4df523b3ef",
                            "0x0000000000000000000000008ca030649720b94b16e8c3b551cc2ab88c681c0f",
                            "0x0000000000000000000000002815c10740f4d738b20fdc13167c865380156623"
                        ],
                        "signature": "Transfer(index_topic_1 address from, index_topic_2 address to, uint256 value)",
                        "events": [
                            {
                                "name": "from",
                                "type": "address",
                                "value": "0x8ca030649720b94b16e8c3b551cc2ab88c681c0f"
                            },
                            {
                                "name": "to",
                                "type": "address",
                                "value": "0x2815c10740f4d738b20fdc13167c865380156623"
                            },
                            {
                                "name": "tokenId",
                                "type": "uint256",
                                "value": "0"
                            }
                        ]
                    },
                    {
                        "decodeStatus": "success",
                        "address": "0x8ca030649720b94b16e8C3B551cc2ab88c681C0F",
                        "transactionLogIndex": "0x3",
                        "data": "0x000000000000000000000000000000000000000000000f4fa2a5ed6d45039d5b00000000000000000000000000000000000000000001e6212d948b77b4396dee",
                        "topics": [
                            "0x1c411e9a96e071241c2f21f7726b17ae89e3cab4c78be50e062b03a9fffbbad1"
                        ],
                        "signature": "Sync(uint112 reserve0, uint112 reserve1)",
                        "events": [
                            {
                                "name": "reserve0",
                                "type": "uint112",
                                "value": "72304510059526599449947"
                            },
                            {
                                "name": "reserve1",
                                "type": "uint112",
                                "value": "2295682137632454490025454"
                            }
                        ]
                    },
                    {
                        "decodeStatus": "success",
                        "address": "0x8ca030649720b94b16e8C3B551cc2ab88c681C0F",
                        "transactionLogIndex": "0x4",
                        "data": "0x0000000000000000000000000000000000000000000000056bc75e2d63100000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000abd6e5f9187f2303c0",
                        "topics": [
                            "0xd78ad95fa46c994b6551d0da85fc275fe613ce37657fb8d5e3d130840159d822",
                            "0x0000000000000000000000007a3909c7996efe42d425cd932fc44e3840fcab71",
                            "0x0000000000000000000000002815c10740f4d738b20fdc13167c865380156623"
                        ],
                        "signature": "Swap(index_topic_1 address sender, uint256 amount0In, uint256 amount1In, uint256 amount0Out, uint256 amount1Out, index_topic_2 address to)",
                        "events": [
                            {
                                "name": "sender",
                                "type": "address",
                                "value": "0x7a3909c7996efe42d425cd932fc44e3840fcab71"
                            },
                            {
                                "name": "amount0In",
                                "type": "uint256",
                                "value": "100000000000000000000"
                            },
                            {
                                "name": "amount1In",
                                "type": "uint256",
                                "value": "0"
                            },
                            {
                                "name": "amount0Out",
                                "type": "uint256",
                                "value": "0"
                            },
                            {
                                "name": "amount1Out",
                                "type": "uint256",
                                "value": "3169878293381724177344"
                            },
                            {
                                "name": "to",
                                "type": "address",
                                "value": "0x2815c10740f4d738b20fdc13167c865380156623"
                            }
                        ]
                    }
                ]
            }
        ],
        "transactionsRoot": "0xae721df5743f9f6f8af02b2dea5dc2625f1703f7824ba5b9a9f4e23be959a353",
        "uncles": []
    }
```

# 安装 geth
```
brew tap ethereum/ethereum
brew install ethereum
``` 

# 配置创世区块
my_genesis.json

```json
{
  "config": {
        "chainId": 0,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
  "alloc"      : {},
  "coinbase"   : "0x0000000000000000000000000000000000000000",
  "difficulty" : "0x20000",
  "extraData"  : "",
  "gasLimit"   : "0x2fefd8",
  "nonce"      : "0x0000000000000042",
  "mixhash"    : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "parentHash" : "0x0000000000000000000000000000000000000000000000000000000000000000",
  "timestamp"  : "0x00"
}
```

# 创建私有链
| 设置区块链数据文件夹 chain_data ,设置创世区块初始化文件为 my_genesis.json
```$xslt
geth --datadir chain_data init my_genesis.json
```
# 建私链

见 [create_private_chain.md](create_private_chain.md)
```$xslt
geth --datadir chain_data init my_genesis.json
```


# 新建账号
```$xslt

personal.newAccount("这里是密码~~~~~")     //创建新用户


eth.accounts                             //查看所有用户
["0x11bbe8db4e347b4e8c937c1c8370e4b5ed33adb3db69cbdb7a38e1e50b1b82fa"]
```

# 删除私链数据
```$xslt
geth removedb --datadir chain_data   #这个不会删除账号
```

# 修改初始化 json 文件
| 分配以太币，单位是 Wei

[分配给账号以太币](https://github.com/ethereum/go-ethereum#operating-a-private-network)
```json
{
  "config": {
        "chainId": 0,
        "homesteadBlock": 0,
        "eip155Block": 0,
        "eip158Block": 0
    },
  "alloc"      : {
    "0x11bbe8db4e347b4e8c937c1c8370e4b5ed33adb3db69cbdb7a38e1e50b1b82fa": {"balance": "111111111"},
    "0x0000000000000000000000000000000000000002": {"balance": "222222222"}
  },
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

# 重新初始化链
```markdown
geth --datadir chain_data init my_genesis.json
```

# 查看账户余额
```markdown
eth.getBalance(eth.accounts[0])
```
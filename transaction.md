# 查看钱包
```markdown
> personal.listWallets
[{
    accounts: [{
        address: "0x1824671775f22a88d73882a02921288f9635a912",
        url: "keystore:///Volumes/Storage/blockchain/testnet/node3/chain_data/keystore/UTC--2018-03-08T09-13-42.980433100Z--1824671775f22a88d73882a02921288f9635a912"
    }],
    status: "Locked",
    url: "keystore:///Volumes/Storage/blockchain/testnet/node3/chain_data/keystore/UTC--2018-03-08T09-13-42.980433100Z--1824671775f22a88d73882a02921288f9635a912"
}]
```

# 查看账户余额
```markdown
> web3.fromWei(eth.getBalance("0x1824671775f22a88d73882a02921288f9635a912"),'Ether')
70.000378000001
```

# 解锁账户
| 没有解锁的账户可以收钱，但是不能转出
```markdown
123456 是密码，如果不写，会有提示让输入，没有密码不能解锁
> personal.unlockAccount("0x1824671775f22a88d73882a02921288f9635a912","123456")
true
```

# 转账
```markdown
> eth.sendTransaction({from: myAddr, to: hisAddr, value:1000000})
"0xa65e69c5036816998ca2bdbdb4b669afe8ea899c6d7f77b8f115e41b668714aa"
```

```markdown
用 Ether 为单位转账
> eth.sendTransaction({from: myAddr, to: hisAddr, value:web3.toWei(2.5, "Ether")})
"0x58b8027381486e9853f3ca6db371791fdbb1d09cf2c11aa8ce596d9591381065"
```

```markdown
加入 gas，矿工的报酬就是 gas

> eth.sendTransaction({from: myAddr, to: hisAddr, value:web3.toWei(2.5, "Ether"), gas:50000, gasPrice:web3.toWei(33, "gwei")})
"0x4a159b26983e91d4217c4396aecdb7c8a21b422de7c930bb0c684cec68449bad"
```
# 查看账户余额
| 发现余额没有变动，一般是还没放入区块链中
```markdown
> eth.getBalance(hisAddr)
0
```

# 等待或者挖矿，让交易成功
```markdown
miner.start()
```

# 再次查看余额
| 交易成功
```markdown
> eth.getBalance(hisAddr)
1000000
```

# 查看还未确认的交易个数
```markdown
> eth.getBlockTransactionCount("pending")
0
```

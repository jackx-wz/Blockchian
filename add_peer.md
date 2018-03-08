# 初始化第一个节点
```markdown
geth --datadir node1/chain_data init ../node1/my_genesis.json

```
```markdown
如果 chain_data 文件夹里面有其他区块链信息，保证不需要这些的情况下先删除
geth --datadir chain_data removedb
```

# 启动第一个节点
| 第一个节点默认端口 30303
```markdown
geth --datadir node1/chain_data console 2>> geth.log
```

# 初始化第二个节点
```markdown
与第一个节点一样，但是数据存放目录需修改 node2/chain_data
创世区块需要一致，所以初始化文件为同一个
geth --datadir node2/chain_data init ../node1/my_genesis.json
```

# 启动第二个节点
| 第二个阶段端口自动变为 30304
```markdown
geth --datadir node1/chain_data console 2>> geth.log
```

# 查看第一个节点的 nodeurl
```markdown
> admin.nodeInfo.enode
"enode://2a9940cfd5051c8160e1ea3800a5d12e62800801844f3cffcc65fdb756747c81b45c5498d84e558b7965671790309084b2422ef70651e18fee40734d6fd7918a@[::]:30303?discport=0"
```

# 第二个节点中加入第一个节点地址
| 就是让两个节点可以互相发现
```markdown
admin.addPeer("enode://2a9940cfd5051c8160e1ea3800a5d12e62800801844f3cffcc65fdb756747c81b45c5498d84e558b7965671790309084b2422ef70651e18fee40734d6fd7918a@[::]:30303?discport=0")
```

# 查看是否已经加入 peers
| 如果是空的 [] 那么就没有加入成功
```markdown
> admin.peers
[{
    caps: ["eth/63"],
    id: "eabccf7b324526450a1e441a288e6ee36124b940902b27ca14bb8c0fe1a2d996f4ed265a0ed6c0c0206bf5f5518d403aed723dd35b09bd46ac1e1a97dedc1e42",
    name: "Geth/v1.8.2-stable/darwin-amd64/go1.10",
    network: {
      inbound: true,
      localAddress: "10.0.1.213:61136",
      remoteAddress: "10.0.1.213:30303",
      static: false,
      trusted: false
    },
    protocols: {
      eth: {
        difficulty: 13635459,
        head: "0x3f5fe50d6313dfce01653a2a42b71f0020ee034683822e27ab83d312431ed2a1",
        version: 63
      }
    }
}]
```

# 在两个节点中分别创建新账号
| 两个节点都新建账号
```markdown
> personal.newAccount("123456")
"0x1824671775f22a88d73882a02921288f9635a912"
```

# 设置 coinbase 账号，就是挖矿的账号
| 将新账号设置为挖矿账号
```markdown
miner.setEtherbase("0x1824671775f22a88d73882a02921288f9635a912")
```

# 启动挖矿
| 在第一个节点挖矿
```markdown
> miner.start()
null
```

# 在两个节点查看区块链节点是否统一
| 在第二个节点查看区块是否增加，如果增加了就成功了
```markdown
> eth.blockNumber
147
```

# 查看两个节点的账号上面的以太币
```markdown
只有挖矿节点的账号有以太币,数字很大，因为单位是 Wei

> eth.getBalance(eth.coinbase)
885468750000000000000

改成 Ether 为以太币单位
> web3.fromWei(eth.getBalance(eth.coinbase),'Ether')
55
```

# 竞争挖矿
| 另一个节点也加入挖矿
```markdown
miner.start()
```

# 查看账号是否都有以太币
```markdown
eth.getBalance(eth.coinbase)
```

# 停止挖矿
```markdown
miner.stop()
```
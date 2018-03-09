# 使用 truffle
solidity 以太坊智能合约的编程语言。
truffle 是 solidity 开发框架。

# 初始化项目
```markdown
> truffle init
  Downloading...
  Unpacking...
  Setting up...
  Unbox successful. Sweet!

  Commands:

    Compile:        truffle compile
    Migrate:        truffle migrate
    Test contracts: truffle test
```

# 配置truffle.js
```markdown
127.0.0.1:13301 是本地私链的 rpc 地址

module.exports = {
    networks: {
        development: {
            host:"127.0.0.1",
            port:13301,
            network_id:"*"
        }
    }
};
```

# 编译智能合约
```markdown
> truffle compile
  Compiling ./contracts/Migrations.sol...
  Writing artifacts to ./build/contracts
```

# 部署智能合约
```markdown
truffle migrate 是 truffle deploy 的别名
```
```markdown
> truffle migrate
  Using network 'development'.

  Network up to date.
```

# 开发环境中查看
```markdown
truffle develop
```
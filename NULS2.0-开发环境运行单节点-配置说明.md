## NULS2.0-开发环境运行单节点-配置说明

### 1. 更新到develop分支最新代码

### 2. 覆盖项目根目录下module.ncf文件内容，如下

```
[global]
encoding=UTF-8
language=en
logPath=../../../../Logs
logLevel=DEBUG
dataPath=../../../../data
#默认链ID
chainId=2
#默认资产ID
assetId=1
#默认链名称
chainName=nuls
mainChainId=2
mainAssetId=1
blackHolePublicKey=0298f88c3cae67385ce3cbee00f78816db3e56e566b62bd0f4c5b45f205d3021c3

[account]
dependent=protocol-update

[network]
port=18001
#魔法参数
packetMagic=20198888
#种子节点
selfSeedIps=localhost:18001

[block]
#启动时自动回滚区块数
testAutoRollbackAmount=0
#最小链接节点数,当链接到的网络节点低于此参数时,会持续等待
minNodeAmount=0
dependent=protocol-update,smart-contract


[consensus]
seedNodes=tNULSeBaMkrt4z9FYEkkR9D6choPVvQr94oYZp
password=nuls123456
dataPath=../../../../../data
logPath=../../../../../Logs
dependent=protocol-update,smart-contract

[smart_contract]
#合约视图方法调用最大消耗的Gas
maxViewGas=100000000
systemLogLevel=WARN

```

### 3. 启动相关模块

![graph](https://github.com/MIMIEYES/readmd/blob/master/package/startModules.png)

其中`MyKernelBootstrap`优先启动，其余模块启动不顺序要求

### 4. 启动好模块后，导入出块账户和创世块账户

 - 执行以下testcase
   
    `io.nuls.contract.tx.base.BaseQuery#importPriKeyTest`
    
### 5. 查看`ConsensusBootstrap`共识模块Console控制台输出的打包日志

类似以下日志

```
2019-06-05 14:41:49.599  [pool-9-thread-6] INFO  - io.nuls.poc.utils.manager.BlockManager.addNewBlock(BlockManager.java:59):区块保存，高度为：1 , txCount: 1,本地最新区块高度为：1
2019-06-05 14:41:52.090  [[consensus2-2]] WARN  - io.nuls.poc.utils.manager.RoundManager.getFirstBlockOfPreRound(RoundManager.java:653):the first block of pre round not found
2019-06-05 14:41:52.097  [[consensus2-2]] DEBUG - io.nuls.poc.utils.manager.RoundManager.calculationRound(RoundManager.java:418):当前轮次为：155971692;当前轮次开始打包时间：2019-06-05 14:41:51
2019-06-05 14:41:52.098  [[consensus2-2]] DEBUG - io.nuls.poc.utils.manager.RoundManager.calculationRound(RoundManager.java:419):
calculation||index:155971692,startTime:1559716911000,startHeight:1,hash:{"bytes":"DiSfxabiwi9JJeFLGatJlo2fct5CKBtQMPrFv3HpUYY="}
round:index:155971692 , start:Wed Jun 05 14:41:51 CST 2019, netTime:(Wed Jun 05 14:41:52 CST 2019) , totalWeight : 0.0 ,members:
tNULSeBaMkrt4z9FYEkkR9D6choPVvQr94oYZp ,order:1,packTime:Wed Jun 05 14:42:01 CST 2019,creditVal:0.0
```

### 6. 节点正常打包后，可部署合约

- 打开以下testcase
  
    `io.nuls.contract.tx.pocm.ContractPOCMSendTxTest`

内部包含部分POCM的功能测试，如果不够测试，请参考代码自行添加单元测试    
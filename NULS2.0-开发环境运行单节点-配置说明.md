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
chainName=nuls2
#本链默认资产符号
symbol=NULS
mainChainId=2
mainAssetId=1
mainSymbol=NULS
blackHolePublicKey=000000000000000000000000000000000000000000000000000000000000000000
#默认资产的小数精确位数
decimals=8

[network]
port=18001
crossPort=28001
#魔法参数
packetMagic=89898989
#种子节点
selfSeedIps=127.0.0.1:18001

[account]
keystoreFolder=/keystore/backup

[block]
#区块最大字节数
blockMaxSize=5242880
#区块扩展字段最大字节数
extendMaxSize=1024
#引发分叉链切换的高度差阈值
chainSwtichThreshold=3
#最小链接节点数,当链接到的网络节点低于此参数时,会持续等待
minNodeAmount=0
#区块同步过程中,每次从网络上节点下载的区块数量
downloadNumber=10
#从网络节点下载单个区块的超时时间
singleDownloadTimeout=15000
#从网络节点下载多个区块的超时时间
batchDownloadTimeout=60000
#区块同步过程中缓存的区块字节数上限(20M)
cachedBlockSizeLimit=20971520
#创世块文件路径(支持绝对路径与相对路径,相对路径相对于此配置文件的目录)
genesisBlockPath=genesis-block.json
dependent=smart-contract

[consensus]
#种子节点列表
seedNodes=tNULSeBaMkrt4z9FYEkkR9D6choPVvQr94oYZp
#出块地址密码
password=nuls123456
#出块间隔时间(单位：s)
packingInterval=10
#共识委托抵押资产链ID
agentChainId=2
#共识委托抵押资产ID
agentAssetId=1
#共识奖励资产ID(共识奖励必须为本链资产)
awardAssetId=1
#共识交易手续费单价
feeUnit=100000
#初始通胀金额
inflationAmount=500000000000000
#通胀开始计算时间(单位:S)
initTime=1563951658
#通缩比例(如果没有通缩则设为100)
deflationRatio=100
#通缩间隔时间(单位：S)
deflationTimeInterval=31536000
#总通胀量
totalInflationAmount=11000000000000000
dataPath=../../../../../data
logPath=../../../../../Logs
dependent=smart-contract

[smart-contract]
#合约视图方法调用最大消耗的Gas
maxViewGas=100000000

[public-service]
#public-service模块对外的rpc端口号
rpcPort=18003
#数据库url地址
databaseUrl=127.0.0.1
#数据库端口号
databasePort=27017
#连接池最大数
maxAliveConnect=20
#连接最大等待时间
maxWaitTime=120000
#连接超时时间
connectTimeOut=30000
dependent=smart-contract
developerNodeAddress=tNULSeBaMuKuKY4UstKpXvGxd7LEvEBtd3NXAG,tNULSeBaMns1C6kTePxcQS7rGAu37foAwAMpri
ambassadorNodeAddress=tNULSeBaMhWyQBHc54oXLXB13WhJsyrTobMYYU,tNULSeBaMtCmUuBHMDAjKVSoVBsAEvLoWCspyE
mappingAddress=tNULSeBaMqTC6rnF56dnJqz1Fb8gMdVxGGvxSf,tNULSeBaMkroWKUKj6X4zURBE3V47VZwMJdHPm
businessAddress=tNULSeBaMnf1qfX7emr14att2DsSb2TSPcPBSL
teamAddress=tNULSeBaMqTvaS2NEEZfdrmPzoRvd8zN6T57LH
communityAddress=tNULSeBaMm9RQLKKUBXKJ1rQ7g4iobmWAB73mS

[cross-chain]
minNodeAmount=1
maxNodeAmount=10
sendHeight=5
byzantineRatio=70
crossSeedIps=127.0.0.1:28001
dataPath=../../../../../data
logPath=../../../../../Logs

[protocol-update]
interval=5

[nuls-api]
dependent=smart-contract
#httpServer的启动ip
server_ip=0.0.0.0
#httpServer的启动port
server_port=18004
```

### 3. 覆盖项目根目录下genesis-block.json文件内容，如下

```json
{
  "height": 0,
  "time": "1531152",
  "txs": [
    {
      "address": "tNULSeBaMvEtDfvZuukDf2mVyfGo3DdiN8KLRG",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMnrs6JKrCy6TQdzYJZkMZJDng7QAsD",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMrbMRiFAUeeAt6swb4xVBNyi81YL24",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMu38g1vnJsSZUCwTDU9GsE5TVNUtpD",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMp9wC9PcWEcfesY7YmWrPfeQzkN1xL",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMshNPEnuqiDhMdSA4iNs6LMgjY6tcL",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMoodYW7AqyJrgYdWiJ6nfwfVHHHyXm",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMmTNYqywL5ZSHbyAQ662uE3wibrgD1",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMoNnKitV28JeuUdBaPSR6n1xHfKLj2",
      "amount": 1000000000000000,
      "lockTime": 0
    },
    {
      "address": "tNULSeBaMqywZjfSrKNQKBfuQtVxAHBQ8rB2Zn",
      "amount": 1000000000000000,
      "lockTime": 0
    }
  ],
  "extend": "010000000100010000000100010001003c64002056e81f171bcc55a6ff8345e692c0f86e5b48e01b996cadc001622fb5e363b421",
  "remark": "4f70656e2c204c69626572616c2c204175746f6e6f6d6f75732c2053656c662d45766f6c76696e670ae5bc80e694beefbc8ce887aae794b1efbc8ce887aae6b2bbefbc8ce8bf9be58c960a4f75766572742c204c696272652c204175746f6e6f6d652c20c389766f6c757469660ae382aae383bce38397e383b3e38081e38395e383aae383bce38081e887aae6b2bbe38081e980b2e58c960ad09ed182d0bad180d18bd182d18bd0b92c20d0a1d0b2d0bed0b1d0bed0b4d0bdd0b0d18f2c20d090d0b2d182d0bed0bdd0bed0bcd0bdd0b0d18f2c20d18dd0b2d0bed0bbd18ed186d0b8d18f0aeab09cebb0a9eca0812020eca784ebb3b4eca08120ec9e90ec9ca8eca08120ed9881ebaa85eca0810a4162696572746f2c204c696272652c20417574c3b36e6f6d6f2c2045766f6c757469766f0ad981d8aad8ad20d88c20d8add8b120d88c20d985d8b3d8aad982d98420d88c20d8aad8b7d988d8b10a4f6666656e2c20667265692c206175746f6e6f6d2c2045766f6c7574696f6e0a45766f6c75c3a7c3a36f206162657274612c206c69767265206520617574c3b36e6f6d610ac39670706e612c20667269612c206175746f6e6f6d612c2065766f6c7574696f6e0ace91cebdcebfceb9cebacf84ceae2c20ceb5cebbceb5cf8dceb8ceb5cf81ceb72c20ceb1cf85cf84cf8ccebdcebfcebcceb72c20ceb5cebeceadcebbceb9cebeceb70a41c3a7c4b16b2c20c3b67a67c3bc722c20c3b67a65726b2c20657672696d0a4f736361696c2c2073616f7220696e2061697363652c206e65616d6873706c65c3a163682c20c3a96162686cc3b36964",
  "privateKey": "009cf05b6b3fe8c09b84c13783140c0f1958e8841f8b6f894ef69431522bc65712"
}
```


### 4. 启动相关模块

![graph](https://github.com/MIMIEYES/readmd/blob/master/package/startModules_v1.jpg)

其中`MyKernelBootstrap`优先启动，其余模块启动不顺序要求

### 5. 启动好模块后，导入出块账户和创世块账户

 - 执行以下testcase
   
    `io.nuls.contract.tx.base.BaseQuery#importPriKeyTest`
    
### 6. 查看`ConsensusBootstrap`共识模块Console控制台输出的打包日志

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

### 7. 节点正常打包后，可部署合约

- 打开以下testcase
  
    `io.nuls.contract.tx.pocm.ContractPOCMSendTxTest`

内部包含部分POCM的功能测试，如果不够测试，请参考代码自行添加单元测试    
## 区块链随机数研究

> 参考资料: 
> 
> [Solidity Pitfalls: Random Number Generation for Ethereum](https://www.sitepoint.com/solidity-pitfalls-random-number-generation-for-ethereum/)
> 
> [Predicting Random Numbers in Ethereum Smart Contracts](https://blog.positive.com/predicting-random-numbers-in-ethereum-smart-contracts-e5358c6b8620)

### 1. 使用未来块的`BlockHash`

以彩票为例，抽奖需要调用两次合约交易，第一次，结束彩票，第二次，抽奖

第一次结束彩票后，记录当前块高度H1，并生成一个数字N，在未来区块高度达到`H1+N`的时候，才能抽奖

第二次抽奖时，根据第一次记录的块高度H1再加上(0~80]个块(待定)得到块高度H2，获取H2这个块的`BlockHash`，以它作为随机种子

ETH不能使用这种方式的原因如下：
![](https://cdn-images-1.medium.com/max/1600/1*eyNTfWTkmM-3YuMca-1H0A.png)

### 2. 随机种子限定在参与者内

# FTP 2

## PoS算法

使用PoW算法来冷启动一条区块链，在早期算力不足的情况下，区块链的安全会受到威胁。我们提出一套新的PoS算法，使用治理币来保护区块链的安全。本算法的设计充分考虑PoS转PoW的场景，当超过一半的投票选择放弃PoS之后，区块链的安全将由PoW来接管。我们假定这一投票决定会在有足够的PoW算力保护之后发生。



{% hint style="info" %}
为什么不直接使用PoS来保护区块链安全？

我们认为，只有矿工贡献资源来交易/交换，才有机会实现可持续的经济模型。

PoS使用资本质押，但是并未消耗资源，用户获得的奖励像是一种利息，但与银行不同，银行将资本放贷给实体经济赚取利差，储户才有利息收入，但质押是纯粹的印钞。PoS的Staking是不可持续的，并非源自交易/交换，需要依靠生态的补贴才可以发展。

比特币使用了PoW算力作为获得奖励的条件，但本质上也没有发生交易。比特币利用了内卷的特性，不断扩大自己对这个世界的影响力，使得更多的能源和算力被用于比特币的安全保护。但从长期看，这是一种不可持续的机制。
{% endhint %}

 使用的变量：

* Prev\_blockhash
* Block\_data
* Secret\_commit
* Address
* Secret
* Staking
* Height
* Timestamp
* Total\_staking

在区块链中会有一张表，记录各自秘密的承诺，以及质押数量

| Address | Secret\_commit      | Staking |
| ------- | ------------------- | ------- |
| 0x1     | 0x5f123c12b33a423e4 | 10      |
| 0x2     | 945456455318        | 1       |
| 0x3     | 723423423423        | 5       |

$$
Pointer = Prev\_blockhash+Secret \pmod {Total\_staking}
$$

计算 Pointer 越接近 0，就应该广播 Secret。如果两个地址都找到了相等的 Pointer，则 Staking 数量较大的 Address 获胜。这里可以想象成一个时钟，时钟的周长是 Total\_staking。

$$
Blockhash = H(Prev\_blockhash | Height | Secret | Address | Timestamp|Block\_data)
$$

暴露 Secret 的 Address 无法参加下一轮的抽签，直到以新的 Secret 重新质押 Token。



参考 PoW：

$$
Blockhash = H(Prev\_blockhash | Height | Nonce | Address|Timestamp | Block\_data)
$$

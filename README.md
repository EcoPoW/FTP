# FTP  1

## 私钥记忆保存方法

区块链和 web3 世界中，私钥保存至关重要。采用目前流行的助记词方法 ([https://en.bitcoin.it/wiki/BIP\_0032](https://en.bitcoin.it/wiki/BIP\_0032))，无法在大脑中记忆。

本文提出简单的私钥记忆和保存方法。



### 问题

目前，大部分的私钥使用助记词生成。最安全的方法是把助记词写在纸上，扔进保险箱。

但是这也造成了新的问题，用户几乎无法记忆自己的助记词。记录助记词的纸制物品也很容易丢失。



### Web2中的密码

在Web2中，很多网站为了增加安全性，对密码的复杂度有了各种要求，比如要求大小写字母，数字混用，这大大增加了忘记密码的可能性。很多时候需要多次尝试才能找到密码。

在此基础上，我们建议只使用**小写的字母**和**数字**，并将空格转成**下划线**字符。



### 方案

我们提出的方案是让用户使用长句子作为秘文，比如两句无关的歌词，再加上一些只有自己知道的秘密字符。两句歌词可以写在常用的笔记本上帮助记忆，秘密字符就如同常用密码。



将秘文经过sha256算法后，得到私钥。私钥可以单独导入Metamask或者在web3py等库中调用。

秘文长度在50个字符以上，可以达到和助记词相等的安全性。


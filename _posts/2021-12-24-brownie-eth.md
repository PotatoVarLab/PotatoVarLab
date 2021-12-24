# Basic Brownie ETH

`Ethereum + Python = Brownie`

通过安装使用`brownie`进行`smart contract`的`compile,test and deploy`,一个非常重要的功能是`verify source`到`etherscan.io`



## Baisc usage

- create a empty folder
- `brownie init` within folder
- Basic project structure
- add `brownie-config.yaml` and config
- Write contract with solidity
- `brownie compile`
- `brownie test`
- write deploy.py script
- `brownie run scripts/deploy.py --network ropsten`



### configuration

> Use infura network API,and set etherscan.io apitoken

使用brownie的test框架时，重要使用pytest包构建，其中account基本使用geth-cli进行生成使用，用于测试



## Plan

> Use Web3.py to interact deployed contracts

How to use Web3.py?

Init object with infura HTTP provider,the object can use `eth` attributes to get some infomations,also can send transaction,but need use private key to signature,that all use api function with parameters

Interact contract need contract address and Abi,the two important things, get deployed contract object, we can use object's function with name to call or build transaction to change states,this also need signature with private key

有个疑问，在send transaction的signature过程中没有直接体现使用public key的过程，如何与知识讲解中的lock关联上？

从死gnature后的hash，同时需要`r,s,v`参数，可以recover，其中核心就是通过`recover_public_key_from_msg_hash`，再通过`public key to_checksum_address`得出address，对比是否与sender's address一致,以此verify sender own “public key”



How to automatic generate contract unit test?

when write a smart contract with solidity,we need to unit test,every time need write test functions that contract supported,if where exists frame to automatic generate unit test code,simple like re-mix web ide deployed contract can test basic function in ui

其中关于send transaction和contract function call transaction到底需要哪些参数，参数的具体含义和必要参数还需要进一步了解，共同的参数包括`nonce,chainId,gas,maxFeePerGas,maxPriorityFeePerGas`,send 还需要`to(address), value(wei)`;call contract function transaction 则不需要这两个参数



## Challenge

由于deploy contract后Permanent & immuable,但是软件升级是必要的，因此三层结构的proxy 工程化合约显得非常的重要，如何根据openzeppli的示例构建适合项目的工程化contract？以及实现背后的基本原理是什么？

`box,proxy-admin,transparentUpgardeableProxy`










# AAVE Flash Loan(AAVE闪电贷)

## 简介
这个项目用AAVE闪电贷在Goerli测试网对自定义DEX中的USDT/USDC之间价差的进行套利, 最终仅以0.5u的premium获取利润110.6u

## 套利逻辑
在自定义的DEX中，USDC/USDT = 1.11, USDT/USDC = 1, 很明显，这里存在套利的机会，用价值为一美元的USDC可以以9折的价买入同样是一美元的USDT，再拿USDT卖出USDC，就能获取10%的利益。

1. arbitrage借款1000usdc
2. arbitrage向dex存入1000usdc
3. arbitrage用1000usdc买入得到1111.11usdt
4. arbitrage向dex存入1111.11usdt
5. arbitrage卖出1111usdt得到1111.11usdc
6. arbitrage还款1000usdc外加0.5usdc手续费
7. arbitrage获利110.6usdc

## Arbitrage合约执行结果
https://goerli.etherscan.io/tx/0x6627443794a84bd49efeadf32d0dfe7c23ba3098ad31544d217331ac67075da7

[![goerli-tx.jpg](https://i.postimg.cc/gjkvzN9W/goerli-tx.jpg)](https://postimg.cc/njgsTKcR)


## Remix导入
import {FlashLoanReceiverBase} from "https://github.com/aave/protocol-v2/blob/master/contracts/flashloan/base/FlashLoanReceiverBase.sol"; import {ILendingPool} from "https://github.com/aave/protocol-v2/blob/master/contracts/interfaces/ILendingPool.sol"; import {ILendingPoolAddressesProvider} from "https://github.com/aave/protocol-v2/blob/master/contracts/interfaces/ILendingPoolAddressesProvider.sol"; import {IERC20} from "https://github.com/aave/protocol-v2/blob/master/contracts/dependencies/openzeppelin/contracts/IERC20.sol";

## 参考文档
* https://docs.aave.com/developers/deployed-contracts/v3-testnet-addresses

* https://docs-aave-com.translate.goog/developers/getting-started/readme?_x_tr_sl=auto&_x_tr_tl=zh-CN&_x_tr_hl=zh-CN&_x_tr_hist=true

* http://app.aave.com/

## 代币详情
USDC contract address: 0x65aFADD39029741B3b8f0756952C74678c9cEC93

USDT contract address: 0x2E8D98fd126a32362F2Bd8aA427E59a1ec63F780

## 部署的Dex.sol(Goerli)
0x32cfF99c99693cac82D08E63139e597494A1aF2B

## 部署的Arbitrage.sol(Goerli)
0x587C339f077E90Ea864b4EA0C42ce1e5bd080cF0

## 为Dex.sol添加流动性
往Dex.sol转入1500USDT, 1500USDC

## 授权(approve)
USDC 1000000000 
USDT 1200000000

## 请求闪电贷
0x65aFADD39029741B3b8f0756952C74678c9cEC93
1000000000




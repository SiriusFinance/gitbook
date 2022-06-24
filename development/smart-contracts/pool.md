# Pool

## Contract info

**Contract name:** Swap

**Contract address**

* 4Pool: 0x417E9d065ee22DFB7CC6C63C403600E27627F333
* Starlay 4Pool: 0x0fB8C4eB33A30eBb01588e3110968430E3E69D58
* BAI Metapool: 0xD18aD1e2992Da974b5A8d69377e6aB3b16e30F29
* JPYC Metapool: 0x3cd1Fa4EeeFdf6c30E66c66A474e8E4dd509f54c
* WBTC Metapool: 0xD25Cf814EeE54840A08Db8dfAbFE445B1DE37f0f
* WETH Metapool: 0x2d5Da7c463B3E8f4CF1AF08a1aA0a5DB9BB644F7
* WBNB Metapool: 0xC9d4f937Fa8e0193b46817a41435a262867ff090
* oUSD Metapool: 0xD18AbE9bcedeb5A9a65439e604b0BE8db0bdB176

View [Sirius on Github](https://github.com/SiriusFinance/siriusfinance-contract)

___

## Interfaces

## Write functions

### **addLiquidity**

```
void addLiquidity(uint256[] amounts, uint256 minToMint, uint256 deadline);
```

### **removeLiquidity**
```
removeLiquidity(uint256 amount, uint256[] minAmounts,uint256 deadline);
```

### **removeLiquidityImbalance**
```
removeLiquidityImbalance(uint256[] amounts, uint256 maxBurnAmount, uint256 deadline);
```

### **removeLiquidityOneCoin**
```
removeLiquidityOneCoin(uint256 tokenAmount, uint256 tokenIndex, uint256 minAmount, address receiver);
```

## Read functions

### **getA**
```
getA() external view returns (uint8 A);
```

### **getVirtualPrice**
```
getVirtualPrice() external view returns (uint8 virtualPrice);
```

### **getTokenBalance**
```
getTokenBalance(uint8 tokenIndex) external view returns (uint8 tokenBalance);
```

### **getTokenIndex**
```
getTokenIndex(string tokenAddress) external view returns (uint8 tokenIndex);
```

### **paused**
```
paused() external view returns (bool isPaused);
```

### **swapStorage**
```
swapStorage() external view returns (
    uint8 initialA,
    uint8 futureA,
    uint8 initialATime,
    uint8 futureATime,
    uint8 swapFee,
    uint8 adminFee,
    string lpTokenAddress
);
```
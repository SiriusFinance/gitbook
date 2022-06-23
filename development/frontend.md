# Frontend

## Pool

### TVL/Fee Reward/24 Hours Volume

https://graph.sirius.finance/static/volume.json

___


## Farming

### calculate APR

1.get farm LpAmount
```javascript
LpAmount = LPTokenContract.balanceOf(farmAddress)
```

2.get LPToken total totalSupply
```javascript
LPTokenTotalSupply = LPTokenContract.balanceOf(farmAddress)
```

3.get pool TVL
```javascript
https://graph.sirius.finance/static/volume.json
```

4. get LPPrice
```javascript
LPPrice = poolTVL / LPTokenTotalSupply
```

5.get farm staked value
```javascript
farmStakedValue = LpAmount * LPPrice
```

6.get farm base rewards
```javascript
oneYearRewardValue = srsContract?.rate() * 60 * 60 * 24 * 365 * SRS_PRICE * FarmControllerContract?.gaugeRelativeWeight(
    FarmAddress,
    nearThursday,
)
baseRewards = oneYearRewardValue / farmStakedValue
```

7.get farm extra rewards
```javascript
rewardCount = await FarmContract?.rewardCount()
RewardTokensList = FarmContract?.getRewardTokensList(
    0,
    rewardCount,
)

for (tokenAddress in RewardTokensList) {
    secondRate = FarmContract?.rewardData(tokenAddress)
    rewardPerYearValue = secondRate.rate * 86400 * 365 * tokenPrice
    oneTokenextraRewards = rewardPerYearValue / farmStakedValue
}

extraRewards = summation all oneTokenextraRewards
```

8.get Rewards APR
```
rewardsAPR = baseRewards + extraRewards
```

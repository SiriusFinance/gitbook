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
```typescript
https://graph.sirius.finance/static/volume.json
```

4. get LPPrice
```typescript
LPPrice = poolTVL / LPTokenTotalSupply
```

5.get farm staked value
```typescript
farmStakedValue = LpAmount * LPPrice
```

6.get farm base rewards
```typescript
function getNearThursday() {
  const str = new Date()
  const Today0 = moment(str).utcOffset(0)
  let ago = 0
  Today0.set({ hour: 0, minute: 0, second: 0, millisecond: 0 })

  const day = new Date(str).getUTCDay()
  const diff = 0
  if (day < 4) {
    ago = 7 - (4 - day)
  } else {
    ago = day - 4
  }
  const final_time = Today0.subtract(ago, "days").unix()
  return final_time
}
nearThursday = getNearThursday()

oneYearRewardValue = srsContract.rate() * 60 * 60 * 24 * 365 * SRS_PRICE * FarmControllerContract.gaugeRelativeWeight(
    FarmAddress,
    nearThursday,
)
baseRewards = oneYearRewardValue / farmStakedValue
```

7.get farm extra rewards
```typescript
rewardCount = FarmContract.rewardCount()
RewardTokensList = FarmContract.getRewardTokensList(
    0,
    rewardCount,
)

for (tokenAddress in RewardTokensList) {
    secondRate = FarmContract.rewardData(tokenAddress)
    rewardPerYearValue = secondRate.rate * 86400 * 365 * tokenPrice
    oneTokenextraRewards = rewardPerYearValue / farmStakedValue
}

extraRewards = summation all oneTokenextraRewards
```

8.get Rewards APR
```typescript
rewardsAPR = baseRewards + extraRewards
```

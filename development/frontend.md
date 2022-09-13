# Frontend

## Pool

### TVL/Fee Reward/24 Hours Volume

https://graph.sirius.finance/static/volume.json

***

## Farming

### calculate APR

> Retrieving the farming APR could be complicated, what shows below is not complete runnable code, it's just for showing the logic behind it.

1. We first need to retrieve how many LP tokens (eg. 4SRS) the farm is holding by calling the 'balanceOf' method.

```javascript
LpAmount = LPTokenContract.balanceOf(farmAddress)
```

&#x20; 2\. Then retrieve the total supply of the LP token.

```javascript
LPTokenTotalSupply = LPTokenContract.totalSupply(farmAddress)
```

&#x20; 3\. Call the subgraph API to get the TVL of the corresponding pool.

```typescript
https://graph.sirius.finance/static/volume.json
```

&#x20; 4\. Get the single LP token price using the TVL to divide the total supply of the LP token.

```typescript
LPPrice = poolTVL / LPTokenTotalSupply
```

&#x20; 5\. Retrieve the total staked TVL of the farm.

```typescript
farmStakedValue = LpAmount * LPPrice
```

&#x20; 6\. Retrieve the base rewards in SRS.

```typescript
// SRS price is fixed to 0.1 at this moment
const SRS_PRICE = 0.1;

// Sirius' rewards reset at 0:00 UTC every Thursday, so we need to get the nearest time point.
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

const nearThursday = getNearThursday()

// srsContract.rate returns of how many SRS is mined per second.
// so the following formula is to determine how many SRS can be retrieved by the farm for a year.
oneYearRewardValue = srsContract.rate() * 60 * 60 * 24 * 365 * SRS_PRICE * FarmControllerContract.gaugeRelativeWeight(
    FarmAddress,
    nearThursday,
)

// the reward for each dollar.
const baseRewards = oneYearRewardValue / farmStakedValue
```

&#x20; 7\. Get farm extra rewards. Besides SRS base reward, some farms could provide extra rewards as well such as incentive programs or partnership programs. please notice that some rewarding tokens might also use fixed price.

```typescript
// get all extra reward tokens.
const rewardCount = FarmContract.rewardCount()
const rewardTokensList = FarmContract.getRewardTokensList(
    0,
    rewardCount,
)

// calculate APR for each token.
const extraRewards = 0;
for (tokenAddress in rewardTokensList) {
    // this token price can be fixed just like SRS, or it needs to be retrieved from external resources. (DEX/CEX/Oracle, etc).
    const tokenPrice = 0.01; 
    
    const secondRate = FarmContract.rewardData(tokenAddress)
    const rewardPerYearValue = secondRate.rate * 86400 * 365 * tokenPrice
    const tokenExtraRewards = rewardPerYearValue / farmStakedValue
    extraRewards += tokenExtraRewards;
}

// here goes the total extra rewards.
cosole.log(extraRewards);
```

&#x20; 8\. Plus the base APR and extra APR together.

```typescript
const rewardsAPR = baseRewards + extraRewards
```

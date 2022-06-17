---
description: pools with unstable assets like JPYC, wBTC, wETH or BNB.
---

# How does unstable crypto pool work?

**Unstable Cryptocurrency pools** are pools that consist of unstable or volatile assets like JPYC, wBTC, wETH or BNB.

_\*JPYC, the Japanese Yen-pegged digital asset, cannot be considered as a standard stablecoin because of the fluctuating exchange rate between it and the dollar. In dollar terms, JPYC carries the characteristics of a volatile asset._

__

Unlike Sirius Finance’s stable pools which only consist of stablecoins pegged to $1 where both impermanent loss and slippage can almost be neglected, the unstable crypto pool consists of unstable assets whose price changes all the time, hence traders tend to exercise **extra cautiousness** **about the possible impermanent loss and slippage.**

To put it simply, based on the Sirius Finance AMM algorithm, the trading rate of a pair and token price mostly depends on the total value of both tokens(the amount of a token multiplied by the current unit price).

Let’s use an example that might not be so accurate but easy to understand to break this down a bit further: In the circumstance of the stable pool, when the ratio of A token total value and B token total value is 50%/50% with deep enough liquidity, then the trading rate will be close to 1A=1B.

### ❓**What happens when it’s not 50%/50% in the stable pool**❓ <a href="#9c19" id="9c19"></a>

if a stable pool consists of 1000 A tokens and 2000 B tokens(both pegged to $1), the trading rate at this point is about 1A = 2B.

The imbalance of a pool generates arbitrage opportunities where users can gain profits by swapping A tokens for more B tokens and selling B tokens in another exchange or over-the-counter trading. This stable pool will be balanced again with more A tokens in, and much more B tokens out.

Therefore, **ALL liquidity providers will take the loss** because clearly there are fewer tokens and the LP amount is still the same:

> _**Less** LP staked value = LP amount \* **Less** LP unit price;_
>
> _LP unit prize = **Less** total value of a pool/total amount of the LP._

Solutions: Sirius Finance mechanism encourages users to deposit or withdraw with a certain ratio of assets which helps with the balance by offering LP token bonus.

If you’re looking for more ways to earn in Sirius Finance please check this article👉: [_**Earn in Sirius Finance: A win for everyone.**_](https://medium.com/@siriusfinance/earn-in-sirius-finance-a-win-for-everyone-a352dce22bd)

### ❓**What happens when the liquidity is not deep enough in the stable pool**❓ <a href="#b044" id="b044"></a>

If a stable pool only consists of 10 A tokens and 10 B tokens(both pegged to $1) and a user expects to swap 5 A tokens for 5 B tokens, he will receive less than 5 B tokens because the swapping result is far away from balance.

Solutions: Sirius Finance offers attractive APR on farms to liquidity providers and traders will be less likely to act towards a more imbalanced situation in order to reduce or even avoid the slippage.

We recommend users learn more about how stablecoin AMM works through this article for a more detailed and precise explanation👉: [_**What is stablecoin AMM?**_](https://medium.com/@siriusfinance/if-you-understand-stablecoin-amm-you-will-know-sirius-finance-better-3d600e8cc3cc)

### 👀**So, what’s the difference between a stable pool and an unstable crypto pool that needs traders to pay extra attention?** <a href="#7fc1" id="7fc1"></a>

* Imbalance: An imbalance can happen **at ANY time** due to the fluctuating price of unstable assets in the unstable crypto pool:

Even when the unstable crypto pool is perfectly balanced in certain instances, due to the frequent fluctuation of unstable assets like BTC, arbitrageurs find opportunities to earn profits like what they do in an unbalanced stable pool.

But, also because of the frequent fluctuation, as long as the liquidity providers don’t withdraw their assets when it is in the status of a loss, **the loss is impermanent which means it can be back at ANY minute.**

* The depth of liquidity will affect an unstable crypto pool more because it magnified the impact of price change: This happens when the pool is imbalanced and the liquidity is not deep.

### 🌟**What is the Sirius Finance team doing to improve?** <a href="#1a04" id="1a04"></a>

1. Restrict the way that liquidity can be added, for example making depositing in the combo the only available option;
2. Increase the Amplification Parameter to maintain low-slippage trading in a wider range；
3. Add “Risk Disclosure” that emphasizes the possible loss due to the nature of unstable cryptos and AMM mechanisms.

### 🚨**Last but not least to EVERY investor:** <a href="#60dc" id="60dc"></a>

**Always be careful with your own assets and understand how things work for them.**

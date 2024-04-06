---
layout: post
title:  "Backtesting Bias"
date:   2024-04-05 14:09:10 +0000
categories: Machine-Learning
permalink: Backtesting-Bias
excerpt: 
---
In an optimal trading environment devoid of backtesting bias, traders would possess a figurative "crystal ball" providing deep insights into the complex dynamics of financial markets, enabling accurate predictions of <!--more--> market behavior and the development of profitable trading strategies. However, given the inherently non-deterministic nature of markets, testing new strategy ideas becomes a challenging endeavor. While traders aspire to validate the profitability of their concepts before committing real capital, the absence of a definitive formula necessitates a process of experimentation.

This experimental phase during strategy development exposes traders to potential pitfalls, leading to significant costs in terms of time, money, and frustration. Essentially, traders face two options when it comes to testing systematic trading strategies:

Assessing the actual performance of the strategy by deploying it with real capital.
Estimating the likely performance of the strategy through simulation, typically using historical data, before engaging in live trading.
In financial trading, simulating past performance is known as backtesting. Contrary to common misconceptions, successful backtesting requires more than simply aligning signals with historical entry and exit prices. It demands a comprehensive approach to generate accurate insights while mitigating the risk of backtest bias.

#Backtest Bias
Backtest bias arises from oversimplified methodologies that overlook critical factors influencing strategy performance, potentially hindering trading success. This bias often stems from subtle yet profound biases within the development process, such as look-ahead bias and overfitting bias.

##Look-ahead Bias
Look-ahead bias occurs when future knowledge influences decisions made during historical scenario analysis, distorting backtest results. Even with backtesting software designed to prevent look-ahead bias, caution is necessary to avoid errors like retrospectively applying trade parameters calculated over the entire simulation period.

##Overfitting Bias
Overfitting bias becomes evident when models perform exceptionally well in backtests but fail to replicate the same success in live trading. This bias typically arises from fitting models too precisely to historical data, resulting in poor performance in real-world scenarios.

To mitigate these biases, traders must adopt rigorous methodologies that account for these complexities. Implementing out-of-sample testing, favoring robustness over in-sample performance, and avoiding over-optimization are crucial steps in reducing the impact of backtesting bias.

While backtesting bias is inevitable to some extent, traders can minimize its influence by adopting a cautious and methodical approach to strategy development and validation. By acknowledging the limitations of backtesting and implementing sound risk management practices, traders can enhance their chances of success in the dynamic world of financial markets.

## So what’s the overarching lesson from all this?
Well, in-sample data is only useful in the following ways:
1. Finding out whether a strategy can be profi table and under what conditions
2. Determining which parameters have a signifi cant impact on performance
3. Determining sensible ranges over which parameters might be optimized
4. Debugging the strategy, that is, ensuring trades are being entered as expected

Given the topic of this post, you’ll notice something missing from that list: measuring the performance of a trading strategy.

Any estimate of performance you derive from an in-sample test is plagued with overfitting and similar backtesting bias and is likely to be an optimistic estimate – unless your entire development process is watertight…but that’s a story for another time.

The solution to overfitting bias is adopting a sensible approach to the marketsand strategy development. This includes:

Keeping trades simple. The fewer the number of fi ttable parameters, the better.
Favouring trades that can be rationalised in a sentence, over blindly data mining fortrading rules.
Optimising for robustness, not in-sample performance (more on this later).
Avoid the temptation to be precise in your model specifi cation. Market data isnoisy and fickle, and any signal is weak.
Avoid trades that will, at best, marginally cover retail trading costs, such asscalping.

## Backtesting Bias
This one is unavoidable. So, rather than spending an eternity trying to eliminatethis bias entirely, just be aware of it and accept that, generally, your strategieswon’t perform as well in the markets as they did in your simulations.

You’ll commonly introduce data-mining bias when selecting the best performerfrom a bunch of strategy variants, variables or markets to continue developing.If you’re persistent enough in trying strategies and markets, you’ll eventuallyfind one that performs well simply due to luck.

Think of it this way. Say you develop a trend following strategy in FX. Thestrategy crushes its backtest on EUR/USD but flops on USD/JPY. Any sensibleperson would trade the EUR/USD market, right? Sure, but you’ve just introduced selection bias into your process. Now, your estimate of the strategy’sperformance is upwardly biased. Should you throw the strategy in the bin? Not necessarily. Maybe it performed well on EUR/USD specifically for good reason.But nevertheless, some selection bias has crept into your development process.

There are statistical tests to account for data mining bias, including comparingthe performance of the strategy with a distribution of random performances. You can find examples of this in the Robot Wealth Advanced Course.

You can also use out-of-sample data, but this quickly becomes problematic aswe only have a finite amount of historical data on which to develop.
So your best bet to overcome selection bias is simply adopting a sensible, measured approach to strategy development, as outlined above.
The more complex your approach, the more likely you are to fall into thebacktesting bias traps we’ve talked about above. Either way, it’s surprisingly easy to find strategies that appear to do well, but whose performance turns outto be due to luck or randomness. That’s part of the game.






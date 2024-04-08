---
layout: post
title:  "Liquidity Risk Management and EWI"
date:   2024-04-02 21:53:10 +0000
categories: Algorithmic-Trading
permalink: Liquidity-Risk-Management-and-EWI
---

<!-- This content will not appear in the rendered Markdown -->

One of the paramount advantages of contemporary financial risk management lies in its remarkable objectivity. It adopts a scientific methodology, leveraging mathematics and statistics to quantify and assess financial instruments and investment portfolios. Although these mathematical <!--more--> instruments wield substantial influence, they remain just that—tools. Should we operate under unjustified assumptions, misapply models, present outcomes inadequately, or worse, have our insights disregarded, even the most sophisticated mathematical frameworks would prove futile. After all, having flawlessly prepared eggs holds little significance if the customer's request was for a steak. 

> **"**
> ...there is also broad belief among users of financial liquidity—traders, investors and central bankers—that the principal challenge is not the average level of financial liquidity... but its variability and uncertainty.... —Persaud (2003)

## What is risk?
In colloquial terms, "risk" typically refers to the potential for negative outcomes. Something is considered risky when its final result is uncertain, with a chance of adverse consequences. However, different risk measures handle positive and negative outcomes differently. To address this, risk managers often refer specifically to downside risk when dealing with negative outcomes.

Financial risk is commonly categorized into four main types: market risk, credit risk, liquidity risk, and operational risk. Most financial transactions involve elements of all four types of risk to some extent. Consequently, risk management departments in financial institutions are often structured accordingly. For instance, market risk and liquidity risk are frequently managed together due to their interconnected nature. Additionally, many firms have an enterprise risk management group, bringing the total principal areas of risk management to five.

Some financial experts distinguish between risk and uncertainty, but a more useful distinction might be between intrinsic risk and extrinsic risk. Intrinsic risk refers to risks inherent to financial instruments, which cannot be mitigated regardless of the level of knowledge about the instrument, except by reducing the investment size.

#### History
Long-Term Capital Management (LTCM) is significant in the annals of risk management for several reasons. The collapse of LTCM in 1998 sent shockwaves through the financial community. At the time, it stood as one of the largest and most esteemed hedge funds globally, boasting an impressive track record and founded by notable figures like John Meriwether, Myron Scholes, and Robert Merton. LTCM's extensive portfolio and network of counterparties raised concerns among regulators, who feared its downfall could wreak havoc on the broader financial system. The New York Fed convened an emergency meeting of major investment bank heads to oversee the orderly liquidation of LTCM's assets. The fact that a relatively small firm, employing fewer than 200 individuals and virtually unknown outside financial circles, could pose such systemic risk underscored the remarkable expansion of non-traditional financial markets, particularly derivatives and hedge funds, during the 1980s and 1990s. This growth alone justifies LTCM's place in the history of risk management.

Another often overlooked aspect of LTCM's story is its founders' perception of risk management as a tool to reduce capital requirements for both financial and non-financial entities. The idea was that by freeing up capital, firms could allocate resources more efficiently, fostering greater productivity across the economy. While LTCM's demise revealed clear issues of overleverage and undercapitalization, the concept that effective risk management can enhance firms' efficiencies remains valid. Finally, LTCM's failure, partly attributed to its flawed risk models and their application, served as a wake-up call for the risk management community. The external trigger of LTCM's collapse—the Russian debt default—continues to underpin stress tests at numerous financial institutions and prompted a reevaluation of historically-based quantitative risk models, driving the search for more robust solutions.

Another pivotal player in risk management history is RiskMetrics. Founded in 1998 as a spin-off from JP Morgan, it went public in 2008 before being acquired by MSCI Inc. in 2010. RiskMetrics stood out as one of the premier companies exclusively dedicated to risk management, with its software still utilized by major financial firms worldwide. However, its most enduring legacy lies in its contribution to risk management methodology. In 1992, RiskMetrics released the RiskMetrics Technical Document, outlining its approach to risk evaluation and popularizing the concept of value at risk (VaR). Alongside standard deviation, VaR emerged as a key statistic for summarising financial risk, solidifying RiskMetrics' place in the history of risk management.

#### Future
Despite experiencing significant growth in recent years, financial risk management remains a relatively young discipline. Anticipating numerous changes in the roles of financial risk managers in the near future is inevitable. Moreover, we can expect to witness a shift towards a more integrated approach to risk management and performance analysis, which have traditionally been treated as separate functions by most financial firms.

Nevertheless, there are still critical areas of risk management, such as liquidity risk, where widely accepted models and standards have yet to be developed. Liquidity, often overlooked in the past, has emerged as a crucial source of financial risk. The finance industry has paid a hefty price for neglecting liquidity risk while focusing solely on other aspects of risk modeling.

#### Liquidity Modelling
Recognizing the time lag between changes in a variable's value and its impact on the real market is becoming increasingly pivotal for successful modeling. The significance of liquidity has been underscored and has garnered significant attention since the global financial crisis of 2007 – 2008.

The concept of liquidity encompasses various facets. Broadly, an asset is considered liquid if it is easily convertible to cash. This entails the ability to sell the asset swiftly, affordably, and without causing significant price fluctuations—qualities encapsulated by liquidity's key characteristics: tightness, immediacy, depth, and resiliency. Similarly, a market is deemed liquid if positions can be unwound promptly, at minimal transaction costs, and without substantial price deterioration.

Different types of liquidity risk exist, including transaction liquidity risk, which arises from the possibility of adverse price movements during asset transactions. Funding liquidity risk, also known as balance sheet risk, occurs when a borrower's credit position deteriorates or is perceived to do so by market participants, especially when longer-term assets are funded with shorter-term liabilities, leading to a maturity mismatch. Additionally, systemic risk, posing a threat to the overall financial system, arises from severe financial stress that impairs credit allocation across the system.

Liquidity risks materialize when bid-ask spreads fluctuate, the trader's actions influence the equilibrium price of the asset (resulting in adverse price impacts), or when the asset's price deteriorates during the execution of a trade, termed as slippage.

Monitoring future cash inflows and outflows is crucial for managing quantitative liquidity risk in banks. Liquidity risk can stem from various factors, including both positive and negative cash flows, associated with current and projected contractual obligations arising from routine business operations. Identifying sources of liquidity is essential as they contribute to managing and hedging liquidity risk.

Cumulative expected cash flows encompass both positive and negative cash flows projected over time, starting from a specific reference point. For a series of contracts or securities (d1, d2...), the anticipated positive and negative cash flows at a given time (t1) relative to the reference time (t0) can be calculated using the following formula:

$$ Cf_{e}^+(t_{0},t_{1}) = E\Big[\sum_{j=1}^N cf^+(t_{0},t_{1};d_{j})\Big] $$

$$ Cf_{e}^-(t_{0},t_{1}) = E\Big[\sum_{j=1}^N cf^-(t_{0},t_{1};d_{j})\Big] $$


### Early Warning Indicators

In risk management, early warning indicators (EWIs) serve as vital signals akin to warning lights on a car dashboard. These indicators are alterations in key metrics—be they qualitative or quantitative—that may signify an impending liquidity issue, varying in severity and priority.

For instance, consider three potential scenarios arising from EWIs:

- Immediate indication of an urgent problem requiring immediate action.
- Indication of a potential problem necessitating future attention.
- Call for further analysis to ascertain the presence of a problem and determine necessary actions, if any.

The primary objective of EWIs is to prompt management acknowledgment of the situation, fostering essential dialogue and actions, along with proper documentation.

#### Framework
The EWI framework encompasses measures, escalation, reporting, integrated systems, and thresholds. Transitioning effectively from measures to escalation mandates timely reporting, supported by integrated systems and appropriate thresholds.

#### Measures
A forward-looking perspective on liquidity risk exposures is paramount. Evaluation should encompass both balance sheet and off-balance sheet items, considering normal and stressed states across various time frames. Ultimately, measures should forecast future cash flows and liquidity positions.

EWIs should incorporate both internal and external measures. Internal measures focus on the bank's balance sheet, while external measures scrutinize macroeconomic factors. A robust EWI should detect internal stress events before they become publicly evident. Additionally, EWIs should be leading and granular, providing advance warning signals and sharp indicators despite data noise.

#### Normal and Stressed States
EWIs are crucial in normal operating conditions to signal potential deterioration in a bank's financial position. Simultaneously, stress testing in hypothetical but plausible scenarios helps determine whether the bank possesses sufficient liquid resources to withstand stress situations and uncover systemic risks.

#### Different Time Horizons
Considering various time horizons is essential, given the differing durations of the bank's assets and liabilities. Time horizons such as hourly, daily, weekly, and monthly are effective for early warnings due to their shorter durations.

### Applications in liquidity risk management process

#### Escalation
EWIs play a pivotal role in potentially escalating issues to relevant management personnel, enabling appropriate remedies based on issue severity. Clear inclusion of EWIs in an escalation plan enhances their effectiveness in LRM.

#### Reporting
Timely reporting of EWIs, such as daily or even intraday for banks involved in significant trading activity, allows adequate time to respond to negative events. Reporting should strike a balance between breadth to cover a range of relevant matters and focus on critical aspects.

#### Integrated Systems
Integrated data processing systems ensure consistent and accurate reporting of measures by consolidating data from multiple sources. This provides liquidity risk managers with valuable internal EWI information complementing external measures.

#### Thresholds
EWI thresholds can adopt a "green, amber, and red" stoplight approach, with each colour signifying varying degrees of action urgency. Calibration from green to amber should be meticulous to avoid undetected problems or unnecessary alerts.

#### Industry Practices
Banks and financial institutions are increasingly adopting EWI dashboards to facilitate supervisory duties and enhance risk reporting.

EWI Guidelines from regulators and supervisors
Regulatory guidelines on EWIs have been established by entities like the Office of the Comptroller of the Currency (OCC) [^1], the Basel Committee on Banking Supervision (BCBS)[^2] [^3], and the Federal Reserve [^4], aiming to improve liquidity risk management practices.

EWIs are indispensable tools in liquidity risk management, guiding timely actions and fostering effective risk mitigation strategies.

#### Net liquidity and Strategies

Liquidity epitomizes a financial institution's ability to access funds promptly and at a low cost, precisely when required. Maintaining liquidity is paramount for all financial entities, as any insufficiency can signal financial distress and undermine public confidence.

A firm's net liquidity position is determined by the disparity between the liquidity inflows and outflows:

Net Liquidity Position (L) = Liquidity Inflows - Liquidity Outflows

Where:

- Liquidity Inflows include incoming deposits, customer loan repayments, asset sales, revenue from nondeposit services, and money market borrowings.
- Liquidity Outflows comprise deposit withdrawals, borrowing repayments, dividend payments, loan requests, and other operating expenses.

If the demand surpasses the supply (L < 0), the firm faces a liquidity deficit and must secure additional funds. Conversely, if the supply exceeds the demand (L > 0), the firm has a liquidity surplus, necessitating investment to cover future liquidity requirements. However, in reality, demand and supply seldom align, resulting in perpetual shifts from liquidity deficit to liquidity surplus positions. Moreover, funding sources that bolster the firm's liquidity often yield minimal returns, compelling a delicate balance between liquidity and profitability.

Timing plays a pivotal role in liquidity management, with some needs being immediate (e.g., when certificates of deposits [CDs] mature, and customers seek alternative investment options), while others are long-term, allowing access to funds from diverse sources.

Liquidity challenges arise due to various factors. Financial institutions often grapple with maturity imbalances between short-term borrowings (requiring imminent liabilities settlement) and long-term lending (entailing prolonged customer payments). Interest rate risk (associated with fluctuating rates) and availability risk (liquid funds not accessible when needed) are two prevalent risks stemming from this disparity.


[^1]: OCC (2012) Guidelines. EWIs should exist for securities and derivatives with embedded options (e.g., callable debt) to indicate when those options are likely to be exercised and/or any contingent liabilities associated with the embedded options. EWIs should provide advance notice of a possible negative event to give the bank enough time to prepare. Examples of EWIs include: Reduced financing to be provided by lenders. More stringent requirements to issue long-term debt. Forthcoming regulatory changes. Capital, asset quality, management, earnings, liquidity, and sensitivity (CAMELS) rating downgrades. Spread increases on fixed income and swap products. Falling stock prices. Higher borrowing rates in normal market conditions. Reduced deposits by portfolio managers and funds. Higher margins required.


[^2]: BCBS (2008) Guidelines. Banks need to have indicators available to signal deterioration of liquidity or increased need for funding. EWIs are quantitative or qualitative and include: Very sharp increase in assets. More concentrated assets or liabilities. More currency mismatches. Lower liability durations. Frequent occurrences of breaches or near breaches of limits.


[^3]: BCBS (2012) Guidelines. Examples of intraday liquidity indicators include: Daily maximum liquidity. Intraday liquidity availability. Total intraday payments, including the timing of them. Key obligations (e.g., time-sensitive). Amount of payments made for financial institution customers. Intraday lines of credit provided to financial institution customers.

[^4]: Federal Reserve (Supervision and Regulation [SR] 10-6) Guidelines. Use EWIs and event triggers to identify possible constraints on liquidity. The EWIs should be consistent to the firm’s liquidity risk profile. Advance notice of potential problems allows the firm more time to prepare and allows them a way to relay the information to relevant internal or external parties. Examples of EWIs include: Bad publicity surrounding specific assets held by the firm. Possible worsening of the firm’s balance sheet (e.g., decreased assets, increased liabilities). Increasing spreads for fixed income and swap products.


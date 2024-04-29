---
layout: post
title:  "Kalman Filters"
date:   2024-04-07 07:53:10 +0000
categories: Algorithmic-Trading
permalink: Kalman-Filters
---

Noise in data refers to any unwanted or irrelevant information that interferes with the transmission or processing of a signal. In signal processing, the goal is to extract the useful information (the signal) from the noise. This can be particularly challenging in scenarios like wireless communication, where signals are transmitted through the air and can be distorted or contaminated by various environmental factors. Techniques such as filtering and noise reduction are used to mitigate the effects of noise and recover the <!--more--> original signal as accurately as possible.

The concept of noise extends to various domains such as data science and finance, where raw data typically contains valuable information, like trading signals, amidst irrelevant noise. Extracting and distinguishing this meaningful data from extraneous noise presents a significant challenge, particularly when the true signal is unknown.

The Kalman filter stands out as a powerful tool in dynamic linear modeling, particularly for analyzing sequential data like time series. Unlike traditional methods such as moving averages or exponential moving averages, which rely on fixed-size windows or predetermined weights, the Kalman filter dynamically adjusts its estimates based on incoming information. It does so by incorporating new data into its calculations, continually updating its predictions of the current state of the time series through a probabilistic framework.

Specifically, the Kalman filter operates as a probabilistic model that accounts for a sequence of observations, denoted as $$z_{1}, z_{2}, …, z_{T}$$, and their corresponding hidden states, represented as $$x_{1}, x_{2}, …, x_{T}$$. This model iteratively refines its estimates of the hidden states by recursively applying two main steps: prediction and update. In the prediction step, the filter forecasts the next state based on the previous state and the system dynamics. Then, in the update step, it assimilates the most recent observation, refining its prediction based on the observed data and its associated uncertainty.

By dynamically adjusting its estimates in response to new information, the Kalman filter excels in scenarios where data evolves over time and where accurately tracking the underlying process is paramount. Its versatility and adaptability make it a cornerstone in various fields, including engineering, finance, and robotics, where real-time decision-making relies on precise and up-to-date information.

The Kalman filter is a powerful algorithm designed to leverage noisy observations of a system over time, enabling real-time estimation of its parameters, some of which may be unobservable, and forecasting future observations. At each time step, it performs prediction, measurement intake, and self-updating based on the comparison between prediction and measurement.

The filter prioritizes high-accuracy estimates, crucial for making precise predictions and informed decisions. Consequently, it finds extensive application in robotics and real-time systems where dependable information is indispensable.

Notably, the Kalman filter excels in efficiently estimating future state variables within nonlinear prediction systems. Regarded as an optimal estimator, it proves particularly valuable in predictive model development, especially when dealing with limited dataset sizes.

#### How does it work?

The algorithm operates as follows.

  1. Input Parameters - Receive a mathematical model of the system comprising:
<ul>
<li>The transition matrix (commonly denoted as $$A$$), indicating the system's evolution from one state to another. For example, in modeling a car's movement, kinematic equations could compute the subsequent position and velocity based on prior values. Alternatively, for a stable system, a random walk model might suffice.</li>
<li>The observation matrix (typically denoted as $$H$$), specifying the expected next measurement based on the predicted state. In simpler cases like measuring a car's position, it might directly extract position values from the state. In more complex scenarios such as linear regression, the state represents model coefficients, and the next measurement is predicted from the linear equation.</li>
<li>Any control factors influencing state transitions but not directly measured (summarized in matrix B and time-varying control vector $$ u_{t} $$).</li>
<li>Covariance matrices for transition noise (Q) and measurement noise (R).</li>
</ul>

  2. Initial Estimation:
<ul>
<li>Accept an initial estimate ($$μ_{0}$$) of the system state and its estimation error ($$σ_{0}$$).</li>
</ul>

  3. At each timestep:
<ul>
<li>Estimate the current system state ($$x_{t}$$) using the transition matrix.</li>
<li>Receive new measurements ($$z_{t}$$).</li>
<li>Update the current state estimate ($$x_{t}$$) and its covariance matrix ($$P_{t}$$) by considering the conditional probability of measurements given the state, while factoring in uncertainties in both measurement and state estimation.</li>
</ul>

The Kalman filter relies on the following assumptions to effectively recover the hidden state:

  1. Linearity: The system under consideration behaves linearly.
  2. Markovian Property: The hidden state process follows a Markov chain, meaning that the current state ($$ x_{t} $$) depends solely on the most recent prior state ($$x_{t-1}$$).
  3. Gaussian Noise: Measurements are affected by Gaussian, uncorrelated noise with a constant covariance.

Hence, the Kalman filter shares similarities with a hidden Markov model (HMM), albeit with some key distinctions. In the Kalman filter, the latent variable's state space is continuous, and both hidden and observed variables follow normal distributions, typically denoted with mean and standard deviation sigma.

Assuming the following linear equation for evolution of the state:
$$ x_{k} = F_{k}x_{k−1} + w_{k} $$

where:

$$ x_{k} $$ is the true state at time $$t_{k}$$,

$$ F_{k} $$ iis the state transition matrix assumed to be time dependent,

$$ w_{k} $$ is the process noise assumed to be a multivariate normal distribution with zero mean and covariance $$Q_{k}$$, that is, $$w_{k} ∼ N(0,Q_{k})$$.

The basic Kalman filter is meant for linear systems, but challenging scientific problems, for example in satellite navigation, are nonlinear and therefore it was necessary to implement a special version of the Kalman filter called the extended Kalman Filter (EKF).

A Kalman filter can be adapted to model non-linear transition and observation functions effectively. To handle such cases, extended and unscented Kalman filters are available, with the latter conveniently integrated into pykalman. These filters are capable of handling scenarios where noise is not simply additive, such as when it's proportional to the measurement's size. Moreover, they allow for the specification of non-Gaussian errors, a particularly useful feature when dealing with financial data, which often exhibits heavy-tailed distributions.

Key disadvantages are the assumptions of linearity and Gaussian noise that financial data often violates.
As we know in reality, in a temporal and spatial time-series of financial data (e.g. stock prices) there are common nonlinearities, we will be discussing the Extended Kalman Filter (EKF) as well as the Unscented Kalman Filter (UKF).

> References:
> 1. Dixon, M. F., Halperin, I., Bilokon, P. (2020). Machine Learning in Finance. Springer.
> 2. Alireza Javaheri, et al. Filtering in Finance
> 3. Guo, M., & Zhang, Q. (2021). Machine Learning for Asset Management: A Primer. Journal of Portfolio Management, 47(2), 114-128.

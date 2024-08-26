# BDT

The Black-Derman-Toy (BDT) model is a one-factor short-rate model used in the pricing of fixed income securities, particularly interest rate derivatives like bond options and interest rate caps/floors. The BDT model assumes that the short-term interest rate (the "short rate") follows a lognormal process, meaning that the short rate is always positive and exhibits volatility that can change over time.


Short Rate:
The short rate is the interest rate for a very short period (typically overnight). In the BDT model, it is the key variable that evolves over time in a stochastic manner.

Binomial Tree:
The BDT model uses a binomial tree structure to model the evolution of the short rate over discrete time steps. Each node in the tree represents a possible future short rate.
Lognormal Process:

The BDT model assumes that the short rate follows a lognormal distribution, meaning that the logarithm of the short rate follows a normal distribution. This ensures that the short rate remains positive.

1. Short Rate Dynamics
The short rate at time t_i  and state j is given by:
r(t_i, j) = r(0, 0) * exp( (alpha_i) * (i - 2*j) * sqrt(delta_t) )
Where:
r(t_i, j) is the short rate at time step i and state j.
r(0, 0) is the initial short rate.
alpha_i is a volatility parameter at time i.
delta_t is the time step length.

2. Forward Rate Dynamics
The BDT model fits forward rates to the short rate tree. The forward rate at time t_i is:
f(t_i) = r(0, 0) + ( (i / T) * (r(t_i, 0) - r(0, 0)) )
Where:
f(t_i) is the forward rate at time step i.
T is the total number of time steps.

3. Pricing Bonds
The price of a bond using the BDT model is calculated using backward induction. Starting from the bond's final cash flow (face value and any coupon payment), the bond price at each node is:
P(t_i, j) = ( C + 0.5 * (P(t_{i+1}, j) + P(t_{i+1}, j+1)) ) * exp(-r(t_i, j) * delta_t)
Where:
P(t_i, j) is the price of the bond at time step i and state j.
C is the coupon payment.
r(t_i, j) is the short rate at time step i and state j.


Constructing the BDT Tree:
Use the initial forward rates and the volatility parameter to build the BDT tree for short rates.

Pricing a Bond:
Starting from the bond's maturity, calculate the bond price at each previous time step using backward induction.

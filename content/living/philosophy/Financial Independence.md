# Financial Independence

As an independent citizen in a thriving country, you earn salaries, pay checks for your family and invest your savings to compound the profits.

Your dream is that one day, you don't have to worry about losing the job -- the passive income can still cover your paycheck. And more ideally, your savings earn as much as you can -- you can just retire early!

What you would need to do is:

1. Save as much as possible, live in low cost
2. Try to earn money from the market, create passive income and make the best effort to avoid losing money.

But does it really work? Let's solve it by math and visualize it.

# Settings

you earn $\alpha\_{n}$ money and spend $\beta\_{n}$ money every year, so you save $\delta\_{n}=\alpha\_{n}-\beta\_{n}$ per year, the earning and expense increase with rate $r\_{1}$ per year, and so as $\delta\_{n}$. The feasible investment return is $r\_{2}$.

$$
\begin{align}
\beta\_{n} & = (1 + r\_{1})\beta\_{n-1} \\
\alpha\_{n} & = (1 + r\_{1})\alpha\_{n-1} \\
\delta\_{n} & = \alpha\_{n} - \beta\_{n} = (1 +r\_{1})\delta\_{n-1}
\end{align}
$$

Question: when you can achieve financial independence?

the next year asset $x\_{n}$:

$$
\begin{align}
x\_{n+1} & = x\_{n} (1 + r\_{2}) + \delta\_{n+1} \\
\delta\_{n+1} & = \delta\_{n} ( 1 + r\_{1}) \\
x\_{0} & = 0
\end{align}
$$
financial independence conditions

## solve $x\_{n+1}$, $\beta\_{n+1}$

the formula of $x\_{n+1}$
$$
\begin{align}
x\_{n+1} & = \delta\_{1}(1+r\_{2})^{n} + \delta\_{2}(1+r\_{2})^{n-1} + \dots + \delta _{n+1} (1+r_{2})^{0} \\
& = \delta\_{1} \left\[ (1+r\_{1})^{0}(1+r\_{2})^{n} +  \right (1+r\_{1})^{1}(1+r\_{2})^{n-1} + \dots + (1+r\_{1})^{n}(1+r\_{2})^{0}] \\
& = \delta\_{1} \sum\_{i=0}^{n} (1+r\_{1})^{i}(1+r\_{2})^{n-i} \\
& = \delta\_{1} (1+r\_{2})^{n} \sum\_{i=0}^{n} \left( \frac{1+r\_{1}}{1+r\_{2}} \right)^{i} \\
& = \dots \\
& = \begin{cases}
\delta\_{1} \frac{(1+r\_{2})^{n+1}-(1+r\_{1})^{n+1}}{r\_{2}-r\_{1}} & , & r\_{1} \neq r\_{2} \\
\delta\_{1} (1+r)^{n} (1+n) & , & r\_{1} = r\_{2} = r
\end{cases}
\end{align}
$$
the formula of $\beta\_{n+1}$
$$
\beta\_{n+1} = (1 + r\_{1})\beta\_{n} = \dots = (1 + r\_{1})^{n}\beta\_{1}
$$

# Phase 1: cover your spending with passive income

condition: the $n$-th year asset should generate enough passive income for expense of $n+1$ year:
$$
\begin{align}
\beta\_{n+1} & = x\_{n}r\_{2}
\end{align}
$$

expense coverage:

$$
\text{expense coverage} = \frac{x\_{n}r\_{2}}{\beta\_{n+1}}
$$

solve for $n$.

if $r\_{1} = r\_{2} = r$:
$$
\begin{align}
(1 + r)^{n} \beta\_{1} & = \delta\_{1} (1 + r)^{n-1} (1+n) r\\
1+n & = \frac{\beta\_{1}}{\delta\_{1}} \frac{r}{1+r} \\
n & = \frac{\beta\_{1}}{\delta\_{1}} \frac{r}{1+r} - 1
\end{align}
$$

if $r\_{1} \neq r\_{2}$:

$$
\begin{align}
(1+r\_{1})^{n}\beta\_{1} & = \delta\_{1} \frac{(1+r\_{2})^{n} - (1+r\_{1})^{n}}{r\_{2}-r\_{1}} r\_{2} \\
(1+r\_{1})^{n} & = \frac{\delta\_{1}r\_{2}}{(r\_{2}-r\_{1})\beta\_{1}} \left\[ (1+r\_{2})^{n} - (1+r\_{1})^{n} \right] \\
(1+r\_{1})^{n}\left( 1 + \frac{(r\_{2}-r\_{1})\beta\_{1}}{\delta\_{1}r\_{2}} \right) & = (1+r\_{2})^{n} \\
\left( 1 + \frac{(r\_{2}-r\_{1})\beta\_{1}}{\delta\_{1}r\_{2}} \right) & = \left( \frac{1+r\_{2}}{1+r\_{1}} \right)^{n} \\
n & = \frac{\ln\left( 1+\frac{(r\_{2}-r\_{1})\beta\_{1}}{\delta\_{1}r\_{2}} \right)}{\ln \left(  \frac{1+r\_{2}}{1+r\_{1}}  \right)}
\end{align}
$$

# Phase 2: a sustainable cover your income increase.

the investment return compared with the next year salary:
$$
\text{salary coverage} = \frac{x\_{n}r\_{2}}{\alpha\_{n+1}}
$$

when your investment return reach your salary, you retire.

# Visualization

Assuming that you graduated from the University as a PhD, and you are 30-year-old now, you just want to know how much save ratio you need to achieve financial independence and how many year would it takes.

According to [world bank](https://data.worldbank.org/indicator/NY.GDS.TOTL.ZS?locations=CN), China domestic savings is $43.4%$ of GDP at 2024, due to the public's current pessimistic opinion of to economy, let's set a goal $37%$ as a saving ratio goal.

Let's set your first year salary. This does not matter with your financial independency, but affect your balance after retiring. Assuming that you graduated from a good school and found a good job and earn $¥20,000$ per month, so your first year income is $¥240,000$. So you have a balance of $240000\*(1-0.37)/12 = 12600$.

Assuming that your salary goes up year by year, and since the CAGR of the salary of post-90s is now around $6.7%$, let set it conservatory as $5%$ for you, one of the Gen Z.

As for investment, I hope you won't invest garbage asset and invest those really valuable and realize a reasonable return rate -- 8%.

Finally, the simulation said that with saving + investment:

1. it would costs you around 17 years (at your 47's) to let the expense coverage reach 1 -- your assets build a firewall for your life.
2. it would costs you around 25 years (at your 55's)to let the salary coverage reach 1 -- know you can just retire!
3. your asset is 1.58x more than those earn from your boss
4. and you earn $¥1,000,000$ dollars.

![[living/philosophy/Attachments/Pasted image 20260329033153.png]]

This model assumes that your salary grow exponentially.

But since we're Gen Z, most people can't exponentially increase their salary these days. But surprisingly it also takes $\sim 17$ years to Phase 1 and $\sim 24$ years to Phase 2. But this only bring your asset to 4 millions rather than 16 millions.

![[living/philosophy/Attachments/Pasted image 20260329044058.png]]

But as a PhD you're about to reach 8 millions asset and $¥300,000$ budges per year.

![[living/philosophy/Attachments/Pasted image 20260329044841.png]]

[Interactive notebook to visualize your financial plan consequences on google colab](https://colab.research.google.com/drive/1Fz-JWZnYI1Fyi-_TES98sPQ_Q46OdNNI?usp=sharing)

# Terminology
*Random variable*
Maps the outcome of an unpredicable experiment to a value.

*Dsicrete Probability*
Random vraialbes have a finit or countably-infinite number of possible values. 

*Continous Probability*
Random variables have an uncountably-infinite number of possible values. 
## Expected Value, Variance, Standard Deviation

*Expected Value*
Average value after  repeating experient often enough.  -> mean value

For discrete random variable: 
$$
E[X] = \sum_{i=1}^n x_i p_i 
$$
$$ 
\displaylines{
X = Random variable \\
x_1, x_2 ... x_n = values \\
p_1, p_2 ... p_3 = propabilities \\
}
$$

*Variance*
Mean squared deviation from expected value. 

$$
Var[X] = E[(X-E[X])^2] = E[X^2] - E[X]^2
$$

*Standard Deviasion*

$$
SD[X] = \sqrt{Var[X]}SD[X] = \sqrt{Var[X]}
$$


---

**Example**
Fair die with only 3s and 4s.

*Excpected Value*
$$
E[X] = 3 \cdot 0.5 + 4 \cdot 0.5 = 3.5
$$
*Variance*
Die with only 3 and 4: 
$$
\begin{flalign}
E[X] = 3.5 \\
E[X^2] = 9 \cdot 0.5 + 16 \cdot 0.5 = 12.5 \\

Var[X] =  12.5 - 3.5^2 = 0.25
\end{flalign}
$$


Regular die: 
$$
\begin{align*}
E[X] =
1 \cdot \frac{1}{6} + 
2 \cdot \frac{1}{6} + 
3 \cdot \frac{1}{6} +
4 \cdot \frac{1}{6} +
5 \cdot \frac{1}{6} +
6 \cdot \frac{1}{6} \\
= 
\frac{1}{6} + 
\frac{2}{6} + 
\frac{3}{6} + 
\frac{4}{6} + 
\frac{5}{6} + 
\frac{6}{6} + 
= \frac{21}{6} = 3.5
\\ 
E[X^2] = 
\frac{1}{6} + 
\frac{4}{6} + 
\frac{9}{6} + 
\frac{16}{6} + 
\frac{25}{6} + 
\frac{36}{6} 
=  \frac{91}{6} 
= 15.17 \\
Var[X] = ...
\end{align*} 

 
$$

*SD*
$$
\sqrt{0.25} = 0.5
$$

## Central Limit Theorem
For any distributoin the sum of n events is almost nromally distributes for large n^5. 

## Law of Large Numbers
For every randomg veriable X the average of n experiemt converges to the exptected value E[X] as n tends to inifinity. 

## Independence
Two random variables are independent iff the outcome of one tells nothing about hte outcome of the other. 

# Tree Diagrams 

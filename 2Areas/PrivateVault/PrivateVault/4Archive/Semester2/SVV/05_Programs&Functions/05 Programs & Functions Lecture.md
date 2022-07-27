
[[SVV Sheet3 My Solutions]]

##### *Initial conditions* 
$x_0$ is the return value. 
$x_1...x_n$ are the parameters.

##### *Simple statements* 
$x_i := x_j$ sets the value of $x_i$ to the value of $x_j$. 
$x_i := x_j - x$ sets the value the value of $x_i$ to the value of $x_j-x$ or 0.
(+ is similar) 

##### *LOOP Programs* 
LOOP $x_i$ DO P END - Executes P exactly $x_i$ times. 

##### *While Programs* 
WHILE $x_i \ne 0$ DO P END - Executes P unitl $x_i$ becomes 0. 

# Primitive Recursive Functions
A primitive recursive function takes a fixed amount of arguments, each a natural number and return a natural number. 

If it takes n arguments it is called n-ary.

### Basic functions 

Zero function: $0(x) = 0$

Successor: $S(x) = x +1$
Returns successsor of its argument. 

Projection: $P^j_i(x_1,...,x_n) = x_i$
For all natural numbers i, j: Gives pack one of the input parameters

Composition
$$
h(x_1,...x_k) = f(g_1(x_1,...,x_k),...,g_m(x_1,...,x_k))
$$
### Primitive recursion 
$$
\begin{align*}
h(0,x_1,...,x_k) = f(x_y,...,x_k) \\
h(y+1,y_1,...,x_k) = g(y,h(y,x_1,...,x_k),x_1,...,x_k)
\end{align*}
$$

*Example*



Addition
2-ary 
$$
\begin{align*}
Baes Case\\
pl(0,x) = p^1_1(x) \\
pl(y+1,x) = s(p^2_3(y, pl(y,x),x)) 
\end{align*}
$$

$$
\begin{align*}
h(0,x) = p_1^1(x)
\\\\
pl(3+1,2) = s()
\\
\end{align*}
$$
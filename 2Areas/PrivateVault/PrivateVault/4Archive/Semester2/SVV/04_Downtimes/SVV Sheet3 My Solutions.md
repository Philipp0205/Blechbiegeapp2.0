[[4Archive/Semester2/SVV/sheet3.pdf]]

# 3.2
## 2 * a 

### LOOP
---
$x_0:=x_1+x_1$
$x_0:=x_1+2$


General syntax without syntax sugar 
$$
\begin{align*}
\text{LOOP } x_2 \text{ DO} \\
& \text{LOOP } x_1 \text{ DO} \\
&& x_0:=x_0+1 \\
&\text{END} \\
\text{END}
\end{align*}
$$
---
### Recursive function
*mult(0,y) = f(0)*
*mult(2,a) = pr(mult(2,y),2))*


## a * b
### Loop Program

x0 := 0
LOOP x1 DO 
	LOOP x2 DO 
		x0 := x0 +1
	END
END

### Primitive Recursive Function
*mult(0,b) = f(0) (zero-function)*
*mult(a+1,b) = add(mult(a,b),a))*

## a^2
### LOOP
General syntax
$$
\begin{align*}
& x_0 = x_0+1 \\
& \text{LOOP } x_2 \text{ DO} \\
&& x_0=x_0*x_1 \\
& END
\end{align*}
$$
Solution

$$
\begin{align*}
& x_0 = x_0+1 \\
& \text{LOOP } 2 \text{ DO} \\
&& x_0=x_0*a \\
& END
\end{align*}
$$
### Primitive Recursive Function
*mult(a,a)*
???


---
## 2^a
x0 (return value) 
x1 is a 
x2 is b 

x0 := x4 +1  (is just 1 in th beginning )

LOOP x2 DO 
	LOOP x0 DO 
		LOOP x1 DO 
			x4 := x4 +1 
		END
	END
	x0 := x4;
	x4 := x33
END; 

## a^b+c
LOOP x2 DO 
	LOOP x0 DO 
		LOOP x1 DO 
			x4 := x4 +1 
		END
	END
	x0 := x4;
	x4 := x33
END; 

LOOP x3 DO 
	x0 := x0 +1
END 
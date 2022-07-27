# Question 1 
## Definition Software Verification 
Does product meet the requirements of its intended users?

## Definition Software Validation 
Stepwise refinement, starts with requirements end with executable code/software.

## Code Review 
Analyses artifacts during the development process by multiple persons. 
Most common method: Peer review (in Scrum) 
Other methods: Formal review

## How does CR improve software quality 
Errors or sloppiness of the person who wrote that code can be fixed. 
Understanding of code spreads in the team -> better maintenance if one person leave the team. 

# Question 2 
## White Box Tests, Back Box Tests, Difference
Black box: Test has neither knowledge of nor access to the internals of the program. 

White box: The tester has good knowledge of the internals of the program. 

## Which artifacts are required to write software tests 
If possible all artifacts with defined input and output.

## Advantages of white/black box tests


## Coverage
Code coverage is used to assess whether the test cases are well-chosen and cover most of the code. 

## Types of coverage
Statement coverage: Fraction of statement executed during the tests. 
Loop coverage: Every loop was executed zero, one and many times.

# Question 3 
## Safety security
## Door lock potential safety requirement
## Door lock potential security requirement

# Question 4 
## Write loop program that computes
$2 \cdot a$

x0 = x33
Loop $x1$ DO 
 $x_0 := x_0 + 2$
END

## Primitive recursive function 
$3+a$

$$
\begin{align*}
 \text{Base Case} \\
 add(0,x) = 0+x = x = p_2^2(0,x) \\ 
 \\
 \text{Recursive case} \\
 add(y+1,x)=g(y, add(y,x), x)=s(add(y,x)) \\
 \\
 add(3,2) = s(add(2,2))  = s(s(add1,2)) = s(s(s(add(0,2)))) = s(s(s(2))) \\
 s(s(s(2))) = s(s(3)) = s(4) = 5\\
 \\
 \text{Solution} \\
 s(s(s(a)))


\end{align*}
$$

## Given Loop program
**x2 = x2+1** // x2 is initially 0 so here it gets 1
**LOOP x1 DO** // Outer loop executes inner loop x1 times with | e.g.x1=5
	**LOOP x2 Do** // inner loop gets looped one time 
		**x2=x2+1** // x2=2
	**END** 
**END**
**x0 = x2**

---

x1 = 1, x2 = 2
x1 = 2, x2 = 4
x1 = 3, x2 = 8
x1 = 4, x2 = 16

$2^x1$



# Question 5
## a
$E[X]=2$
$E[X^2]=5$
$Var[X]=1$
$SD=1$

## b
$E[X]=4$
$E[X^2]=19$
$Var[X]=3$
$SD=1.732$

## c
3,3,3,3,3,3
6,6,6,0,0,0
3,3,3,3,1,5

## d
1,4,4,4,4,7
2,2,2,2,8,8
1,1,1,7,7,7
6,6,6,6,0,0

2,2,2,6,6,6
1,1,1,5,5,5


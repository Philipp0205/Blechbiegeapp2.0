
# Functional Programming Summary 
[[CPLExams]]

## Tail Recursion 
- Tail recursion means that the recursive function call is the last computation necessary to complete the current call 
- No "open" operations left on the stack that ware waiting for recursive calls to return 
- Faster and more memory-efficient
- Usually achieved by using accumulator  argument and a wrapper function that hides accumulator from the user

- Sources 
	- https://www.youtube.com/watch?v=_JtPhF8MshA&t=616s


```scheme
; if factor 0 always return 0
(define go
  (lambda (base, 0)
	 0))

; if base is one return result 
(define go 
  (lambda (base, 1)
	base))

; recursive function 
(define go
  (lambda (base, factor)
	go(base, (- 1 factor))))
```
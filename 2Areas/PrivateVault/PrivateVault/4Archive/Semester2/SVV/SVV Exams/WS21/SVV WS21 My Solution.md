
# Question 3 
## Write a loop program that computes a * a 
x0 := x33 (undefined so 0)
LOOP x1 DO
	LOOP x1 DO
		x0 := x0 + 1
	END
END


## Write loop program that computes 7 ^ 2
x0 := 0
LOOP x1 DO 
	LOOP x2 DO 
		x0 := x0 + 1
	END
END

???

## Explain Loop Program
Example: 
x1=2, x2=3 -> x0 = 7

**x0 = x0 + 1;** // is 1 in the beginning
**x4 = x1 + 1;** // 3 in the beginning 
**LOOP x4 DO** // loop executed 3 times 
	**x0 = x0 + 1** // 2 -> 3 -> 4
**END**
**LOOP x2 DO** // loop executed 3 times 
	**x0 = x0 + 1** // 5 -> 6 -> 7 
**END**

The loop caluclates:
x1 + 2 + x2 




# Loop for a * b  
x0 := x33
LOOP x1 DO 
	LOOP x2 DO 
		x0 := x0 + 1
	END
END

# Loop for 2 * a 
x0 := x33
LOOP x1 DO 
	x0 := x0 + 2;
END 

**or like previous one**


# Loop a^b

x0 (return value) 
x1 is a 
x2 is b 

x0 := x4 +1  (is just 1 in the beginning )

LOOP x2 DO 
	LOOP x0 DO 
		LOOP x1 DO 
			x4 := x4 +1 
		END
	END
	x0 := x4;
	x4 := x33
END; 

# Loop a^b+c
add:

LOOP x3 DO 
	x0 := x0 +1
END 




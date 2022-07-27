# JUnit
[[!Java]] [[JUnit JavaFX]]
Tags: #unittests #junit #java #programming 
Source: https://www.udemy.com/course/automation-testing-using-junit/learn/lecture/2010132#notes

---
## @Test Annotation
@Test is applied over methods to mark them as test methods.
Its visibility can be made public, default and protected

Class
```java
package com.hubberspot.junit5;

public class OddEven {

	public boolean isNumberEven(int number) {
		return number % 2 == 0;
	}

}
```

Test of this class
```java
package io.educative.junit5;

import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.Test;

class OddEvenTest {

	@Test
	void givenEvenNumber_whenIsEvenIsCalled_thenTrueIsReturned() {
		OddEven oddEven = new OddEven();
		assertTrue(oddEven.isNumberEven(10));
	}
	
	@Test
	void givenOddNumber_whenIsEvenIsCalled_thenFalseIsReturned() {
		OddEven oddEven = new OddEven();
		assertFalse(oddEven.isNumberEven(11));
	}

}
```

## Assertion 
Assertion help validating the exptected output. 



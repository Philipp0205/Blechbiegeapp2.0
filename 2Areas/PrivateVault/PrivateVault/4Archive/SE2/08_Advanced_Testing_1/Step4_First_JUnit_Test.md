## Step 4: First JUnit Test 
Berfore the binary class file: 
![[2_tests_passing.png]]

Our Test cases: 
```java
import static org.junit.jupiter.api.Assertions.*;

import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.Test;

class EmployeeTest {

	@BeforeAll
	public static void info() {
		System.out.println("Employee Version" + Employee.version());
	}

	@Test
	void createEmployeeWithNegativeSallary() {
		assertThrows(RuntimeException.class, () -> new Employee(2000, -2000));
	}

	@Test
	void createEmployeeWithWrongYearOfHiring() {
		assertThrows(RuntimeException.class, () -> new Employee(1234, 1000));
	}

	@Test
	void createCorrectEmployee() {
		Employee employee = new Employee(1990, 1000);
		assertNotNull(employee);
	}

	@Test
	void checkBonusForLessThanThreeYears() {
		Employee employee = new Employee(1990, 1000);
		assertEquals(0, employee.bonus(1990));
	}

	@Test
	void checkBonusForMoreThanThreeYears() {
		Employee employee = new Employee(1994, 1000);
		assertEquals(50, employee.bonus(1994));
	}

	@Test
	void checkBonusForMoreThanFiveYears() {
		Employee employee = new Employee(1996, 1000);
		assertEquals(75, employee.bonus(1996));
	}

	@Test
	void checkBonusForMoreThanEightYears() {
		Employee employee = new Employee(1999, 1000);
		assertEquals(100, employee.bonus(1999));
	}

}
```

Results with the first class file:
![[3_test_passing.png]]

The test "createEmployeeWthNegativeSallary" now passes. That menas that this bug was fixed by the developer. 
The other tests are still failing so more work is needed. 




[[SE2 - SS 17 - Exams.pdf]]

## Exercise 1
[[10DesignPatternsSummary]]
### UML
![[SS17Pattern.png]]

### Code

```java
public interface Contract {
	public double getCharges();
	public double getBalance();
	public double setBalance();
}

public class CoreContract implements Contract {
	private int contractNumber;
	private double balance; 
	
	public CoreContract(int contractNumber, double balance) {
		this.contractNumber = contractNumber; 
		this. balance = balance; 
	}
	
	@Override
	// getter and setter from interface 
}

public class Option implements Contract {
	private Contract contract; 
	
	// Overrite getter and setter from Contract interface 
	// get charges 
	// get set balance 
}

public class Data extends Option {
	public Data(Contract contract) {
		super(contract);
	}
	
	// Override getCharges() 👍 
	
}
```

*Create contract*


```java
Conctract c = new DoubleTransfer(
	new Data(
		new Data(
			
			)
		)
	)
```

*Advantage*
Simple extension 

*Principles*
High coupling / low cohesion

*Role of deign patterns for software maintenance*
Predefined maintencance 
- At patterns canges may / should happen
- At other place no changes should happen


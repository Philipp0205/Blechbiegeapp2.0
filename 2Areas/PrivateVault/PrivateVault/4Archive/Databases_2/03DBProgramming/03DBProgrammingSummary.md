# DB Programming Summary
[[JDBC Programming Exercise]]

## Exam 
2016

```java
String user, password; 

String classNr; //attribute of relation Takes
int matNr, grade; //attributes of relation Takes
user = Reading.readString ("Type the db username: ");

/* We assume the existence of a class Reading 
providing class methods for reading various data
types, here a String.
*/
password = Reading.readString ("Type the password: ");
Connection conn = DriverManager.getConnection
("jdbc:oracle:oci8:" + user + "/" 
+ password); 
```


### Code Example from the lecture slides 
```java
import java.io.*;
import java.sql.*;
public class Student {
 ...
 public static void main (String[] args)
 	throws SQLException, IOException {
	 
 	try {Class.forName("oracle.jdbc.driver.OracleDriver");
		 /* forName returns the class or interface object
 		with the name specified by the parameter string.
 		This line here doesn’t do anything with it, but just
 		by referring to it, the class is loaded into the 
 		JVM => load the JDBC driver for Oracle */
 	}
 	catch (ClassNotFoundException e) {
 		System.out.println("Driver could not be loaded."); 
 	}
 	
	 String user, password; 
 	//username and password for database login
 	String classNr; //attribute of relation Takes
 	int matNr, grade; //attributes of relation Takes
 	user = Reading.readString ("Type the db username: ");
	 
 	/* We assume the existence of a class Reading 
 	providing class methods for reading various data
 	types, here a String.
 	*/
 	password = Reading.readString ("Type the password: ");
 	Connection conn = DriverManager.getConnection
 	("jdbc:oracle:oci8:" + user + "/" 
	 + password);

	 /* The class DiverManager handles all open 
 	connections. The function getConnection takes one
 	String argument of the form 
 	jdbc:oracle:<drivertype>:<dbaccount>/<password>.
 	The : are separators used in JDBC.
 	*/
	 
 	myMatNr = Reading.readInt ("Type the matrikel number: ");
 	//the matNr of the student whose classes we want
	 
 	String query = "select classNr, grade from Takes where matNr = " + myMatNr;
	 
 	Statement stmt = conn.createStatement();
	 
 	// create a statement in the connection conn
 	ResultSet result = stmt.executeQuery(query);
	 
 	/* execute the query for the created statement
 	and return the resulting set of tuples.
 	A result set is similar to a cursor in
 	embedded SQL or an iterator in SQLJ. */
 	while (result.next()) {
		
		/*next() is null when no objects
 		are left. Otherwise goes to the
 		next result object. */
 		classNr = result.getString(1); 
		
 		/*read position 1 in the current result tuple
 		and return it as a String */
 		grade = result.getInteger(2);
		
 		/*read position 2 in the current result tuple
 		and return it as an integer */
 		System.out.println (classNr + ": " + grade);
		
	 } //while conn.close(); //close the database connection } //main
	 
} //Student
	 
	 

```


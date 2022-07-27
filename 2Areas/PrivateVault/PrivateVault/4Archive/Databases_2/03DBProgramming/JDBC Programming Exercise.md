### JDBC Programming Exercise 

KeyboardInputJava
```java
import java.io.*;

public class KeyboardInput {
    /* @author Dorothee Koch
     * @version May 2009
     * Class methods for handling input from the keyboard.
     * Most of the ideas stem from Julie Zelenski, Stanford University.
     */

  static BufferedReader stdin =
      new BufferedReader( new InputStreamReader(System.in));

    /* The class method echo stems from Gordon Beaton, 
       posted at comp.lang.java.programmer
    Its purpose is to switch off the echoing of input characters. We can call it
    to prevent that a password that is typed in will be displayed.*/

    public static void echo(boolean on) {
        try {
            String[] cmd = {
                "/bin/sh",
                "-c",
                "/bin/stty " + (on ? "echo" : "-echo") + " < /dev/tty"
            };
            Process p = Runtime.getRuntime().exec(cmd);
            p.waitFor();
        }
        catch (IOException e) { }
        catch (InterruptedException e) { }
    }


    /* This reads the input from the keyboard an returns it as
       an integer type. */
    public static int readInt () {
        while (true) {
            try{
                String line = stdin.readLine();
                int value = Integer.parseInt(line);
                return value;
            } catch(java.lang.NumberFormatException e){
                ;
            } catch(IOException e){
                ;
            }
        }
    } // end readInt ()

    /* This reads the input from the keyboard an returns it as
       an integer type. One can provide a message that is displayed
    to tell the user what is expected.*/
    public static int readInt (String text) {
        System.out.print(text);
        while (true) {
            try{
                String line = stdin.readLine();
                int value = Integer.parseInt(line);
                return value;
            } catch(java.lang.NumberFormatException e){
                ;
            } catch(IOException e){
                ;
            }
        }
    } // end readInt (String text)


    public static double readDouble () {
        while (true) {
            try {
                String line = stdin.readLine();
                double value = Double.valueOf(line).doubleValue();
                return value;
            } catch (java.lang.NumberFormatException e){
                ;
            } catch (IOException e){
                ;
            }
        }
    } // end readDouble()

    public static char readChar () {
        while (true) {
            try {
                String line = stdin.readLine();
                char value = line.charAt(0);
                return value;
            } catch (IOException e){
                ;
            }
        }
    } // end readChar()

    public static String readString (){
        while(true) {
            try {
                return stdin.readLine();
            } catch (IOException e) {
                ;
            }
        }
    } // end readString()

    public static String readString (String text){
        System.out.print(text);
        while(true) {
            try {
                return stdin.readLine();
            } catch (IOException e) {
                ;
            }
        }
    } // end readString(String text)

}
```

JDBCTestExample
```java
import java.io.*;
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class JDBCTestExample {
	/*
	 * @author Dorothee Koch
	 * 
	 * @version April 2021 This class is to be used as an example in class.
	 * 
	 * Username: 
	 * dk1s_11kuph1mst
	 * 
	 * mysql -h 193.196.143.168 -u dk1s_11kuph1mst -p
	 * 
	 */

	/***************************************************
	 * L O A D D R I V E R
	 ***************************************************/
	public static void loadDriver() {
		// load the JDBC driver
		try {
			Class.forName("com.mysql.cj.jdbc.Driver");

			/*
			 * forName returns the class or interface object with the name specified by the
			 * parameter string. This line here doesn't do anything with it, but just by
			 * referring to it, the class is loaded into the JVM => load the JDBC driver for
			 * MySQL. Other example: oracle.jdbc.driver.OracleDriver
			 */

			System.out.println("Driver successfully loaded.");
		} catch (ClassNotFoundException e) {
			System.out.println("Driver could not be loaded.");
		}
	} // loadDriver

	/***************************************************
	 * G E T U S E R C O N N E C T I O N
	 ***************************************************/

	public static Connection getUserConnection() throws SQLException {
		// ask the user for name and password, create the DB connection

		String user, password;
		// username and password for database login
		user = KeyboardInput.readString("MySQL login: ");
		/*
		 * We assume the existence of a class KeyboardInput providing class methods for
		 * reading various data types, here a String.
		 */

		KeyboardInput.echo(false);
		password = KeyboardInput.readString("password: ");
		KeyboardInput.echo(true);
		System.out.println();

		Connection conn = DriverManager.getConnection("jdbc:mysql://193.196.143.168/koch_universitydb", user, password);
		/*
		 * The class DriverManager handles all open connections. The function
		 * getConnection takes one String argument of the form
		 * jdbc:<databasesystem>:<drivertype>:<username>/<password>. The : are
		 * separators used in JDBC.
		 */
		return conn;
	} // userLogin

	/***************************************************
	 * R E A D S T U D E N T G R A D E S
	 ***************************************************/
	public static void readStudentGrades(Connection conn, int myMatNr) throws SQLException, IOException {
		/*
		 * list the classes and the assigned grades of the student with myMatNr
		 */

		String classNr; // attribute of relation Takes
		int matNr, grade; // attributes of relation Takes

		String query = "select classNr, grade from Takes " + "where matNr = " + myMatNr;

		System.out.println("Query: " + query);

		Statement stmt = conn.createStatement();
		// create a statement in the connection conn

		ResultSet result = stmt.executeQuery(query);
		/*
		 * execute the query for the created statement and return the resulting set of
		 * tuples. A result set is similar to a cursor in embedded SQL or an iterator in
		 * SQLJ.
		 */

		System.out.println("classNr:  grade:");
		while (result.next()) {
			/*
			 * next() is null when no objects are left. Otherwise goes to the next result
			 * object.
			 */
			classNr = result.getString(1);
			
			/*
			 * read position 1 in the current result tuple and return it as a String
			 */
			grade = result.getInt(2);
			
			/*
			 * read position 2 in the current result tuple and return it as an integer
			 */
			System.out.println(classNr + ": " + grade);
		} // while

	} // readStudentGrades

	/***************************************************
	 * M A T N R E X I S T S
	 ***************************************************/

	public static boolean matNrExists(Connection conn, int testMatNr) throws SQLException {
		String query = "SELECT * FROM Student WHERE matNr = " + testMatNr;

		Statement stmt = conn.createStatement();
		// create a statement in the connection conn

		ResultSet result = stmt.executeQuery(query);
		/*
		 * execute the query for the created statement and return the resulting set of
		 * tuples.
		 */

		return result.next(); // true if the matNr existed, false otherwise

	}// matNrExists

	/***************************************************
	 * E N T E R N E W S T U D E N T
	 ***************************************************/

	public static void enterNewStudent(Connection conn, int newMatNr) throws SQLException {
		/*
		 * check that matNr does not exist, insert new student or ask fro new matNr
		 */

		/*
		 * Check first if this matNr does not exist already This would better be handled
		 * by an exception (for instance NonExistingMatNrException), which then should
		 * be caught and handled in main!
		 */

		while (matNrExists(conn, newMatNr)) {
			System.out.println("This matNr is already taken. " + "Please supply a different one!");
			newMatNr = KeyboardInput.readInt("Type the matNr: ");

		} // while

		/*
		 * Now we are sure a valid new matNr has been provided. Read now the name of the
		 * new student.
		 */

		String sName = KeyboardInput.readString("Type the name: ");
		/*
		 * It's not good style to tear apart the user dialogue between main and this
		 * method as I've done here. I'll change it later!
		 */

		// Now enter the new student into the table.

		String query = "INSERT INTO Student (matNr, sName) VALUES (" + newMatNr + ",'" + sName + "')";

		System.out.println("Query: " + query);

		Statement stmt = conn.createStatement();
		stmt.executeUpdate(query);

	} // enterNewStudent

	/***************************************************
	 * D E L E T E S T U D E N T
	 ***************************************************/

	public static void deleteStudent(Connection conn, int delMatNr) throws SQLException {
		/*
		 * delete student with matNr delMatNr from table Student
		 */

		String query = "DELETE FROM Student WHERE matNr = " + delMatNr;

		System.out.println("Query: " + query);

		Statement stmt = conn.createStatement();
		stmt.executeUpdate(query);

	} // deleteStudent

	/***************************************************
	 * GET MAT NUMBERS
	 ***************************************************/

	public static void showMatriculationNumbers(Connection conn) throws SQLException {
		String query = "SELECT matNr, sName " + "FROM Student ";

		System.out.println("Query: " + query);

		Statement stmt = conn.createStatement();

		ResultSet result = stmt.executeQuery(query);
		/*
		 * execute the query for the created statement and return the resulting set of
		 * tuples. A result set is similar to a cursor in embedded SQL or an iterator in
		 * SQLJ.
		 */

		List<String> martricelNumber = new ArrayList<>();

		System.out.println("classNr:  grade:");
		while (result.next()) {
			System.out.println(result.getString(1) + " | "  + result.getString(2));
		}
		
		System.out.println("---------------------");

	} // deleteStudent

	/***************************************************
	 * M A I N
	 ***************************************************/

	public static void main(String[] args) throws SQLException, IOException {

		loadDriver(); // load the JDBC driver
		Connection conn = getUserConnection();
		// ask user identification
		// and get DB connection for user

		boolean cont = true;

		while (cont) {// offer menue while user wants to continue
			System.out.println("Menue: Enter a letter for an action:");
			System.out.println("r for reading grades");
			System.out.println("n for inserting a new student");
			System.out.println("d for deleting a student");
			System.out.println("x for exiting the program.");
			System.out.println("m for showing the matricel numbers");

			char choice = KeyboardInput.readChar();

			switch (choice) {
			case 'r': {
				System.out.println("Get a list of grades of a student.");
				int myMatNr = KeyboardInput.readInt("Type the matNr: ");
				// the matNr of the student whose classes we want

				readStudentGrades(conn, myMatNr);
				// read matNr of a student, list the grades
				break;
			}
			case 'n': {
				System.out.println("You can now insert a new student.");
				int newMatNr = KeyboardInput.readInt("Type the matNr: ");
				enterNewStudent(conn, newMatNr);
				// enter a new Student with matNr and sName
				break;
			}
			case 'd': {
				System.out.println("You can now delete a student.");
				int delMatNr = KeyboardInput.readInt("Type the matNr: ");

				deleteStudent(conn, delMatNr);
				// delete a student chosen by matNr
				break;
			}
			case 'x': {
				cont = false; // user wants to stop
				break;
			}
			case 'm': {
				System.out.println("Show matricel numbers");
				showMatriculationNumbers(conn);
				break;
			}
			}// switch

		} // while
		conn.close();

	} // main
} // JDBCTestExample

```
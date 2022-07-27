
# System Platform 
For our Project we decided to use technologies we already worked in the past with. 
A programming language all group members where familiar with is Java. Therefore we chose Java in combination with JavaFX as UI Framework and SpringBoot as application Framework. 

## Installation 
The code can be found under the following URL: 
https://github.com/Philipp0205/rdbms

To run the source code eclipse with the SpringBoot Plugin is needed. Run the Main class as "SpringBoot Project". 
It is a maven project and therefore all dependencies configured in the pom.xml will be pulled automaticly. 

For the back-end mysql need to be installed and the tables need to be created. The corresponding SQL-Statements can be found ind chapter 4. 

| Software              | Version | Use                               |     |
| --------------------- | ------- | --------------------------------- | --- |
| SpringBoot Starter    | -       | Basic Spring Boot Project         |     |
| Spring Boot Framework | 2.4.5   | The Application Framework we used |     |
| JFoenix               | 8.0.10  | Material UI Libary                |     |
| MySql                 | 5.1.6   | Database                                  |     |

## Project Structure
Our project structure looks like this: 
![[DB_Project_Structure.png]]

We used the *Model-View-Controller Pattern* to structure the project. The views are written in the user interface markup language *FXML* (.fxml). All Model can be found in the *models* package and all the controllers can be found in the *controller package*. Every View has it's own models and controllers. 

All classes for the Backend are in the *db* package. Every model has a corresponding DAO class. The *DBDemo* and abstract *DAO* class handle the connection  to the db. 



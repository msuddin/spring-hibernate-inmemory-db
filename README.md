# sample-spring-hibernate

## Purpose

### Question:
What is the purpose of this project?

### Answer:
#### Main
* Main Application run's a Spring Application which picks up all rest controllers
* The HelloController (a RestController class) exposes two api's ('/hi/{id}' and '/all')
* The AccountService (a Service class) uses a JpaRepository to perform CRUD operations
* The AccountService class uses the Account class as an Entity class
* The Account (an Entity class) matches each of it's member variables to a table, table must be named the same as the class
* The AccountRepository (a Repository interface) extends the JpaRepository interface and provides default CRUD operations

#### Test
* Under main/resources, the application.properties allows h2 logging to console
* Under main/resources, the import.sql is automatically executed by hibernate
* Under src/test/java, two tests for service and controller
* The controller test uses TestRestTemplate to perform a get and assert on the content to the URL
* The Service test checks to see that the data is present after hibernate runs the import.sql under main/java/resource

## Instructions
From the root directory of the project, run the command below to run the tests and build the jar:
```
./gradlew clean build
```
Now let's run the jar:
```
ava -jar build/libs/<jar_name>.jar
```
The application should now start-up. Access all data be curling below:
```
curl http://localhost:8080/all
```
The curl above should give you the following output:
```
["Batman","Superman","Wonder Women"]
```
You can also try the following curl to get just one of the above:
```
curl http://localhost:8080/hi/1
```
Output should be:
```
Hi Batman
```
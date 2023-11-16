# Workflow Management

Welcome to the documentation for the upcoming APIs that will power our workflow management system. In this document, we'll explore the pseudocode for various APIs.

## Projects Screen

`Get All Projects`

Retrieves the list of all the projects without filtering.

| Method | Request                                | Response         |
| ------ | -------------------------------------- | ---------------- |
| GET    | Auth token, userId/orgId (if required) | List of projects |

1. Define a Lambda function handler that takes an event as a parameter.

2. Import the PostgreSQL Client module.

3. Create a new PostgreSQL Client instance database credentails.

4. Attempt connection to database. Log success or error for the connection

5. Parse request body data from the event object ( if there is a request body)

6. Using the pg client create a SQL query to retrieve all projects in a try-catch block.

7. On successfull quey, return the list of projects with a status code 200 and a success message.

8. If there's an error during the database query, log the error and return a response with a status code 500 and a JSON body including an error message.


`Get all projects with progress filter`

Retrieves the list of all the projects with progress filter. The filter is passed as a request param. The filter can be either `inProgress` or `completed`. 

| Method | Request                                | Response         |
| ------ | -------------------------------------- | ---------------- |
| GET    | Auth token, userId/orgId (if required), requestParam : comlpeted or inProgress | List of projects |

1. Define a Lambda function handler that takes an event as a parameter.

2. Import the PostgreSQL Client module.

3. Create a new PostgreSQL Client instance database credentails.

4. Attempt connection to database. Log success or error for the connection

5. Parse request body data from the event object ( if there is a request body)

6. Using the pg client create a SQL query using a WHERE clause thats filters projects based on whether they comleted or inProgres. Use try-catch block for query execution.

7. On successfull quey, return the list of projects that match the WHERE clause with a status code 200 and a success message.

8. If there's an error during the database query, log the error and return a response with a status code 500 and a JSON body including an error message.

`Add new project`

Creates a new project with the given project details like project name, project manager, project description, resources, project department, project duration ( start and end date) and budget (optional), . 

| Method | Request                                                                                                         | Response         |
| ------ | --------------------------------------------------------------------------------------------------------------- | ---------------- |
| POST   | projectName : string<br>project manager : string<br>project description : string<br>resources : list<names><br>project department : string<br>startDate : date<br>end date: date<br>budget : string (optional)  | List of projects |


1. Define a Lambda function handler that takes an event as a parameter.

2. Import the PostgreSQL Client module.

3. Create a new PostgreSQL Client instance database credentails.

4. Attempt connection to database. Log success or error for the connection

5. Parse request body data from the event object ( if there is a request body)

6. Using the pg client create a SQL query using a WHERE clause thats filters projects based on whether they comleted or inProgres. Use try-catch block for query execution.

7. On successfull quey, return the list of projects that match the WHERE clause with a status code 200 and a success message.

8. If there's an error during the database query, log the error and return a response with a status code 500 and a JSON body including an error message.

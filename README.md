# This repository has a REST API for Product and Analytics entities

This project presents an API Flask Implementation, as requirement for BackEnd Developer position at Osedea Corporation. All details as Business Requirements, Stack Technologies, Solutions Developed and API endpoint presentation and tests are showed below. Thanks for review !

## 📋 Business Requirements
A client wants to develop a dashboard to analyze the sales results of their ecommerce website.
Two kinds of users will be able to access to the dashboard: admins and managers. So the client need an API for Product and Statistics information as defined in the User Story below.

* 1 - **Entities details and Funcionability**
  * 1.1 - **Product : Atributes** id:int, name:string, description:string</br>
           * 1.1.1 - Create a new product
           * 1.1.2 - View the full list of products
           * 1.1.3 - Update product information
           * 1.1.4 - Delete a produc
           
  * 1.2 - **Analytics : Atributes** id:int, order_id:int, date:datetime, session_duration:int, nb_products:int, amount:float, new_visitor:string, device_type:string</br>
           * 1.2.1 - Total revenue in 2020</br>
           * 1.2.2 - The average revenue of orders made on a mobile device (smartphone or tablet)</br>
           * 1.2.3 - The average number of products per order</br>
           * 1.2.4 - One route that returns all the statistics
           
* 2 - **Rules**
  * 2.1 - The admins can access to all the statistics
  * 2.2 - The managers can't access to the revenue statistics

* 3 - **Future Need**
  * 3.1 - Create new user roles with different data access in the future
  * 3.2 - New metrics might be available in a next version of the CSV file

## ⚙️ Main Technologies
* 1 - **Flask** Endpoint and infraestruture
* 2 - **SQLAlchemy** Database acess and configuration
* 3 - **Blueprint** Integrate different endpoint file

## ⚙️ Architecture ( MVC Pattern )
To meet the functional requirements indicated by the customer, all services (endpoint) are available in a single app.py file. This approach does not represent the cohesion and coupling best practices described in Software Engineering. Therefore, some improvement points are described below and will be implemented in next release.
* 1 - **Entities**
    * 1.1 - Create different endpoint file for each entity (Product, Analytics and other)
* 2 - **Models**
    * 2.1 - Create a file for different Entities
* 3 - **Configurations**
    * 3.1 - Create a file for configurations
* 4 - **Utils module** 
    * 4.1 - Create a file for utils functions

## ⚙️ The Project Development
  **Developper Feedback**
  Despite working with systems development with a focus on backend for almost 20 years, developing this REST API using Python, Flask and SQLAlchemy was an extra challenge, as they are technologies with which I had no practical experience until the moment I started the implementation of the API.</br>

In the 4 days of deadline I had to research, learn and implement the entire project. Some tutorials on youtube gave me the minimum knowledge necessary to start coding and prepare my "Hello World", which gradually grew to meet the customer's needs.</br>

I recognize that the project has Software Engineering flaws and that it also need applying advanced concepts of the technologies used, but that's for a next release.</br>

**1 - How the problem was approached** Step by step, and the first point was to try to understand how technologies are used in their simplest forms. From this central idea, all the features were developed in the simplest way and without architectural concerns.</br>

**2 - Explain your reasoning behind any technical decisions you made** As an experienced developer, I know the importance of a good MVC development model, but the approach to project development was to focus on learning, coding and meeting the business requirements first, and then improving other technical aspects with the creation of modules of business and blueprint integration

**3 - Best practices or changes you would make if this were a real production app**
    * 1.1 - Token generation dynamically and valid for a few minutes
    * 1.2 - Not use email as user name
    * 1.3 - Create a Analytics.csv table for importing control, avoinding import the same file twice
    * 1.4 - Create Project Test using framework Rest-Assured for API Test
    * 1.5 - Create a hook from GitLab and Jenkins, SonarQube, Quality Gate for CD/CI Environment pipeline
    * 1.6 - Use the SGBD like MySQL, PortGres
    * 1.7 - Create different layer project 
      ** 1.7.1 - Controller (endpoint)
      ** 1.7.2 - Data Transfer Object DTO/VO
      ** 1.7.3 - Business Object BO
      ** 1.7.4 - DAO
    * 1.8 - Load Balance and Backup
    * 1.9 - Create a LOG funcionallity
    * 1.10 - Data importing functionality by assincronous methodology
     
**4 - Any learning resources used**
    * 4.1 - Youtube
    * 4.2 - Blogs and tutorials
    * 4.3 - Official documentation (Flask, SQLALchemy)

**5 - if some steps were not completed, the steps you would have taken in your approach to complete them**
    * 5.1 - Dockerization was not completed. Actions: Improve knowledge about Decker
    * 5.2 - User authentication was not completed until today (04/21). I'll try complete it in 04/22 

**6 - Any major issues encountered and the solutions found (or not)**
    * 6.1 - Date format in Analytics.py file was not valid for database. Was created a function to convert in valid date
    * 6.2 - New visitor in Analytic.py file is string while the Entity is Boolean. Was created a function that read the value as 'Yes' or 'No' and setting 0 or 1


## 🛠️ Tools Technical Requirements

* 1 - MySQL Database (SGBD Tool)
* 2 - Python version 3.9
* 3 - VS Code IDE
* 4 - Http request tool as Postman or similar  


## 🚀 Starting Database and Environment
Fellow the below step for run the project

## 🔧 Development Environment Setup - DATABASE
* 1 - Download in https://github.com/edfcbz/task-api-rest-spring-360agency-test **task-api-rest-360agency.rar** file and unzip it.

* 2 - Install and Run the MySQL Server (Default port)
* 3 - Install and Run the HeidiSQL
  * 3.1 - In HeidiSQL run **CreatingDatabase360agency.sql** and **InsertDataTestInTables.sql** files. These files are located in task-api-rest-360agency\src\main\resources\files folder. For it select: File -> Load SQL file -> Press SQL Execute (Blue Icon), this action will create the SCHEMA and insert basic data into tables. 
  * 3.2 - After prior step refresh environmet F5 key or press icon green (Refresh)
  * 3.3 - Verify if schema was created and tables has data 

## 🔧 Development Environment Setup - DEVELOPMENT

* 1 - Run Eclipse and Import the project as "Existing Maven Project" option
* 2 - In Eclipse menu select Project -> Clean
* 3 - Open package br.com.edfcbz and locate **Statup.java** file. Run it as Java Application. The TomCat server will run at 8080 port
  * 3.1 - Tips: If the Eclipse console show the message "Caused by: java.net.BindException: Address already in use: bind", finalize the service in 8080 port as showed
  * 3.2 - Run CMD as Administrator and type de command line: C:\>netstat -a -n -o | findstr :8080 (This command will show a line as:
          *TCP 0.0.0.0:8080 0.0.0.0:0 LISTENING 8457 (In this example 8457 is the PID process)
  * 3.3 - Run CMD command line as Administrator: C:\>taskKill.exe /F /PID 8457 ( This command will show a line as: 
          *SUCCESS: The process with PID 8457 was terminated. ( Or similar message )
  * 3.4 - Execute 3.1 step again

## ⚙️ Testing environment
* 1 - Requesting a token (Security Layer)
  * 1.1 - Run Postman
  * 1.2 - Select a POST request and type http://localhost:8080/auth/signin
  * 1.3 - In Body section type: {
                          "username":"leandro",
                          "password":"admin123"
                        }
  * 1.4 - Select SEND button (You will receive a message with a token as below)
  ![image](https://user-images.githubusercontent.com/63114961/163141178-e52010dc-74a7-44c4-9e02-ce4680aafaf5.png)

  * 1.5 - Copy the token returned without ""

* 2 - Requesting a TomCat service
  * 2.0 - Select a GET request and type http://localhost:8080
  * 2.1 - In Header section create or modify a  **Authorization** key with value: Bearer <paste here token received in step 1.3>. Tip: There is just one empty space between Bearer and token
  * 2.2 - Select SEND button. You will receive all a list with services available, as showed in image below. So, your enviroment is running...

![image](https://user-images.githubusercontent.com/63114961/163140854-fb7691cd-cd45-412b-8c78-c5fd09df6046.png)


## ⚙️ API RESTFul - Endpoints list and general informations
* 1 - **Dealer** endpoints
  * 1.1 - GET request for http://localhost:8080/dealer ( Show all Dealer registered in the Database )
  * 1.2 - GET request for http://localhost:8080/dealer/{dealerId} ( Show the Dealer details according **dealerId** informed and all Listing related )
  * 1.3 - GET request for http://localhost:8080/dealer/{dealerId}/{listingState} ( Show the Dealer by dealerId and Listing registered by listingState )
  * 1.4 - GET request for http://localhost:8080/dealer/name/{dealerName} ( Lists all dealers whose names match with the parameter, fully or not ) 
  * 1.5 - POST request for http://localhost:8080/dealer ( Save the Dealer informed in  Body section )
  * 1.6 - PUT request for http://localhost:8080/dealer ( Update the Dealer informed in  Body section using **dealerId** as key )
  * 1.7 - DELETE request for http://localhost:8080/dealer/{dealerId} ( Delete Dealers by identification match with the parameter ) 


* 2 - **Listing** endpoints 
  * 2.1 - GET request for http://localhost:8080/listing  ( Show all Listing registered in the Database )
  * 2.2 - GET request for http://localhost:8080/listing/{listingId} ( Show the Listing details according **listingId** informed and all Listing related )
  * 2.3 - GET request for http://localhost:8080/listing/description/{descriptionVehicle} ( Show all Listing whose **vehicle** atribute match with  **descriptionVehicle** parameter )
  * 2.4 - GET request for http://localhost:8080/listing/state/{stateListing} ( Show all Listing whose **state** atribute match with  **stateListing**  parameter)
  * 2.5 - GET request for http://localhost:8080/listing/dealerid/{dealerId} ( Show all Listing whose **dealerid** atribute match with  **dealerId**  parameter)
  * 2.6 - GET request for http://localhost:8080/listing/dealerid/{dealerId}/state/{stateListing} ( Show all Listing whose **dealerid** atribute match with  **dealerId** and  **state** atribute match with  **stateListing** parameter)
  * 2.7 - POST request for http://localhost:8080/listing ( Save the Dealer informed in  Body section )
  * 2.8 - POST request for http://localhost:8080/listing/overwriting ( Save the Listing informed in Body section removing the oldest registre if limit was reached )
  * 2.9 - PUT request for http://localhost:8080/listing ( Update the Listing informed in  Body section using **id** atribute as a key )
  * 2.10 - DELETE request for http://localhost:8080/listing/{listingId} ( Delete Listing using **listingId** as a key) 

## 🚀 Starting JUnit Test Class
## VERY IMPORTANT Before everything, execute section "Testing environment" Above. "THIS IS ESSENTIAL"

* 1 - **(Default OPTION)** Access the Database SCHEMA and remove all informations using the command SQL below:
  * 1.1 - Clean Listing table: DELETE FROM Listing;
  * 1.2 - Clean Dealer Table: DELETE FROM Dealer;
  * 1.3 - Execute the file InsertDataTestInTables.sql in Client SQL Tool (This step will create the data tests in Database squema)
  
* 2 - **(Another OPTION)** Creating new database
  * 2.1 - Remove the Database schema created before
  * 2.2 - Execute the SQL file "CreatingDatabase360agency.sql" in Client SQL Tool (This step will create the data tests in Database schema) 
  * 2.4 - Execute the SQL file "InsertDataTestInTables.sql" in Client SQL Tool (This step will create data in Schema Tables)
* 3 - Run the **Sturtup.java** class as java application. This file is located in br.com.edfcbz project package or repeat the "Testing environment" section 

## ⚙️ API RESTFul - Running Examples
* 1 - **Dealer** endpoints 
  * 1.1 - Resquet type GET http://localhost:8080/dealer/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd (This endpoint return Dealer details and all Listing related. See image below for details)

![image](https://user-images.githubusercontent.com/63114961/163675037-9894b3ef-c1b2-4d02-b137-061e75f36281.png)</br>

  * 1.2 - Resquet type GET http://localhost:8080/dealer/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd/**draft** or /**published** (This endpoint return a specific Dealer using dealerId and Listing by state. In this case **draft**  ( See images below )
  
![image](https://user-images.githubusercontent.com/63114961/163675139-e3352bbd-4548-4a1c-af42-08056d8d596d.png)

  * 1.3 - Resquet type GET http://localhost:8080/dealer/name/dealer 1 (Shows a list af all Dealer which has "dealer 1" inside name) ( See images below )

![image](https://user-images.githubusercontent.com/63114961/163675216-805ff0b2-f8dd-4b69-b49d-6e8e0e00649c.png)

  * 1.4 - Resquet type POST http://localhost:8080/dealer (Will add a new Dealer registry in Database, before add the personal information in body section as below ) 
  
![image](https://user-images.githubusercontent.com/63114961/163675433-e92248c5-58d7-49b7-a191-f7dc042e6c38.png)</br>
The API will return the Dealer created (See Image below for details)

![image](https://user-images.githubusercontent.com/63114961/163675480-5b04d518-40b0-442c-b018-571504967319.png)</br>
Verify the correct behavior sending a GET request findById as 1.1 Step Above, bus informing the id returned in 1.4 step above too. The result will be similar like below  image

![image](https://user-images.githubusercontent.com/63114961/163675613-482bce0d-e4d3-4a98-a627-7ec268bd0a2e.png)

  * 1.5 - Resquet type PUT http://localhost:8080/dealer  (Will update the Dealer information registred in Database, before add the personal information in body section as below )
  
  ![image](https://user-images.githubusercontent.com/63114961/163675694-d3e5ca50-515b-4210-8217-0498e5ba10cf.png)</br>
This operation will update the Dealer name and Limit os Listing state as published. The update return is showed in image below for details

![image](https://user-images.githubusercontent.com/63114961/163675765-e6be55ab-b47e-4eae-b971-b249e82646a6.png)</br>
The Dealer name and Limit Listing as published were modified

Request DELETE http://localhost:8080/dealer/{dealerId} (This endpoint will remove the Dealer if doesn't have Listing. If has, the operation will fail and API will return an Exception. See details below )</br>
![image](https://user-images.githubusercontent.com/63114961/163677242-9c2f9984-46d6-4680-9cb0-197692a74dda.png)


* 2 - **Listing** endpoints (Using data of initial setup and the new Dealer added above )
  * 2.1 - Request GET http://localhost:8080/listing/dealerid/ae8e9b8b-5a84-4140-84bd-f6e6ea1f57cd/state/published 
![image](https://user-images.githubusercontent.com/63114961/163650117-35bbb03f-195a-4c62-bb6b-2221722ff156.png)</br>
**BUSINESS REQUIREMENT** This endpoint implements the Business Requirement, searching and returning all Listing of a Dealer and state of them</br>

  * 2.2 - Request GET http://localhost:8080/listing (Will show all Listing from database - See image below for details about one of them. 2 Registry from 5)</br>
![image](https://user-images.githubusercontent.com/63114961/163676004-beab6f59-38c3-4b31-b556-a143e1d0bc34.png)</br>

  * 2.3 - Request POST  http://localhost:8080/listing (Will add a new Listing for Dealer created in Dealer 1.4 step above. The information about Listing must be in Body section of request as showed in image below )</br>
  ![image](https://user-images.githubusercontent.com/63114961/163676975-a6b8d65c-cac8-4e9a-8b7c-4c8df4a8e2a1.png)</br>

The result will be similar at image below. **As default the Listing state is draft** See the details</br>
![image](https://user-images.githubusercontent.com/63114961/163676993-a31f501c-c0cd-4b8d-99a7-2037cf1be140.png)</nr>

  * 2.4 - Request PUT http://localhost:8080/listing  (The endpoint will modify the Listing created in 2.3 step Above. The Listing data must be in body section as below)</br>
![image](https://user-images.githubusercontent.com/63114961/163677115-64002a05-fb8f-4814-9609-e97bbd65fc5f.png)</br>
The API will return the Listing updated. See image below for details</br>
![image](https://user-images.githubusercontent.com/63114961/163677143-2137e8f8-4755-4a65-8069-177232e23c76.png)

  * 2.5 - Request DELETE http://localhost:8080/listing/3bed1f91-38ec-48df-86a2-19dd1ac905ce (The API will return 200 as status code)</br>
   

## ⚙️ API RESTFul JUnit Test - Running Examples
As requirement, this project implemented JUnit test class for Dealer and Listing Service. Some tests are descrited below.

* 1 - **The Test Classes** 
  * 1.1 - The class **BaseClassAPITest.java** conect with data base using user named leandro and password admin123. After that, receive a token to add in all request. Is not necessary running this class. It will run automatically on each test  
  * 1.2 - The class **DealerEndpointDifferentMethodologiesTest.java** tests the Dealer endpoint using different test methologies.
  * 1.3 - The class **DealerEndpointTest.java** define the RestAssured given(), When() and Then() methologies
  * 1.4 - The class **ListingEndpointTest.java** test different business aspect 
  
* 2 - **Test Classes Path**
  * 2.1 - Path classes in src/test/java/br/com/edfcbz/endpoint/dealer package (Run file as JUnit test)
  * 2.2 - Path classes in src/test/java/br/com/edfcbz/endpoint/listing package (Run file as JUnit test)

* 3 - **Suite Test**
  * 3.1 -  The **Suite360AgenceTest.java** class will run all test classes from project. For this, go to path src/test/java/br/com/edfcbz/endpoint/dealer package (Run file as JUnit test). The final result looks like the image below.</br>

![image](https://user-images.githubusercontent.com/63114961/163678283-3890d531-1806-4237-86b1-74324688879f.png)

## 📋 API Development - Review Technical Aspect and Improvement Suggestions
* **1 ListingServiceBO.java**
   * 1.1 - Method **public Listing update(Listing listing_)**
           *This method need some improvements in logical and structural aspect. Improvements in Dealer's Listing limit test (published)
   * 1.2 - Method **public Listing published(String listingId)**
           *With similar aspect with update methody, it's possible improve the Limit Listing test, creating a new method for test it.
   * 1.3 - Method **public void findDealerByDealerIdAndVerifyNameAndLimitListing()**

* **2 - DealerServiceBO.java**
   * 2.1 - Method **public Dealer update(Dealer _dealer)**
           *This method need improvements during Limit updating. This service not verify the Listing state as published yet ( Known bug )

* **3 - Exception Classes**
   * 3.1 - Generalize and reduce the number of exception classes. It will be important to adopt a handle class that will be responsible for returning the appropriate exception class for each case.

## 📋 LOG - Review Technical Aspect and Improvement Suggestions
   * 1.1 - Increase details, adding logged user in the message
   * 1.2 - Currently shown log message on console. Add save-to-file behavior

## 📋 JUnit Test - Review Technical Aspect and Improvement Suggestions

**(Functional Test)** Status: Developed
* **1 - ListingEndpointTest.java 
   * 1.1 - Class **DealerEndpointTest.java**
   * 1.2 - Class **ListingEndpointTest,java**
In general, deepen the level of tests especially when the return has complex object with objects and list. Example: the draft or published Listing of a specific dealer

**(Coverage Test)** Status: Technical debt (Not developed)
**(Unit Test)** Status: Technical debt (Not developed)

## 📋 DevOps - Review Technical Aspect and Improvement Suggestions
Is essential implement the DevOps concept as below:
* 1 - Continuous Development and Continuous Delivery environment CD/CI using tools such as pipeline Jenkins
* 2 - Quality Gate and Sonar To define the developed code acceptance criteria
* 3 - Dockerized environment, for Development and Homologation

## 📋 Technical Debt
As a requirement, the use of the UUID data type was requested as an identifier for the Dealer and Listing entities, however the project used the String type and the **org.hibernate.id.UUIDGenerato** strategy to generate the primary keys.

## ⚙️ Documentation Swagger
Open browser and type: http://localhost:/swagger-ui.html (This url will open a page with and example for API use.

## 🛠️ Building tools

* Eclipse
* Maven

## 📌 Version

* Tags in **https://github.com/edfcbz/task-api-rest-spring-360agency-test**

## ✒️ Author

* **Developer contact** - edfcbz@gmail.com

## 📄 License

 **NA**

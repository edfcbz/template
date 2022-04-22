# This repository has a REST API for Product and Analytics entities

This project presents an API Flask Implementation, as requirement for BackEnd Developer position at Osedea Corporation.</br> 
All details as Business Requirements, Stack Technologies, Solutions Developed and API endpoint presentation and demontration are below. Thanks for review !</br>

## 📋 Business Requirements </br>
A client wants to develop a dashboard to analyze the sales results of their ecommerce website.</br>
Two kinds of users will be able to access to the dashboard: admins and managers. </br>
So the client need an API for Product and Statistics information as defined in the User Story below.</br>

* 1 - **Entities details and Functionalities**</br>
  * 1.1 - **Product : Atributes** id:int, name:string, description:string</br>
           * 1.1.1 - Create a new product</br>
           * 1.1.2 - View the full list of products</br>
           * 1.1.3 - Update product information</br>
           * 1.1.4 - Delete a produc</br>
           
  * 1.2 - **Analytics : Atributes** id:int, order_id:int, date:datetime, session_duration:int, nb_products:int, amount:float, new_visitor:string, device_type:string</br>
           * 1.2.1 - Total revenue in 2020</br>
           * 1.2.2 - The average revenue of orders made on a mobile device (smartphone or tablet)</br>
           * 1.2.3 - The average number of products per order</br>
           * 1.2.4 - One route that returns all the statistics</br>
           
* 2 - **Rules**</br>
  * 2.1 - The admins can access to all the statistics</br>
  * 2.2 - The managers can't access to the revenue statistics</br>

* 3 - **Future Need**</br>
  * 3.1 - Create new user roles with different data access in the future</br>
  * 3.2 - New metrics might be available in a next version of the CSV file</br>

## ⚙️ Main Technologies</br>
* 1 - **Flask** Endpoint and infraestruture</br>
* 2 - **SQLAlchemy** Database acess and configuration</br>
* 3 - **Blueprint** Integrate different endpoint file</br>

## ⚙️ Architecture Improvement ( MVC Pattern )</br>
To meet the functional requirements indicated by the customer, all services (endpoint) are available in a single app.py file.</br> 
This approach does not represent the cohesion and coupling best practices described in Software Engineering.</br> 
Therefore, some improvement points are described below and will be implemented in next release.</br>
* 1 - **Entities**</br>
    * 1.1 - Create different endpoint file for each entity (Product, Analytics and other)</br>
* 2 - **Models**</br>
    * 2.1 - Create a file for different Entities</br>
* 3 - **Configurations**</br>
    * 3.1 - Create a file for configurations</br>
* 4 - **Utils module** </br>
    * 4.1 - Create a file for utils functions</br>

## ⚙️ The Project Development</br>
  **Developper Feedback**</br>
  Despite working with systems development with a focus on backend for almost 20 years, developing this REST API using Python, 
  Flask and SQLAlchemy was an extra challenge, because I no had practical experience until the moment, and in 4 days I had to research, learn, implement and document the developed solution. Some tutorials on youtube, gave me the minimum knowledge necessary to start coding and prepare my "Hello World", which gradually grew to meet the customer's needs. I recognize that the project has technical debt and Software Engineering gaps, but that's for a next release.</br>
  
**Schedule**
04/19 day: Technologies review and "Hello World" 
04/20 day: Product endpoint and Analytics import endpoint (Solved issues from .csv file as date, boolean values etc)
04/21 day: Finishing import and build Analytics endpoint and tests
04/22 day: Occasional adjustments, general review and documentation
  
**1 - How the problem was approached** Step by step, and the first point was to try to understand how technologies are</br> 
used in their simplest forms. From this central idea, all the features were developed in the simplest way and without architectural concerns.</br>

**2 - Explain your reasoning behind any technical decisions you made** As an experienced developer, I know the importance</br> 
of a good MVC development model, but the approach to project development was to focus on learning, coding and meeting the business</br> 
requirements first, and then improving other technical aspects with the creation of modules of business and blueprint integration</br>

**3 - Best practices or changes you would make if this were a real production app**</br>
    * 3.1 - JWT - Json Web Token especification JWS + JWE </br>
    * 3.2 - Not use email as user name</br>
    * 3.3 - Create a Analytics.csv table for importing control, avoinding import the same file twice</br>
    * 3.4 - Create Project Test using framework Rest-Assured for API Test</br>
    * 3.5 - Create a hook from GitLab and Jenkins, SonarQube, Quality Gate for CD/CI Environment pipeline</br>
    * 3.6 - Use the SGBD like MySQL, PortGres</br>
    * 3.7 - Create different layer project</br> 
      ** 3.7.1 - Controller (endpoint)</br>
      ** 3.7.2 - Data Transfer Object DTO/VO/BO</br>
      ** 3.7.3 - Business BO Micro services Layer</br>
      ** 3.7.4 - DAO</br>
    * 3.8 - Load Balance and Backup</br>
    * 3.9 - Create a LOG funcionallity</br>
    * 3.10 - Data importing functionality by asynchronous function methodology</br>
    * 3.11 - Create Exception class for entity and endpoint
    * 3.12 - Adopt the UUID type as Entity.id (Increase the security in Http GET request, avoinding robot actions)
    * 3.13 - In Http DELETE, avoid id as parameter in URL
    * 3.14 - Refactory Importing function creating an object from analytics.csv file and apply the concepts as: analytics.id[i], analytics.date[i] etc.
      
**4 - Any learning resources used**</br>
    * 4.1 - Youtube</br>
    * 4.2 - Blogs and tutorials</br>
    * 4.3 - Official documentation (Flask, SQLALchemy)</br>

**5 - if some steps were not completed, the steps you would have taken in your approach to complete them**</br>
    * 5.1 - Dockerization was not completed. Actions: Improve knowledge about Decker</br>
    * 5.2 - User authentication and acess permition was not completed until today (04/21). I'll try complete util PM last minute in 04/22 </br>

**6 - Any major issues encountered and the solutions found (or not)**</br>
    * 6.1 - Date format in Analytics.py file was not valid for database. Was created a function to convert in valid date</br>
    * 6.2 - New visitor in Analytic.py file is string while the Entity is Boolean. Was created a function that read the value as 'Yes' or 'No' and setting 0 or 1</br>
    * 6.3 - Amount field has commas "," as separator. This was the easiest to solve using replace method</br>

## 🛠️ Tools Technical Requirements</br>

* 1 - MySQL Database (SGBD Tool)</br>
* 2 - Python version 3.9</br>
* 3 - VS Code IDE</br>
* 4 - Http request tool as Postman or similar</br>  

## ⚙️ Business Requirements X API Endpoint</br>
* 1 - **Product</br>
    * 1.1 - Create a new product **Http POST http://localhost:5000/product**</br>
            In body section type: {"name":"name product", "description":"Product description"}</br>
    * 1.2 - View the full list of products **Http GET http://localhost:5000/product**</br>
    * 1.3 - Update product information **Http PUT http://localhost:5000/product**</br>
            In body section type: { "id": 1, </br>
                                    "name":"new name product", </br>
                                    "description":"new Product description"</br>
                                  }</br>
    * 1.4 - Delete a produc **Http DELETE http://localhost:5000/product**</br>
            In body section type: { "id": 1}</br>     
            
* 2 - **Analytics</br>
    * 2.1 - Total revenue in 2020 and other years **Http GET http://localhost:5000/analytics/2020** or type 2019, 2021 etc</br>
    * 2.2 - The average revenue of orders made on a mobile device (smartphone or tablet) **Http GET http://localhost:5000/analytics/average/<device_type>**</br>
    * 2.3 - The average number of products per order **Http GET http://localhost:5000/analytics/average_product_order**</br>
    * 2.4 - One route that returns all the statistics  **Http GET http://localhost:5000/analytics**</br>

* 3 - **Import</br>
    * 3.1 - Endpoint to importing Analytics data to database **Http GET http://localhost:5000/import**</br>

## 🚀 Starting Application and Environment
* 1 - Install MySQL Server in default port. After that create a new database named osedea setting user as root and password as admin123
* 2 - Install Python 3.9.4 
* 3 - Download the source code from repository. Locate the app.py file and execute de command line in the same folder by CMD. >**python app.py**

**WARNING VERY IMPORTANT**
Before you run the application, be sure to choose a port that is not being used by other applications. Follow the steps below:

**TIP 1** - Run CMD as Administrator and type de command line: netstat -a -n -o | findstr :**5000**  (5000 is default Flask port) 
      (This command will show a line as: *TCP 0.0.0.0:8080 0.0.0.0:0 LISTENING 8457 (In this example, the port is been used by PID 8457 process). 
      Choose another port and try again. Finding a free port, setting app.run(...) command line at the end of **app.py** file. 
      In the project was selected the 5000 port. See the command line **app.run(port=5000, host='0.0.0.0', debug=True, threaded=True)**
      
**TIP 2** - To finish the PID process in specific port, run CMD command line as Administrator: taskKill.exe /F /PID 8457 ( This command will show a line as: *SUCCESS: The process with PID 8457 was terminated. ( Or similar message ).

## 📌 Version
V1.0

## ✒️ Author

* **Developer contact** - edfcbz@gmail.com

## 📄 License

 **NA**

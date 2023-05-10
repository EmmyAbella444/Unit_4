

# Unit 4: The CasHub - Create, Interact and Showcase Your Clubs and Activities!
![CasHub (2)](https://user-images.githubusercontent.com/111819437/230899973-d353750e-ac64-4d2c-80a1-a1263a509b46.png)


Fig1.Logo for the website made in Canva[^1]


# Table of contents
## Criteria A: Planning
## Criteria B: Design
## Criteria C: Development
## Criteria D: Functionality
## Criteria E: Evaluation

# Criteria A: Planning

In the international baccalaureate program, students must create a CAS portfolio to show their participation in extracurricular activities. Unfortunately, the students from a local school are having difficulty with their portfolios. Many of them lack proper documentation and forget to update their portfolios every week, because the current portfolio makes it hard for teachers to keep track of their progress since they have to open multiple links to check each student, since the users are not logged in the same website, which is time-consuming for teachers. The CAS portfolio is also used to assess a student's development of skills like collaboration and communication. However, the current portfolio does not facilitate this since it does not allow students to view each other's profiles, collaborate or interact with them. Additionally, the current portfolio does not have the option to download the activities in pdf format, which is an IB requirement, making it difficult for students to demonstrate their involvement which can result in them potentially receiving a lower grade and this can negatively impact their IB score and future university applications.

## Proposed Solution
To address this problem, I first ran interviews[^2] with the client and based on that I decided to create a website, called CasHub. It will work like a social network because it allows students to post their activities and interact with each other. With the client's approval[^2], I decided to use Python Flask, CSS, and HTML because it allows the creation of a dynamic and interactive website, which is essential for a social network-style platform. In CasHub students and teachers will be able to create profiles and log in, make posts about their activities, check a statistics page to track students' progress, visit each other's profiles, interact with other student's and teacher's posts, and have a personal profile page with options to delete posts, download activities as PDFs and have a message displayed if the user forgets to post regularly. All this information will be stored in SQLite databases because they are supported by Python Flask.

## Rationale
The choice of Python Flask, HTML, CSS, and SQLite for building CasHub is based on their suitability for creating a dynamic and interactive social network-style website that meets the needs of the school's students and teachers.

### Why a website?
The network-style website[^3] was chosen because it can run on browsers that all users will be able to access from any computer, differently from the application for example. It also allows post and get requests that make the users able to log in, and posts their activities.

### Why Python?
 Python[^8] has excellent support for handling data, making it an excellent choice for web applications that require data manipulation. This feature is particularly important in a social network-style platform like CasHub, where data handling is critical.

### Why Python flask?
Python Flask[^4]  is a Python web framework that provides tools to create website. Flask was chosen because its simplicity and flexibility make it ideal for building web applications that require frequent updates and modifications, such as a social network like CasHub. Additionally, Flask offers built-in support for SQLite, which is the database management that CasHub will use to store user data on CasHub and also it allows for easy integration with the front-end technologies that will be used: HTML and CSS.

### Why HTML and CSS?
HTML and CSS[^5] were chosen because HTML is used for structuring the content of web pages, while CSS is used for styling the content, making it visually appealing and easy to navigate creating a user-friendly and intuitive interface that is essential for the success of any social network.

### Why SQLite?
SQLite[^6] was chosen as the database management system for CasHub because it offers robust and safe data consistency, differently from CSV.files[^7] for example, ensuring that the information submitted by students is consistent, reliable, and easily accessible, which is essential for a perfect Cas Portifolio.

## Design Statement
I will design and make a Website for a client who are students and teachers at a local school. The website will be a social network to post, monitor, interact, and download CAS activities and is constructed using the software CSS, HTML, and PYTHON. It will take 4 weeks to make and will be evaluated according to the following success criteria.

## Success Criteria
| Success Criteria                                                                                                                 | "Issues Tackled"                                                                          |
|----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| 1. The website should have a user registration and login system with encryption of the password.                                 | "the users are not logged in the same website"                                              |
| 2. The website should allow users to post their activities and ensure that all posts are properly documented. | "lack proper documentation"                                                               |
| 3. The website should allow users to download the portfolio in pdf format.                                                                     | "The current portfolio does not have the option to download the activities in pdf format" |
| 4. The website should provide reminders for users to post about their activities.                                                | "Forget to update their portfolios every week"                                            |
| 5. The website should allow users to like and comment on other users posts.                                                      | "Does not allow students to collaborate or interact"                            |
| 6. The website should have a page with statistics of every student showing the last time that students posted.                   | "they have to open multiple links to check each student, which is time-consuming."             |
| 7. The website should allow users to visit each others profile.                                                                  | "does not allow students to view each other's profiles"                                   |


# Criteria B: Design
## System Diagram
![Habit Tracker (3)](https://user-images.githubusercontent.com/111819437/236936740-f0cd75c5-697b-471b-b19a-4d071192a0e4.png)


Fig.2 [^1] Shows the System Diagram for the project.

The System Diagram represents the different parts of the website and how they relate to eachother. The website uses Python to create the my.app file that interacts with the templates in HTML, as well as the Flask Library and other external libraries and My_Library to create the Python flask server. The arrows in the diagram indicate the data that is stored in the Social_net.db database, which utilizes the SQLite database engine.


## Wireframe
![name](https://user-images.githubusercontent.com/111819437/236926641-5bb8fcf1-dc2a-4a7a-a55c-a8e0f7744ea0.png)

fig.3 [^1] Shows the wirefram diagram for CasHub social network.

This wirefram shows all the screens in the social netwrok(login, register, main page, statistics, personal profile and users profile).The arrows extending from the buttons to the screens indicate to the user which screen will be opened when they click and release the button.

## UML Diagram
![uml (3)](https://user-images.githubusercontent.com/111819437/236927524-8618af73-6f97-4098-b783-a046514fb2a4.png)

Fig.4 [^9]This UML shows the class database_worker.

This class is used to control the database interaction. It has 4 methods and 2 private instance variables. The __init__() method initializes the connection and cursor variables using the sqlite3 module. The search() method takes a SQL query as input and returns a list of tuples as a result. The get() method also takes a SQL query as input and returns only the first result as a tuple. The run_save() method executes the given SQL query and commits the changes and  the close() method closes the database connection.


## ER Diagram
![ER diagram](https://user-images.githubusercontent.com/111819437/236806597-c08f7319-9175-477a-b616-22c6f70955d0.png)

Fig.5[^9] Shows the ER Diagram for the database used in the social network. 

The databse named:"Social_net.db" is organized with 4 tables: "Comments", "users", "likes" and "posts". This diagram shows that one user can have multiple posts which can have multiple likes and comments.

### Databases

![Screen Shot 2023-05-09 at 5 37 48](https://user-images.githubusercontent.com/111819437/236929668-3c6be295-f795-45cf-bbf0-3db331da148f.png)

Fig. 6 Shows the "Comments" table

The "comments" table has columns for the comment's id(primary key), the content, the user_id of the user who created the comment, and the post_id of the post that the comment belongs to. Both the user_id and post_id columns are foreign keys that reference the id columns of the "users" and "posts" tables, respectively.

![Screen Shot 2023-05-09 at 5 38 30](https://user-images.githubusercontent.com/111819437/236929772-c33b941a-f79c-48ad-b6b6-c76055b75369.png)

Fig. 7 Shows the "Likes" table

The "likes" table has columns for the like's id(Primary key), the post_id of the post that the like belongs to, and the user_id of the user who created the like. Both the post_id and user_id columns are foreign keys that reference the id columns of the "posts" and "users" tables, respectively. 

![Screen Shot 2023-05-09 at 5 39 05](https://user-images.githubusercontent.com/111819437/236929887-c838ce2b-48fd-4187-8191-a898d5992be7.png)
Fig.8 Shows the "posts" table

The "posts" table has columns for the post's id(primary key), title, content, the club that the post belongs to, the datetime the post was created, the user_id of the user who created the post, the number of likes the post has, the number of comments the post has and the picture attached to the post. The user_id column in this table is a foreign key that references the id column of the "users" table.

![Screen Shot 2023-05-09 at 5 40 08](https://user-images.githubusercontent.com/111819437/236930128-2ad0a0f5-a38c-42b6-9278-30bf8f16fa01.png)
fig.9 Shows the database for the "users" table

The "users" table has columns for the user's id(primary key) , email, password , username, description, clubs , and the number of posts made by the user. The "posts" table has columns for the post's id (primary key), title , content , the club that the post belongs to, the datetime, the user_id of the user who created the post, the number of likes , the number of comments and the picture attached to the post. The user_id column in this table is a foreign key that references the id column of the "users" table.


## Flow Diagrans

![add_comment](https://github.com/EmmyAbella444/Unit_4/assets/111819437/eff45064-5334-44d5-87db-e368b09be0b0)
Fig 10.[^9] Show the flodiagram for the add comments function.

This function first checks if the user is logged in by checking if their user ID exists in the request cookies. If the user is logged in, it retrieves the user ID and the comment content from the request form. Then, it connects to the database and inserts the comment into the comments table using an SQL query. It also updates the post's comment count in the posts table using another SQL query and closes the database. Finally, it redirects the user to the home page. If the user is not logged in, it redirects them to the login page.

![home ](https://github.com/EmmyAbella444/Unit_4/assets/111819437/2828cf89-2b33-43cc-8abb-00812834b149)
Fig 11.[^9] Show the flodiagram for home page function.

This function is responsible for rendering the home page, fist it checks if the user is logged in, and if so, it initiates the database to  retrieve posts and comments for each post and passes them to the HTML template.If there is a "POST" request it checkes if all data is valid and save this new post in the database,  If the user is not logged in, it redirects them to the login page.

![save_pdf](https://github.com/EmmyAbella444/Unit_4/assets/111819437/5221dc1e-6c39-4d8c-8d13-86b85974b726)
Fig 12.[^9] Shows the flodiagram for the save_pdf function.

This function creates a PDF file of all posts made by the user whose ID is stored in a cookie. It connects to the database, retrieves the user's posts, and with a for loop adds them to the PDF document and set the font size. The PDF document is saved and then sent to the user as a download using a Flask response object.

## Record of Tasks
| Task No 	| Planned Action          	| Planned Outcome                           	| Time estimate 	| Target completion date 	| Criterion 	|
|---------	|-------------------------	|-------------------------------------------	|---------------	|------------------------	|-----------	|
| 1       	| Planning: Meeting with the client     	| Understand the problem that the cliente is facing      	| 30 minutes    	| April 4                	| A         	|
| 2       	| Planning: Brainstorm of ideas     	| Have the first ideas for the project      	| 30 minutes    	| April 4                	| A         	|
| 3       	| Planning: Make a folder in code pen	| Have ideas for the wireframe of the project	| 30 minutes    	| April 7                	| A         	|
| 4       	| Planning: Write the problem difinition	| To have a clear ideia of the target problem to develop a solution| 30 minutes    	| April 8                	| A         	|
| 5       	| Planning: Select final idea	|Choose the best idea for the project | 30 minutes    	| April 8                	| A         	|
| 6       	| Planning: Write the proposed solution |To have a better idea on how the website is going to solve the problem| 30 minutes    	| April 8                	| A         	|
| 7       	| Planning: Write the rationale for proposed solution     	| Have clear justification on why and how the website will be developed    	| 30 minutes    	| April 8                	| A        | 
| 8       	| Planning: Write the design statement	|Have a clear plan in mind before start to code the website | 30 minutes    	| April 8                	| A         	|
| 9       	| Planning: Define the success criterias	| Have a clear outline of what is needed to be acheived and to have a clear idea about what are the features in the website	| 30 minutes    	| April 8    	| A         	|
| 10       	| Planning: Meeting with client	| Present to the client the criteria A and get final approval | 30 minutes    	| April 9  | A         	|             
| 11       	| Design: Design the system diagram	|To have a clear idea of the hardware and software requirements for the proposed solution | 1 hour    	| April 9                	| B         	|
| 12       	|Design: ER diagram	| Have an idea of the the data entities, attributes, and relationships between them	| 30 minutes    	| April 9                	| B         	|
| 13       	| Design: Wireframe| Have a clear view of how the website is going to look like	| 2 hours   	| April 8                	| B         	|
| 14       	| Design:  Create logo| have a logo that shows what the program is about| 1 hour  	| April 10                	| B         	|
| 15       	| Develop: Create the databases and tables following the ER diagram| to store the data for the program in an organized and efficient way	| 30 minutes    	| April 10                	| C         	|
| 16       	| Develop: Backgound desigh for signup page	| Make designs on canva to make the social network more appelealing| 1 hour    	| April 10               	| C         	|
| 17       	| Develop: Routes for sign up, register, mainpage, personal profile, users profile and statistics| Have the pages of the social network	| 30 minutes   	| April  11               	| C         	|
| 18       	| Develop: Build the base HTML and CSS design| Make the base template for pages to make it visualy pretty and user friendly| 3 hours  	| April 12                	| C  
| 19       	| Develop: Registration| Make the user able to register their personal data and create an account in the website| 2 hours  	| April 12                	| C         	|
| 20       	| Develop: login page| Make the user able to login in the social network| 2 hours  	| April 13                	| C         	|
| 21       	| Develop: Main page| Make the user able to see all posts| 2 hours  	| April 13                	| C         	|
| 22 | Develop: Add post feature | Make the user able to post a new entry in the social network | 2 hours | April 14 | C |
| 23 | Develop: Add datetime on the post feature | Make the user able to register the date of each post entry | 2 hours | April 16 | C |
| 24 | Develop: likes and comments features | Make the user able to interact with other users posts | 3 hours | April 23 | C |
| 25 | Develop: statistics page | Make the users able to see the studens and clubs of the week and students history. | 3 hours | April 25 | C |
| 26 | Develop: personal profile page | Make the user able to see all their posts and information | 2 hours | April 28 | C |
| 27 | Develop: Delete posts fature | Make the user able to delete their posts | 30 minutes | April 29 | C |
| 28 | Develop: Function to display message to the user | Make the user able to know when they need to post a new entry | 1 hour | May 1 | C |
| 29 | Develop: Download posts feature | Make the users able to dowload their portifolios in PDF format | 3 hours | May 2 | C |
| 30 | Develop: Log out feature | Clear all the cookies and make the user able to log out the website | 30 minutes | May 2 | C |
| 31 | Develop: upload pictures on the add post | Make the user able to add a picture on the the posts entries | 3 hours | May 5 | C |
| 32 | Develop: Validation of data entry | Make sure that the data entered by the user is valid and the website will not crash if the user enters an invalid data | 1 hour | May 5 | C |
| 33       	| Implement good coding practices |Organize final code and add commments | 1 hour  	| May 5 | C         	|
| 34 | Design:  List of existing tools | Make clear the tools used to make the website | 20 minutes | May 6 | B |
| 35 | Design:  List of techniques | Make clear the techniques used to make the website | 20 minutes | May 6 | B |
| 36 | Design: Flow diagrams | Showcase how my code works and explain it through flow diagrams | 2 hours | May 6 | B |
| 37 | Design: UML diagram | Show the relations between all the classes in the website | 40 minutes | May 6 | B |
| 38       	| Functionality: Script for video  | Write an organized script for the functionality video | 20 minutes 	| May 7 | D         	|
| 39       	| Functionality: Record video  | To showcase an explain the functionality of the website | 20 minutes 	| May 7 | D         	|
| 40 | Test: Test plan | Develop comprehensive testing strategies for the prototype, covering all aspects of the website, such as login, registration, and posting functionalities to make sure that the code runs without any error. | 1 hour | May 7 | C |
| 41 | Test: Execute test plan |  Execute the test plan an analize the outcomes| 20 minutes | May 7 | C |
| 42 | Test: Beta testing |  Execute the test plan with the client and an user to gather feedback | 20 minutes | May 7 | C |
| 43 | Implement: Debug|  Fix bugs in the website inf any | 20 minutes | May 7 | C,D |
| 44 | Evaluation: Client and user interview |  Verify that the success criteria are met and collect additional feedback and implementable recommendations| 20 minutes | May 7 | C |
| 45      	| Development: Organize and review project documentation | Make sure that everything is properly codumentaded | 30 minutes 	| May 8 |  C        	| 
| 46 | Development: Add citations | To give the credits for the resources used | 20 minutes | May 8 | C |


## Test Plan
| Instruction                                                  | Category               | Input/example code                                                                                                                                                                                                                   | Description                                                                                                                                                   | Expected output                                                                                                                                                                                                                                      | Success criteria |
|--------------------------------------------------------------|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| Test if the program runs without any error                   | Integration testing    | Run website                                                                                                                                                                                                                          | Run website                                                                                                                                                   | Website runs with 0 exit code                                                                                                                                                                                                                        | n/a              |
| Test registration function - email already registered        | Unit testing           | Username:Joe Email:john.doe@company.com Password: JoeDoe123@ Password confirmation:JoeDoe123@ Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                 | Register an account with an input of an email already registered                                                                                              | The user is not able to register and it is displayed the message:"⚠️User with that email already registered."                                                                                                                                         | 1                |
| Test registration function - email not valid                 | Unit testing           | Username:Joe Email:john.doecompany.com Password: JoeDoe123@ Password confirmation:JoeDoe123@ Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                  | Register an account with an input of an invalid email                                                                                                         | The user is not able to register and it is displayed the message:"Please include an '@' in the email adress. 'john.doecompany.com' is missing an '@'                                                                                                 | 1                |
| Test registration function - invalid password                | Unit testing           | Username:Joe Email:john.doe@company.com Password: 12345678 Password confirmation:12345678 Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                     | Register an account with an input of an invalid password that do not follow the pattern of having at least 8 characters one number and one special character. | The user is not able to register and it it displayed the message:"⚠️Password must be at least 8 characters long and contain at least one number and one special character."                                                                           | 1                |
| Test registration function - passwords do not match          | Unit testing           | Username:Joe Email:john.doe@company.com Password: JoeDoe123@ Password confirmation:JoeDoe123& Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                 | Register an account with an input of two different passwords                                                                                                  | The user is not able to register and it is displayed the message: "⚠️Passwords do not match"                                                                                                                                                          | 1                |
| Test registration function - Missing any fields              | Unit testing           | Username:   Email:john.doe@company.com Password: JoeDoe123@ Password confirmation:JoeDoe123& Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                  | Register an account missing inputs                                                                                                                            | The user is not able to register and it is displayed the message: "Please fill out this field"                                                                                                                                                       | 1                |
| Test registration function - correct input                   | Unit testing           | Username:Joe Email:john.doe@company.com Password: JoeDoe123@ Password confirmation:JoeDoe123@ Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum                                                                                 | Register an account, input username, email, password, password confirmation, biography, clubs - all information correct                                       | The user input has been securely saved in the database, their password has been transformed into a hashed format, and they have been directed to the 'login' page.                                                                                   | 1                |
| Test login function - correct input                          | Unit testing           | Username:Joe Email:john.doe@company.com Password: JoeDoe123@                                                                                                                                                                         | Login with email and password - all correct                                                                                                                   | The user is able to log in and is redirected to the main page.                                                                                                                                                                                       | 1                |
| Test login function - incorrect input                        | Unit testing           | Username:Joe Email:john.doe@company.com Password: JoeDoe                                                                                                                                                                             | Login with password incorrect                                                                                                                                 | The user is not able to log in and the login page is refreshed to allow the user to try again                                                                                                                                                        | 1                |
| Test login function - Missing any fields                     | Unit testing           | Username:Joe Email:john.doe@company.com Password: " "                                                                                                                                                                                | Login with missing inputs                                                                                                                                     | The user is not able to log in and it is displayed the message: "You must fill out this field"                                                                                                                                                       | 1                |
| Test add new post function - Missing any fields              | Unit testing           | Title: test, Description: ,Picture:"test.png" ,Club:ICE, date: 08/05/2023                                                                                                                                                            | Post with missing inputs                                                                                                                                      | The user is not able to post and it is displayed the message: "You must fill out this field"                                                                                                                                                         | 2                |
| Test add new post function - Correct input                   | Unit testing           | Title: test, Description:test ,Picture:"test.png" ,Club:ICE, date: 08/05/2023                                                                                                                                                        | Post with title, description, date, picture, club - all correct information                                                                                   | The user is able to add a post and information is stored in the database                                                                                                                                                                             | 2                |
| Test post reminder - no posts                                | Non functional testing | n/a                                                                                                                                                                                                                                  | User with no posts                                                                                                                                            | In the personal profile page it is displayed the message: "⚠️You have not posted anything in more than 7 days, Let's post something!"                                                                                                                 | 4                |
| Test post reminder - last post old than 7 days               | Non functional testing | Title: test, Description:test ,Picture:"test.png" ,Club:ICE, date: 01/05/2023                                                                                                                                                        | Post old than 7 days.                                                                                                                                         | In the personal profile page it is displayed the message: "⚠️You have not posted anything in more than 7 days, Let's post something!"                                                                                                                 | 4                |
| Test like function - for 1 user                              | Unit testing           | User 1 selects the like button for post 1                                                                                                                                                                                            | User 1 selects the like button for post 1                                                                                                                     | If user clicks the like button of the  post 1, the number of likes increases, if user clicks the button again, number of likes decreases, user can not like one post multiple times, number of likes is stored in the database                       | 5                |
| Test like function - for multiple users                      | Unit testing           | User 2 selects the like button for post 1                                                                                                                                                                                            | User 2 selects the like button for post 1                                                                                                                     | If user 2 clicks the like button the previous like count do not decrease, the like count increase, if user clicks the button again, number of likes decreases , user can not like one post multiple times, number of likes is stored in the database | 5                |
| Test download portfolio                                      | Unit testing           | n/a                                                                                                     | User selects option to download portfolio                                                                                                                     | The portfolio is downloaded in pdf showing the title, description, picture date and club of each post from that user.                                                                                                                                      | 3                |
| Test comments function - Correct input                       | Unit testing           | Comment: test                                                                                                                                                                                                                        | User add an comment to a post                                                                                                                                 | The user is able to add a comment, the comment is displayed in the post and stored in the database                                                                                                                                                   | 5                |
| Test comments function - Missing input                       | Unit testing           | Comment: " "                                                                                                                                                                                                                         | User add an empty comment to a post                                                                                                                           | The user is not able to add a comment and it is displayed the message: "You must fill out this field"                                                                                                                                                | 5                |
| Test 'Statistics' page display                               | Non functional testing | n/a                                                                                                                                                                                                                                  | User selects the 'statistics' button                                                                                                                          | Button redirects user to the 'statistics' page on which user can the students and clubs of the week and the students history.                                                                                                                        | 6                |
| Test Users profile display                                   | Non functional testing | n/a                                                                                                                                                                                                                                  | User selects the 'statistics' button and selects the name of a students in the "students history"                                                             | Button redirects user to the user profile that they clicked.                                                                                                                                                                                         | 7                |
| Test registration and login functions                        | Integrated testing     | Register - Username:Joe Email:john.doe@company.com Password: JoeDoe123@ Password confirmation:JoeDoe123@ Biography: "Hi mane is joe Doe" clubs: ICE,Peace Forum Login - Username:Joe Email:john.doe@company.com Password: JoeDoe123@ | User register a new account and login                                                                                                                         | The user is able to register a new account, the information is stored in the database, the user is redirected to the login page where the user is able to log in                                                                                     | 1                |
| Test statistics, create, delete, login and register function | Integrated testing     | n/a                                                                                                                                                                                                                                  | Register multiple users and create/delete multiple posts                                                                                                      | The Statistics page updated automatically according to the number of users registered, number of posts decreased if the post is deleted and increased if the post is added and the students and clubs of the week are also updated.                  | 1,2,6            |



## Existing tools

| Software/Development tools    	| Coding Structure Tools        	| Libraries         	|
|-------------------------------	|-------------------------------	|-------------------	|
| Python                        	| SQL requests                  	| sqlite3           	|
| SQlite                        	| If-else statements             	| passlib           	|
| Html                            | Encryption                    	| database_worker    |
| CSS              	   | Index              	            | Flask                    |
| PyCharm professional 2022.3.2   | For loops                              	| re	                  |
| Chrome (testing)                | Dictionaries                              	| werkzeug.utils                   	|
|                                	|  OOP (classes)                              	|  fpdf                 	|
|                                	|                                	|  os                 	|
## List of techniques used
|    | List of techniques used |
|----|-------------------------|
| 1  | Get/Post methods        |
| 2  | Functions               |
| 3  | If statements           |
| 4  | For loops               |
| 5  | SQL queries             |
| 6  | Lists                   |
| 7  | Password hashing        |
| 8  | Cookies                 |
| 9  | Dictionaries            |
| 10 | flasks routes           |

## Computational Thinking
| Computational thinking |
|------------------------|
| decomposition          |
| pattern recognition    |
| abstraction            |
| algorithm design       |

# Criteria C: Development

### Database scheme
To store and organize the data for the website I made a function called create_database():
```.py
# Create databases
def create_database():
    db = database_worker("social_net.db") #Initiate database connection
    query_user = """CREATE TABLE if not exists users(
                    id INTEGER PRIMARY KEY,
                    email text,
                    password text not NULL,
                    uname text,
                    description text,
                    clubs text,
                    posts INTEGER DEFAULT 0
                    )"""

    query_post = f"""CREATE TABLE if not exists posts(
            id INTEGER PRIMARY KEY,
            title VARCHAR(150),
            content text not NULL,
            club text,
            datetime text,
            user_id INTEGER,
            likes INTEGER DEFAULT 0,
            comments INTEGER DEFAULT 0,
            picture text,
            FOREIGN KEY(user_id) REFERENCES users(id) on delete cascade
            )"""

    query_comment = f"""CREATE TABLE if not exists comments(
            id INTEGER PRIMARY KEY,
            content text not NULL,
            user_id INTEGER,
            post_id INTEGER,
            FOREIGN KEY(user_id) REFERENCES users(id) on delete cascade,
            FOREIGN KEY(post_id) REFERENCES posts(id) on delete cascade
            )"""

    query_likes = f"""CREATE TABLE if not exists likes(
            id INTEGER PRIMARY KEY,
            post_id INTEGER,
            user_id INTEGER,    
            FOREIGN KEY(user_id) REFERENCES users(id) on delete cascade,
            FOREIGN KEY(post_id) REFERENCES posts(id) on delete cascade
    )"""
    db.run_save(query_likes)
    db.run_save(query_user)
    db.run_save(query_post)
    db.run_save(query_comment)
    db.close()
    create_database()
```
 To define how many tables I would use for the website I applied pattern recognition to identify common data elements and group them together in appropriate tables. For example, I recognized that user information such as email, password, username,clubs and description should be stored in a single table called "users. In this way I decided to create 4 tables, like it was showed in the ER diagram.

The function create_database first iniates the connection with the database using the class database_worker, then it defines four SQL queries, each of which creates a table in the database using the CREATE TABLE statement and with an if statement it makes sure to create the table only if a table with the same name does not exist. After defining each element on the data the function calls each query in and save them using the run_save() method of the database_worker. After running all queries, it closes the database connection. In this way all 4 tables are properly created.

To make it easir to work with the database I made a class on my_library called database_worker that provides methods for interacting with a SQLite database.
```.py
class database_worker:
    def __init__(self, name):
        self.connection = sqlite3.connect(name)  # Connect to the database with the given name
        self.cursor = self.connection.cursor()  # Create a cursor object to execute SQL commands

    # Method to execute a SELECT statement and return all results
    def search(self, query):
        result = self.cursor.execute(query).fetchall()  # Execute the SELECT statement and fetch all results
        return result  # Return the list of results

    # Method to execute a SELECT statement and return the first result
    def get(self, query):
        result = self.cursor.execute(query).fetchone()  # Execute the SELECT statement and fetch the first result
        return result  # Return the first result

    # Method to execute a query and commit changes to the database
    def run_save(self, query):
        self.cursor.execute(query)  # Execute the query
        self.connection.commit()  # Commit the changes to the database

    # Method to close the database connection
    def close(self):
        self.connection.close()  # Close the connection to the database
```
The __init__ method is the constructor for the class, which takes the name of the database file as an argument and sets up a connection to it.
The search method takes a query string as an argument, executes it on the database using the cursor object and returns all the resulting rows as a list.The get method also takes a query string as an argument, executes it on the database using the cursor object and returns only the first resulting row as a tuple.The run_save method takes a query string as an argument, executes it on the database using the cursor object and commits the changes to the database. Finally, the close method is used to close the connection to the database. With this method it is easier to execute queries in the code.

## Success criteria 1: The website should have a user registration and login system with encryption of the password.                             

### Registration   
To achieve the first success criteria I made a function to register in the website:
```.py
# Password validation regex: at least 8 characters, 1 number, and 1 special character
password_regex = r"^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{8,}$"
# Email validation regex
email_regex = r"[^@]+@[^@]+\.[^@]+"
@app.route('/register', methods=['GET', 'POST'])
def register():
    message = ""  # initializes an empty string for error messages
    if request.method == "POST":  # checks if form was submitted via POST request
        uname = request.form['name']  # retrieves name from form
        email = request.form['email']  # retrieves email from form
        passwd = request.form['password']  # retrieves password from form
        passwd_check = request.form['check_password']  # retrieves password confirmation from form
        bio = request.form['description']  # retrieves description from form
        clubs = request.form.getlist('clubs[]')  # retrieves list of clubs from form
        clubs_str = ', '.join(clubs)  # joins list of clubs into a single string separated by commas

        # Password validation
        if not re.match(password_regex, passwd):  # checks if password matches the defined regex
            message = "⚠️Password must be at least 8 characters long and contain at least one number and one special character."
            return render_template("register.html", message=message)  # displays error message on registration page
            
       # Email validation
        if not re.match(email_regex, email):  # checks if email matches the defined regex
            message = "⚠️Please enter a valid email address."
            return render_template("register.html", message=message)  # displays error message on registration page
            
        # Check if passwords match
        if passwd != passwd_check:  # checks if password and confirmation match
            message = "⚠️Passwords do not match."
            return render_template("register.html", message=message)  # displays error message on registration page

        db = database_worker('social_net.db')  # connects to database
        existing_user = db.get(f"SELECT * from users where email = '{email}'")  # checks if email already exists in database
        if existing_user:
            message = "⚠️User with that email already registered."
        else:
            new_user = f"INSERT into users (email,password,uname, description,clubs) values ('{email}','{encrypt_password(passwd)}','{uname}','{bio}','{clubs_str}')"  # creates SQL query to insert new user into database
            db.run_save(new_user)  # executes SQL query to insert new user into database
            db.close()  # closes database connection
            return redirect(url_for('login'))  # redirects user to login page after successful registration

    return render_template("register.html", message=message)  # displays registration page with error messages if any
```
To make the register function I first defined a flask route for the registration page and definied the method "post" to get the information posted by the user.The function first check if the request method is POST(if the user submitted the form to register), then it retrieves the user's name, email, password, password confirmation, bio, and selected clubs from the form data that is displayed in the register.html. Then I used a validation method: regular expressions (regex)  to make sure that the uer enter a valid email and secure passowrd
```.py
password_regex = r"^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{8,}$"
email_regex = r"[^@]+@[^@]+\.[^@]+"
 if not re.match(password_regex, passwd):
            message = "⚠️Password must be at least 8 characters long and contain at least one number and one special character."
            return render_template("register.html", message=message)
 if not re.match(email_regex, email):  # checks if email matches the defined regex
            message = "⚠️Please enter a valid email address."
            return render_template("register.html", message=message)  # displays error message on registration page
```
The password_regex is a pattern that defines the requirements for a valid password: it must have at least 8 characters, contain at least one number and one special character. and the email_regex  makes sure that the email contains the "@" symbol followed by a domain name and a top-level domain, such as ".com" or ".org". The re.match() method from the library "re" is used to check if the input password/email matches the regex patterns. If the password/email does not match the pattern, the code sets the message variable to indicate the specific password validation/email validation requirement that was not met and renders the "register.html" template with the message displayed to the user.

After this the function checks if the password and password confirmation are the same, for that I used the check_password function that I stored on my_library.py. If the passwords are the same, the function connect to the database using the database_worker class and then uses a SQL query to check if a user with the provided email already exists, If a user with the provided email exists the function sets the message variable to indicate this to the user. If the email does not exist, the function Inserts the user's name, email, password, bio and clubs in the database,in this way maiking the user able to register in the website, however the password is first hashed to ensure securiy and it is used the encrypt_password from my_library to do so.

Encrypt_password and check_password functions:
```.py
from passlib.context import CryptContext

# Create a password hashing configuration using the pbkdf2_sha256 algorithm
pwd_config = CryptContext(
    schemes=["pbkdf2_sha256"],
    default="pbkdf2_sha256",
    pbkdf2_sha256__default_rounds=30000
)

def encrypt_password(user_password):
    """Encrypt the user's password using the hashing configuration.

    Args:
        user_password (str): The plain text password provided by the user.

    Returns:
        str: The hashed password.

    """
    return pwd_config.encrypt(user_password)

def check_password(user_password, hashed):
    """Verify if the user's provided password matches the hashed password.

    Args:
        user_password (str): The plain text password provided by the user.
        hashed (str): The hashed password to compare against.

    Returns:
        bool: True if the provided password matches the hashed password, False otherwise.

    """
    return pwd_config.verify(user_password, hashed)
```

### My library
I used computational thinking abstraction to define high-level functions like encrypt_password, check_password and the class database_worker in a different file called My_library, because in this way I do not need to keep repeating thoses functions in the main code, I can use it by calling it name and the details of thoses functions are also hidden away from the rest of the code making it easier to understand and make changes to those functions if needed in the future. 
![Screen Shot 2023-05-10 at 17 14 49](https://github.com/EmmyAbella444/Unit_4/assets/111819437/c7f46c41-154a-40fd-b7b1-2db21372e1ad)




### Log in
To Achieve the first success criteria I made also alogin function
```.py
# Login page
@app.route('/login', methods=['GET', 'POST'])
def login():
    # Debugging statement to show that function has been called
    print("here")
    
    # Check if the form has been submitted using POST method
    if request.method == 'POST':
        # Get email and password from the submitted form
        email = request.form['email']
        passwd = request.form['password']
        
        # Check if email and password are not empty
        if len(email) > 0 and len(passwd) > 0:
            # Connect to the database
            db = database_worker('social_net.db')
            
            # Search for the user with the given email in the database
            user = db.search(f"SELECT id,email,password from users where email='{email}'")
            
            # If the user exists
            if user:
                # Get the user's id, email, and hashed password from the database
                user = user[0]  # search returns a list, so here I select one
                id, email, hash = user
                
                # Check if the given password matches the hashed password in the database
                if check_password(hashed=hash, user_password=passwd):
                    # Create a response with a redirect to the home page
                    resp = make_response(redirect('home'))
                    
                    # Set a cookie with the user's id
                    resp.set_cookie('user_id', f"{id}")
                    
                    # Debugging statement to show that the password is correct
                    print("password is correct")
                    
                    # Return the response
                    return resp
                
                # If the given password does not match the hashed password in the database
                else:
                    # Debugging statement to show that the password is incorrect
                    print("incorrect password")
    
    # If the request method is not POST or if the email and password are empty
    # Render the login template
    return render_template('login.html')

```
To make the login function I first defined a flask route for the login page and definied the method "post" to get the information posted by the user, and the method "GET" to handle a request to retrieve the login page. 

The login() function first checks if the request.method is'POST' to know if the user submmited a form. If the method is POST then the email and password entered in the form are obtained using request.form['email'] and request.form['password']. Then the fuction check if the email and password are not empty with "if len(email) > 0 and len(passwd) > 0". If they are not empty, the function connects to the database using the database_worker class and searches for the user with the given email in the database using a SQL query.

If the user exists in the database, their id, email, and hashed password are obtained from the database. The check_password function is used to compare the given password with the hashed password in the database. If the passwords match, a response with a redirect to the home page is created using make_response(redirect('home')). Then a cookie with the user's id is also set using resp.set_cookie('user_id', f"{id}"), to make it able for the users to have separate profiles in the website. If the password does not match the hashed password in the database the function refresh the page returning the login page using render_template('login.html').

## Success criteria 2:The website should allow users to post their activities and ensure that all posts are properly documented.
To achieve this criteria I made a home page which contains an option to add new posts and display all posts made by the users.
```.py
# main page
@app.route('/home', methods=['GET', 'POST'])
def home():
    # Check if user is logged in by checking if user_id cookie exists
    if request.cookies.get('user_id'):
        # Get the user_id from the cookie
        user_id = request.cookies.get('user_id')
        # Connect to the database
        db = database_worker("social_net.db")

        # If the form has been submitted
        if request.method == 'POST':
            # Get the values from the submitted form
            title = request.form['post-title']
            content = request.form['post-content']
            date_str = request.form['date']
            date_obj = datetime.datetime.strptime(date_str, '%Y-%m-%d')
            date = date_obj.strftime('%Y-%m-%d')
            club = request.form['club']
            f = request.files['file']
            filename = secure_filename(f.filename)
            f.save(os.path.join("static/images/", filename))

            # Insert new post into database
            new_post = f"""INSERT into posts(title, content, user_id, datetime,club, picture) values 
                        ('{title}','{content}',{user_id},'{date}','{clubs_str}','{filename}')"""
            db.run_save(new_post)

            # Update the count of posts for all users
            update_post_count = """UPDATE users SET posts = IFNULL((SELECT COUNT(*) FROM posts WHERE user_id = users.id), 0)"""
            db.run_save(update_post_count)

            # Redirect to the main page
            return redirect(url_for("home"))

        # Query the database to get the posts
        posts_query = """SELECT posts.id, posts.title, posts.content, posts.club, posts.likes, posts.comments, posts.datetime, users.uname, posts.club, posts.picture 
                         FROM posts 
                         INNER JOIN users ON posts.user_id=users.id
                         ORDER BY posts.id DESC"""
        posts = db.search(posts_query)

        # Query the database to get the comments for each post
        comments_dict = {}
        for post in posts:
            post_id = post[0]
            comments_query = f"""SELECT comments.content, users.uname 
                                 FROM comments 
                                 INNER JOIN users ON comments.user_id=users.id 
                                 WHERE comments.post_id={post_id}"""
            comments = db.search(comments_query)
            comments_dict[post_id] = comments

        # Pass the posts and comments dictionary to the HTML template
        return render_template("home.html", posts=posts, user_id=user_id, comments_dict=comments_dict)

    # If user is not logged in, redirect to the login page
    else:
        return redirect(url_for("login"))


```
Firstly I defined a Flask route for the '/home' URL, which can accept GET and POST requests.

Then  since it was a lot of taks to perform in only one function I used algorithm design to break down the problem into smaller, more manageable steps, and design a process to handle each step. So first the function "home",  check if the user is logged in by checking if the 'user_id' cookie exists. If the cookie does not exists then the user is redirected to the log in page. If the cookie exists, the user ID is retrieved from the cookie and a connection to a SQLite database named 'social_net.db' is established using the class database_worker.

Then the function checks if the request method is POST, which means that the user has submitted a form on the /home page to add a new post. The form data is then retrieved using request.form to get the title,datetime,club,content for the new post.

To add the datetime in the database, the first code that i did, the date was not being passed in the correct format, so I implemented the datetime library to convert the date string to a datetime object and then back to a formatted string to ensure that the date is in the correct format and is validated.

```.py
            date_str = request.form['date']
            date_obj = datetime.datetime.strptime(date_str, '%Y-%m-%d')
            date = date_obj.strftime('%Y-%m-%d')
```
To add the picture for the new post into the database I first requested it using the request object's 'files' attribute, which returns a dictionary-like object containing the uploaded files. Then I used the 'secure_filename' method from the Werkzeug library to sanitize the filename and remove any potential security vulnerabilities, such as directory traversal attacks. Finally, the 'save' method is called on the retrieved file object to save the file to the desired location on the server. This helps ensure that uploaded files are stored safely and securely.

```.py
            f = request.files['file']
            filename = secure_filename(f.filename)
            f.save(os.path.join("static/images/", filename))
```
To make sure that the user fill all the required forms to submit a new post I added the feature "required" in the HTML form, and in this way the user is not able to submit posts withou filling all section.

```.html
<form name="post" action="/home" method="POST" enctype = "multipart/form-data">
		<label class="label" for="post-title">Title</label>
        <input type="text" id="post-title" name="post-title" required placeholder="Enter post title...">
        <label class="label" for="post-content">Content</label>
        <textarea id="post-content" name="post-content" rows="8" required placeholder="Enter the description and your reflection..."></textarea>
		<label for="date">Date:</label><br>
		<input type="date" id="date" name="date" required title="Please select a date"><br>
        <label for="clubs">Club:</label><br>
        <select id="clubs" name="clubs[]" multiple required size="1" title="Please select one club">
            <optgroup label="Core clubs">
              <option value="Rainbow Alliance">Rainbow Alliance</option>
              <option value="Peace Forum">Peace Forum</option>
              <option value="ICE">ICE</option>
            </optgroup>
            <optgroup label="Student-led clubs">
              <option value="Politics club">Politics club</option>
              <option value="Entrepreneurship">Entrepreneurship</option>
            </optgroup>
          </select>
        <label for="photo">Upload your picture:</label><br>
        <input type="file" name="file" accept="image/*" required title="Please select one image" >
		<input type="submit" value="Submit">
	</form>
```
After retrivieng all elements, the new post is inserted into the database using an SQLquery with the details provided in the form. The function then updates the count of posts for all users in the database and redirects the user to the main page.

If the request method is "GET", the function queries the database to get all posts and comments associated with each post.
To get the comments I decided to use a dictionary, when the function retrievs comments from the database, a dictionary is created with the post id as the key and a list of comments as the value. This is because it allows for easy access to the comments for each post when rendering the HTML template. The dictionary also allows for efficient updating and accessing of comments when a new comment is added to a post. 
```.py
comments_dict = {}
        for post in posts:
            post_id = post[0]
            comments_query = f"""SELECT comments.content, users.uname 
                                 FROM comments 
                                 INNER JOIN users ON comments.user_id=users.id 
                                 WHERE comments.post_id={post_id}"""
            comments = db.search(comments_query)
            comments_dict[post_id] = comments
```
After retrivieng all data from posts and comments the function passes the data to the HTML template using the render_template() function. In this way the user is able to visualize all posts and add new entries.

## Success criteria 3:The website should allow users to download the portfolio in pdf format.
To achieve this success criteria, I first made a research and defined the best library for it. I chose to work with [^10]FPDF library since it is written entirely in Python, so it does not require any external dependencies and is able to add text and images to the pdf file.

```.py
@app.route('/save_pdf', methods=['POST', 'GET'])
def save_pdf():
    if request.cookies.get('user_id'):
        # print message to indicate that the cookie has been found
        print("The cookie was found")

        # get the user ID from the cookie
        user_id = request.cookies.get('user_id')

        # connect to the database
        db = database_worker('social_net.db')

        # search for all posts made by the user with the given user ID
        posts = db.search(f"SELECT title,content,datetime,club,picture from posts where user_id = {user_id}")

        # create a new PDF object
        pdf = FPDF()

        # add a new page to the PDF document
        pdf.add_page()

        # loop through each post and add it to the PDF document
        for p in posts:
            # set the font and add the post title to the PDF
            pdf.set_font("Arial", size=14)
            pdf.cell(0, 10, txt=p[0], ln=1)  # Title

            # set the font and add the post club to the PDF
            pdf.set_font("Arial", size=12)
            pdf.cell(0, 10, txt=p[3], ln=1)  # club

            # set the font and add the post datetime to the PDF
            pdf.set_font("Arial", size=12)
            pdf.cell(0, 10, txt=p[2], ln=1)  # Datetime

            # get the image path and add the image to the PDF
            image_path = os.path.join("static/images", p[4])
            pdf.image(image_path, x=10, y=pdf.get_y(), w=0, h=50)
            pdf.ln(50)

            # set the font and add the post content to the PDF
            pdf.multi_cell(0, 10, txt=p[1])  # Content
            pdf.ln()
            pdf.ln()

        # define the output file path for the PDF
        pdf_file_path = "posts.pdf"

        # save the PDF document to the output file path
        pdf.output(pdf_file_path)

        # create a Flask response object to send the PDF file as a download
        response = make_response(send_file(pdf_file_path, as_attachment=True))

        # set the content disposition header to force the file to download
        response.headers['Content-Disposition'] = f'attachment; filename=posts.pdf'

        # return the Flask response object
        return response

```
I first defined a Flask route called "save_pdf" that generates a PDF file containing all the posts made by a logged-in user. 
Then I made a function called save_pdf() that first checks if the user is logged in by checking the user_id cookie. Then, it connects to the database and use an SQL query to retrieve the title,content,datetime,club,pictures for all posts made by the user with the given user ID. 
Then it uses the FPDF library to create a new PDF object and add a new page to the PDF document. The I used a For loop for each post to set the font and adds the post title, club, datetime, image, and content to the PDF. The image is retrieved from the static/images directory using the filename stored in the database. The ln() method is used to add a new line after each element is added to the PDF.

After all posts are added to the PDF document, it defines the output file path for the PDF and saves the PDF document to that path. It then creates a Flask response object to send the PDF file as a download. It sets the content disposition header to force the file to download with a specified filename. Finally, it returns the Flask response object to the user's browser.


## Success criteria 4:The website should provide reminders for users to post about their activities. 
To achieve this criteria I decided to create a personal page where the user will be able to see all of their posts and a message will be displayed if the user has not posted anything on the last 7 days.
```.py
# Personal Profile
@app.route('/profile/<user_id>')
def profile_user(user_id: int):
    # Check if there is a user ID stored in a cookie, if so use it as the user ID
    if request.cookies.get('user_id'):
        print("The cookie was found")
        user_id = request.cookies.get('user_id')

    # Connect to the database
    db = database_worker("social_net.db")

    # Query the database to get the user information
    user_query = f"""SELECT uname, email, description, clubs FROM users WHERE id = {user_id}"""
    user_data = db.get(user_query)

    # Query the database to get all posts made by the user with the given user ID
    posts_query = f"""SELECT posts.id, posts.title, posts.content, posts.club, posts.likes, posts.comments, posts.datetime, users.uname, posts.picture 
                            FROM posts 
                            INNER JOIN users ON posts.user_id=users.id
                            WHERE user_id = {user_id}
                            ORDER BY posts.id DESC"""
    posts = db.search(posts_query)

    # Query the database to get the comments for each post
    comments_dict = {}
    for post in posts:
        post_id = post[0]
        comments_query = f"""SELECT comments.content, users.uname 
                                    FROM comments 
                                    INNER JOIN users ON comments.user_id=users.id 
                                    WHERE comments.post_id={post_id}"""
        comments = db.search(comments_query)
        comments_dict[post_id] = comments

    # Get the datetime of the last post (if there are any posts)
    last_post_date = None
    if len(posts) > 0:
        last_post_date = datetime.datetime.fromisoformat(posts[0][6])

    # Close the database connection
    db.close()

    # Check if the user has not posted in more than 7 days or has not posted at all
    show_warning = False
    if last_post_date is None or (datetime.datetime.now() - last_post_date).days > 7:
        show_warning = True

    # Render the profile.html template with the necessary data
    return render_template("profile.html", user=user_id, posts=posts, comments_dict=comments_dict,user_data=user_data, show_warning=show_warning)
```
I first created a flask route for the profile page and the made a function called profile_user() that first checks if the user is logged in by checking if the 'user_id' cookie exists. If the cookie does not exists then the user is redirected to the log in page. If the cookie exists, the user ID is retrieved from the cookie and a connection to the database is established using the class database_worker.

Then the function retrieves the user's information from the database(username, email, description, and clubs) and all posts made by the user with the given user ID. The posts are sorted in descending order by ID, so the latest post comes first. In this way users can see when was the last time that they posted. The function then queries the database again to retrieve the comments for each post.

To check when was the last time that the user posted, I first checked if the user had any post:
```.py
# Get the datetime of the last post (if there are any posts)
last_post_date = None
if len(posts) > 0:
    last_post_date = datetime.datetime.fromisoformat(posts[0][6])
```
First it is initialized the last_post_date variable to None. This is done because if there are no posts for the user, there won't be a last post date to retrieve. Then This line:if len(posts) > 0  checks if there are any posts for the user by checking the length of the posts list. If the length is greater than 0, then there are posts, and the code will proceed to retrieve the date of the last post.

If there are posts the line:last_post_date = datetime.datetime.fromisoformat(posts[0][6]) retrieves the date of the last post made by the user. It does this by accessing the first post in the posts list (which has the most recent date, since the posts are sorted in descending order by ID), and then retrieving the 7th item in the tuple returned by the database query. This 7th item contain the date and time of the post .The retrieved date is in ISO format (e.g. "2022-05-09") and is converted to a datetime object using the fromisoformat() method of the datetime.datetime class. The resulting datetime object is stored in the variable last_post_date. After this the database connection is closed.

The next is step is to check if the last posts is older then 7 days:

```.py
# Check if the user has not posted in more than 7 days or has not posted at all
show_warning = False
if last_post_date is None or (datetime.datetime.now() - last_post_date).days > 7:
    show_warning = True
```
 So first it is initializes the show_warning variable to False. The purpose of this variable is to indicate whether a warning message should be displayed to the user. If the user has not posted in more than 7 days or has not posted at all, the warning message will be displayed.
Then the function checks if last_post_date is None or use this line:(datetime.datetime.now() - last_post_date).days > 7 to checks whether the user has not posted in more than 7 days or has not posted at all. If last_post_date is None, it means that the user has not posted anything yet. If the difference between the current date and last_post_date is greater than 7 days, it means that the user has not posted in more than 7 days. In either case, the show_warning variable is set to True.

Finally, the function renders the profile.html template with the necessary data, including the user ID, user data, posts, comments, and whether to show the warning message. In this way a message will be displayed if the user forgets to update their portfolios.

## Success criteria 5: The website should allow users to like and comment on other users posts.
To achieve this criteria I made two functions: one to like and one to comment posts.
### Function to like posts
```.py
# feature to like posts
@app.route('/post/<int:post_id>/like', methods=['POST'])
def like_post(post_id):
    if request.cookies.get('user_id'):
        user_id = int(request.cookies.get('user_id'))
        db = database_worker("social_net.db")

        # Get the post from the database
        post_query = f"SELECT * FROM posts WHERE id={post_id}"
        post = db.search(post_query)[0]

        # Check if the user has already liked the post
        likes_query = f"SELECT * FROM likes WHERE post_id={post_id} AND user_id={user_id}"
        user_like = db.search(likes_query)

        if user_like:
            # If the user has already liked the post, remove their like
            delete_like_query = f"DELETE FROM likes WHERE post_id={post_id} AND user_id={user_id}"
            db.run_save(delete_like_query)

        else:
            # If the user hasn't liked the post yet, add their like
            add_like_query = f"INSERT INTO likes(post_id, user_id) VALUES ({post_id}, {user_id})"
            db.run_save(add_like_query)

        # Update the likes count for the post in the database
        likes_query = f"SELECT COUNT(*) FROM likes WHERE post_id={post_id}"
        likes_count = db.search(likes_query)[0][0]
        update_post_query = f"UPDATE posts SET likes={likes_count} WHERE id={post_id}"
        db.run_save(update_post_query)

        db.close()

        return redirect(url_for("home"))
    else:
        return redirect(url_for("login"))

```
First I made a Flask route for liking posts. The route is specified as "/post/int:post_id/like", where "int:post_id" is a URL parameter that specifies the ID of the post being liked. Then I made a function called Like_post that handles the POST request for liking/unliking a post. The "post_id" parameter is passed in from the URL parameter.

Then the function checks if the user is logged in by checking if the 'user_id' cookie exists. If the cookie does not exists then the user is redirected to the log in page. If the cookie exists, the user ID is retrieved from the cookie and a connection to the databaseis established using the class database_worker. I made sure to get the user ID from the user that liked the post because the first time that I coded this function, it was not working for multiples user, since one user could remove the like from anoter use, and with the user id I can check if that user has already liked that post.

Next, the function retrieves the post with the specified 'post_id' from the database by executing a SQL query using the 'database_worker' object. After this I added a feature to make sure that one user can only like a post one time, first it checks if the user has already liked the post by executing another SQL query to search for a 'like' record in the 'likes' table that matches the current user ID and post ID. If a like record exists, the function deletes it, effectively removing the like. If a like record does not exist, the function adds a new 'like' record to the 'likes' table, indicating that the user has liked the post.

After adding or removing the like, the function updates the 'likes' count for the post in the 'posts' table by executing another SQL query. It retrieves the current count of likes for the specified post and updates the 'likes' column in the 'posts' table accordingly. Finally, the function closes the database connection and redirects the user to the home page with the likes count updated.

To make the like button look like a heart I asked chat gpt[^11] with the following prompt: "make the css code for a hear format button", and I got this code from it, which made the button to like it be user-friendly and visually appealing:
```.css
.like-button {
  border: none;
  background-color: transparent;
  color: #262626;
  font-size: 14px;
  font-weight: bold;
  cursor: pointer;
  padding: 0;
  display: inline-flex;
  align-items: center;
}

.like-button:hover {
  color: #e0245e;
}

.like-button:focus {
  outline: none;
}


.like-button i {
  font-size: 27px;
  margin-right: 5px;
}

.like-button span {
  margin-left: 5px;
}

.fa-heart {
  font-size: 40px;
  color: #e0245e;
}
```
### Function to add comments
```.py
# feature to add comments on posts
@app.route('/post/<int:post_id>/add_comment', methods=['POST'])
def add_comment(post_id):
    if 'user_id' in request.cookies:
        user_id = int(request.cookies['user_id'])
        comment = request.form['comment']
        db = database_worker("social_net.db")

        # Insert the comment into the database
        insert_comment = f"INSERT INTO comments (content, user_id, post_id) VALUES ('{comment}','{user_id}','{post_id}')"
        db.run_save(insert_comment)

        # Update the post count in the database for the specific post
        update_count = f"UPDATE posts SET comments = (SELECT COUNT(*) FROM comments WHERE post_id = {post_id}) WHERE id = {post_id}"
        db.run_save(update_count)

        return redirect(url_for("home"))
    else:
        return redirect(url_for("login"))
```
First I made a Flask route to add comments on posts. The route is specified as "/post/int:post_id/add_comment", where "int:post_id" is a URL parameter that specifies the ID of the post receiving the comment. Then I made a function called add_comment that handles the POST request for addinf a comment to a post. The "post_id" parameter is passed in from the URL parameter.

When a user submits a comment on a post, the function first checks if the user is logged in by checking for the 'user_id' cookie in the request. If the user is not logged in, the code redirects them to the login page. If the user is logged in, the code retrieves the user_id from the cookie and the comment from the form data submitted by the user.

Next, the function inserts the comment into the comments table, associating it with the user and the post. This is done by executing an INSERT SQL query. After the comment is inserted into the database, the function updates the comments count for the post by executing an UPDATE SQL query that counts the number of comments for the post and sets the comments field in the posts table to that count. This ensures that the comments count for the post stays up-to-date. After this the code closes the database connection, redirects the user to the home page. In this way the user is able to add a comment in the desired post.

## Success criteria 6:The website should have a page with statistics of every student showing the last time that students posted. 

```.py
@app.route('/statistics')
def statistics():
    # Connect to the database
    db = database_worker("social_net.db")

    # Retrieve the user with the most posts for the current week
    users =("""SELECT users.uname, COUNT(posts.id) AS post_count
           FROM users
           JOIN posts ON users.id = posts.user_id
           WHERE posts.datetime > date('now', '-7 days')
           GROUP BY users.id
           ORDER BY post_count DESC
           LIMIT 3""")
    most_posts_user = db.search(users)
    print(most_posts_user)

    # Retrieve the uname, last post time and total number of posts for all students, order by most recent to least
    students =("""SELECT users.uname, MAX(posts.datetime) as last_post_time, COUNT(posts.id) as total_posts,users.id
                    FROM users
                    JOIN posts ON users.id = posts.user_id
                    GROUP BY users.id
                    ORDER BY last_post_time ASC""")
    student_stats = db.search(students)


    # Retrieve the club(s) with the most posts for the current week
    clubs = ("""SELECT posts.club, COUNT(posts.id) AS post_count
           FROM posts
           WHERE posts.datetime > date('now', '-7 days')
           GROUP BY posts.club
           ORDER BY post_count DESC
           LIMIT 3""")
    most_posts_clubs = db.search(clubs)

    # Close the database connection
    db.close()

    # Render the template with the retrieved data
    return render_template('statistics.html', most_posts_user=most_posts_user, student_stats=student_stats, most_posts_clubs=most_posts_clubs)

```

## Success criteria 7:The website should allow users to visit each others profile.     
```.py
@app.route('/students_profile/<int:user_id>', methods=['GET'])
def students_profile(user_id):
    db = database_worker("social_net.db")

    # Query the user's data
    user_query = f"""SELECT uname, email, description, clubs FROM users WHERE id = {user_id}"""
    user_data = db.get(user_query)

    # Query the user's posts
    posts_query = f"""SELECT posts.id, posts.title, posts.content, posts.club, posts.likes, posts.comments, posts.datetime, users.uname, posts.picture 
                      FROM posts 
                      INNER JOIN users ON posts.user_id=users.id
                      WHERE user_id = {user_id}
                      ORDER BY posts.id DESC"""
    posts = db.search(posts_query)

    # Query the comments for each post
    comments_dict = {}
    for post in posts:
        post_id = post[0]
        comments_query = f"""SELECT comments.content, users.uname 
                             FROM comments 
                             INNER JOIN users ON comments.user_id=users.id 
                             WHERE comments.post_id={post_id}"""
        comments = db.search(comments_query)
        comments_dict[post_id] = comments

    db.close()

    return render_template("students_profile.html", user_data=user_data, posts=posts, comments_dict=comments_dict)
```


# Criteria D: Functionality
## A video demonstrating the proposed solution with narration


# Criteria E: Evaluation

## Client
| Criteria                                                                                                       | Met or Not? | Feedback               |
|----------------------------------------------------------------------------------------------------------------|-------------|------------------------|
| 1. The website should have a user registration and login system with encryption of the password.               | Met         | No additional feedback |
| 2. The website should allow users to post their activities and ensure that all posts are properly documented.  | Met         | No additional feedback |
| 3. The website should allow users to download the portfolio in pdf format.                                     | Met         | No additional feedback |
| 4. The website should provide reminders for users to post about their activities.                              | Met         | No additional feedback |
| 5. The website should allow users to like and comment on other users posts.                                    | Met         | No additional feedback |
| 6. The website should have a page with statistics of every student showing the last time that students posted. | Met         | No additional feedback |
| 7. The website should allow users to visit each others profile.                                                | Met         | No additional feedback |

## Other user

### Citations
[^1]:  https://www.canva.com/
[^3]: https://www.softwaretestinghelp.com/website-vs-web-application/
[^4]: https://able.bio/hardikshah/6-reasons-why-flask-is-better-framework-for-web-application-development--cd398f73
[^5]: https://codeclan.com/blog/top-5-reasons-you-should-learn-html-css/#:~:text=CSS%20or%20Cascading%20Style%20Sheets,that%20structure%20come%20to%20life.
[^6]:https://www.simplilearn.com/tutorials/sql-tutorial/what-is-sqlite#:~:text=SQLite%20is%20used%20to%20develop,some%20data%20within%20an%20application.
[^7]:https://haveagreatdata.com/posts/why-you-dont-want-to-use-csv-files/
[^8]:https://djangostars.com/blog/python-web-development/
[^9]:https://www.lucidchart.com/
[^10]:https://pyfpdf.readthedocs.io/en/latest/
[^11]:https://chat.openai.com/

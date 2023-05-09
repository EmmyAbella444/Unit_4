

# Unit 4: The CasHub - Create, Interact and Showcase Your Clubs and Activities!
![CasHub (2)](https://user-images.githubusercontent.com/111819437/230899973-d353750e-ac64-4d2c-80a1-a1263a509b46.png)


Fig1.Logo for the website made in Canva[^1]


# Criteria A: Planning

## Problem definition
In the international baccalaureate program, students must create a CAS portfolio to show their participation in extracurricular activities. Unfortunately, the students from a local school are having difficulty with their portfolios. Many of them lack proper documentation and forget to update their portfolios every week. Because the current portfolio makes it hard for teachers to keep track of their progress since they have to open multiple links for each student, which is time-consuming. The CAS portfolio is also used to assess a student's development of skills like collaboration and communication. However, the current portfolio does not facilitate this since it does not allow students to view each other's profiles, collaborate or interact with them. Additionally, the current portfolio does not have the option to download the activities in pdf format, which is an IB requirement, making it difficult for students to demonstrate their involvement which can result in them potentially receiving a lower grade and this can negatively impact their IB score and future university applications.

## Proposed Solution
To address this problem, I first ran interviews[^2] with the client and based on that I decided to create a website, called CasHub. It will work like a social network because it allows students to post their activities and interact with each other. With the client's approval, I decided to use Python Flask, CSS, and HTML because it allows the creation of a dynamic and interactive website, which is essential for a social network-style platform. In CasHub students will be able to create profiles and log in, make posts about their activities, check a statistics page to track progress, and have a personal profile page with options to delete posts and download activities as PDFs. All this information will be stored in SQLite databases because they are supported by Python Flask. 


### Rationale

The choice of Python Flask, HTML, CSS, and SQLite for building CasHub is based on their suitability for creating a dynamic and interactive social network-style website that meets the needs of the school's students and teachers.

The network-style website[^3] was chosen because it can run on browsers that all users will be able to access from any computer, differently from the application for example. It also allows post and get requests that make the users able to log in, and posts their activities. 

Python Flask[^4] was chosen because its simplicity and flexibility make it ideal for building web applications that require frequent updates and modifications, such as a social network like CasHub. Additionally, Flask offers built-in support for SQLite, which is the database management that CasHub will use to store user data on CasHub and also it allows for easy integration with the front-end technologies that will be used:HTML and CSS.

HTML and CSS[^5] were chosen becase HTML is used for structuring the content of web pages, while CSS is used for styling the content, making it visually appealing and easy to navigate creating a user-friendly and intuitive interface that is essential for the success of any social network.

SQLite[^6] was chosen as the database management system for CasHub because it offers robust and safe data consistency, differently from CSV.files[^7] for example, ensuring that the information submitted by students is consistent, reliable, and easily accessible, which is essential for a perfect CasPortifolio.


## Design Statement

I will design and make a Website for a client who are students and teacher from a local school. The website will be a social network to post, monitor, interact, and download CAS activities and is constructed using the software CSS, HTML, and PYTHON. It will take 4 weeks to make and will be evaluated according to the following success criteria.

### Success Criteria
| Succsses criterias                                                                               |
|--------------------------------------------------------------------------------------------------|
| 1. The website should have a user registration and login system with encryption of the password. | 
| 2. The website should allow students to post their activities and ensure that all posts with activities are properly documented.             |                
| 3. The website should allow students to download the portfolio.                                  |           
| 4. The website should provide reminders for students to post about their activities.             |               
| 5. The website should allow students to like and comment on other student's posts.               |                
| 6. The website should have a page with statistics of every student on posts per week.            |                
| 7. The website should allow users to visit each others profile.                               |                


# Criteria B: Design
## System Diagram
![Habit Tracker (3)](https://user-images.githubusercontent.com/111819437/236936740-f0cd75c5-697b-471b-b19a-4d071192a0e4.png)


Fig.2 Shows the System Diagram for the project.

The System Diagram represents the different parts of the websited and how they relate to eachother. The website user uses Python to create the my.app file that interacts with the templates in HTML, as well as the Flask Library and other external libraries and My_Library to create the Python flask server. The arrows in the diagram indicate the data that is stored in the Social_net.db database, which utilizes the SQLite database engine.


## Wireframe
![name](https://user-images.githubusercontent.com/111819437/236926641-5bb8fcf1-dc2a-4a7a-a55c-a8e0f7744ea0.png)

fig.3 Shows the wirefram diagram for CasHub social network.

This wirefram shows all the screen in the social netwrok(login, register, main page, statistics, personal profile and users profile).The arrows extending from the buttons to the screens indicate to the user which screen will be opened when they click and release the button

## UML Diagram
![uml (3)](https://user-images.githubusercontent.com/111819437/236927524-8618af73-6f97-4098-b783-a046514fb2a4.png)

Fig.4 This UML shows the classdatabase_worker.

This class is used to control the database interaction. It has 4 methods and 2 private instance variables. The __init__() method initializes the connection and cursor variables using the sqlite3 module. The search() method takes a SQL query as input and returns a list of tuples as a result. The get() method also takes a SQL query as input and returns only the first result as a tuple. The run_save() method executes the given SQL query and commits the changes. Finally, the close() method closes the database connection.


## ER Diagram
![ER diagram](https://user-images.githubusercontent.com/111819437/236806597-c08f7319-9175-477a-b616-22c6f70955d0.png)

Fig.5 Shows the ER Diagram for the database used in the social network. 

The databse named:"Social_net.db" is organized with 4 tables: "Comments", "users", "likes" and "posts". This diagram also shows that one user can have multiple posts which can have multiple likes and comments.







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

![flow diagram 2 (3)](https://user-images.githubusercontent.com/111819437/236940378-0d0856d0-5273-4278-a133-89bfd7c14630.png)
Fig 10. Show the flodiagram for the add comments function.

This function first checks if the user is logged in by checking if their user ID exists in the request cookies. If the user is logged in, it retrieves the user ID and the comment content from the request form. Then, it connects to the database and inserts the comment into the comments table using an SQL query. It also updates the post's comment count in the posts table using another SQL query and closes the database. Finally, it redirects the user to the home page. If the user is not logged in, it redirects them to the login page.


![flow diagram 2 (4)](https://user-images.githubusercontent.com/111819437/236961811-3c942edd-6b85-48e3-8c38-479bcaa87f58.png)
Fig 10. Show the flodiagram for home page function.

This function is responsible for rendering the home page, fist it checks if the user is logged in, and if so, it initiates the database to  retrieve posts and comments for each post and passes them to the HTML template.If there is a "POST" request it checkes if all data is valid and save this new post in the database,  If the user is not logged in, it redirects them to the login page.













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
| Test download portfolio                                      | Unit testing           | Post - Title: test, Description:test ,Picture:"test.png" ,Club:ICE, date: 08/05/2023                                                                                                                                                 | User selects option to download portfolio                                                                                                                     | The portfolio is download showing the title, description, picture date and club of each activity in pdf format.                                                                                                                                      | 3                |
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
| CSS              	| For loops   | Index              	            | Flask                    |
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

## Development C

# Criteria D: Functionality
## A video demonstrating the proposed solution with narration

# Criteria E




### Citations
[^1]:  https://www.canva.com/
[^3]: https://www.softwaretestinghelp.com/website-vs-web-application/
[^4]: https://able.bio/hardikshah/6-reasons-why-flask-is-better-framework-for-web-application-development--cd398f73
[^5]: https://codeclan.com/blog/top-5-reasons-you-should-learn-html-css/#:~:text=CSS%20or%20Cascading%20Style%20Sheets,that%20structure%20come%20to%20life.
[^6]:https://www.simplilearn.com/tutorials/sql-tutorial/what-is-sqlite#:~:text=SQLite%20is%20used%20to%20develop,some%20data%20within%20an%20application.
[^7]:https://haveagreatdata.com/posts/why-you-dont-want-to-use-csv-files/

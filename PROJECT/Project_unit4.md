

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
1. The website should have a user registration and login system with encryption of the password.
2. The website should ensure that all posts with activities are properly documented. 
3. The website should allow students to download the portfolio.
4. The website should provide reminders for students to post about their activities.
5. The website should allow students to like and comment on other student's posts.
6. The website should have a page with statistics of every student on posts per week.
7. The website should allow students to visit each others profile.


# Criteria B: Design
## System Diagram
![Habit Tracker (2)](https://user-images.githubusercontent.com/111819437/232434049-991cecb2-b176-498c-8fed-634777d20211.png)
Fig.4 Shows the System Diagram for the project, The application uses PyCharm with an app.py python file, templates in HTML and static files in CSS. As well as the Flask Library, and My_Library libraries to create the program. The arrows in the diagram indicate the data that is stored in the Social_net.db database, which utilizes the SQLite database engine.


## Wireframe

## UML Diagram

## ER Diagram
![ER diagram](https://user-images.githubusercontent.com/111819437/236806597-c08f7319-9175-477a-b616-22c6f70955d0.png)
Fig.5 Shows the ER Diagram for the database used in the social network. The databse named:"Social_net.db" is organized with 4 tables:


## Flow Diagrans





## Test Plan
| Description                                 	| Type                            	| Inputs                                                                             	| Outputs                                                                                                  	|
|---------------------------------------------	|---------------------------------	|------------------------------------------------------------------------------------	|----------------------------------------------------------------------------------------------------------	|



## Record of Tasks
| Task No 	| Planned Action          	| Planned Outcome                           	| Time estimate 	| Target completion date 	| Criterion 	|
|---------	|-------------------------	|-------------------------------------------	|---------------	|------------------------	|-----------	|
| 1       	| Brainstorm of ideas     	| Have the first ideas for the project      	| 30 minutes    	| April 4                	| A         	|
| 2       	| Start the documentation 	| Have the first draft of the documentation 	| 20 minutes    	| April 4                	| B         	|
| 3       	| Make a folder in code pen	| Have ideas for the wireframe of the project	| 30 minutes    	| April 7                	| A         	|
| 4       	| Select final idea	|Choose the best idea for the project | 30 minutes    	| April 8                	| A         	|
| 5       	| Write the problem difinition	| To have a clear ideia for the proposed solution	| 30 minutes    	| April 8                	| A         	|
| 6       	| Write the design statement - Proposed solution	|To have a better idea on how the application is going to look like	| 30 minutes    	| April 8                	| A         	|
| 7       	| Define the success criterias	| to have a clear idea about the features in the application	| 30 minutes    	| April 8    	| A         	|
| 8       	| Make the ER diagram	| Have an idea of the the data entities, attributes, and relationships between them	| 30 minutes    	| April 8                	| B         	|
| 9       	| Design the wireframe| Have a clear view of how the website is going to look like	| 2 hours   	| April 8                	| B         	|
| 10       	| Design the system diagram	|To have a clear idea of the hardware and software requirements for the proposed solution | 1 hour    	| April 9                	| B         	|
| 11       	| Create logo| have a logo that shows what the program is about| 1 hour  	| April 10                	| C         	|
| 12       	| Create the databases and tables following the ER diagram| to store the data for the program	| 30 minutes    	| April 10                	| C         	|
| 13       	| Create desigh for signup and register page	| Make designs on canva to make the social network more appelealing| 30 minutes    	| April 7                	| C         	|
| 14       	| Create different routes for sign up, register, mainpage, personal profile, users profile and statistics| Have the pages of the social network	| 2 hours   	| April 8                	| C         	|
| 15       	| Code the features registration page| Make the user able to register their personal data| 2 hours  	| April 11                	| C         	|
| 16       	| Code the features from login page| Make the user able to login in the social network| 2 hours  	| April 11                	| C         	|
| 17       	| Code the Main page| Make the user able to see all posts| 2 hours  	| April 12                	| C         	|
| 18       	| Code the add post feature| Make the user able to post a new entry in the social network| 2 hours  	| April 12                	| C       
| 19       	| Fix the datetime of the post featuers| Make the user able to register the date of each post entry| 2 hours  	| April 20                	| C       
| 20       	| Fix the design of the mainpage| Make it visualy pretty and user friendly| 2 hours  	| April 23                	| C  
| 21       	| Code the likes and comments features| Make the user able to interact with other users posts| 2 hours  	| April 25 | C| 
| 22       	| Code the statistics page | Make the users able to see the studens and clubs of the week and students history.| 2 hours  	| April 28                	| C         	|
| 23       	| Code the personal profile page| Make the user able to see all their posts| 2 hours  	| April 29                	| C         	|
| 24       	| Code the delete posts fature| Make the user able delete their posts| 2 hours  	| April 29                	| C         	|
| 25       	| Code the function to display message to the users | Make the user able to know when they need to post a new entry| 2 hours  	| May 5 | C | 
| 26       	|Code the function do dowload posts | Make the users able to dowload their portifolios| 2 hours  	| May 5 | C | 
| 27       	| Fix the uploade of pictures on the add post | Make the user able to add photos on the posts| 2 hours  	| May 5 | C | 
| 28       	| Code the Main page| Make the user able to see all posts| 2 hours  	| April 12                	| C         	|
| 29       	| Fix the uploade of pictures on the add post | Make the user able to add photos on the posts| 2 hours  	| May 5 | C | 




## Existing tools

| Software/Development tools    	| Coding Structure Tools        	| Libraries         	|
|-------------------------------	|-------------------------------	|-------------------	|
| Python                        	| SQL requests                  	| sqlite3           	|
| SQlite                        	| Database                      	| passlib           	|
|                               	| Encryption                    	| database_handler                   	|
| Github Copilot                	| For loops                     	| encrypto_password  	|
| Html                                	| If-else statements            	| 	|
| CSS                              	|  	|                   	|
| PyCharm professional 2022.3.2                               	| Index                         	|                   	|

## Development C

# Criteria D: Functionality
## A video demonstrating the proposed solution with narration


# List of thechinics
flasks routes
cookies
validation
SQL queries
Hashing password
searching
admin page
statistics
tags
D3js

### Citations
[^1]:  https://www.canva.com/
[^3]: https://www.softwaretestinghelp.com/website-vs-web-application/
[^4]: https://able.bio/hardikshah/6-reasons-why-flask-is-better-framework-for-web-application-development--cd398f73
[^5]: https://codeclan.com/blog/top-5-reasons-you-should-learn-html-css/#:~:text=CSS%20or%20Cascading%20Style%20Sheets,that%20structure%20come%20to%20life.
[^6]:https://www.simplilearn.com/tutorials/sql-tutorial/what-is-sqlite#:~:text=SQLite%20is%20used%20to%20develop,some%20data%20within%20an%20application.
[^7]:https://haveagreatdata.com/posts/why-you-dont-want-to-use-csv-files/

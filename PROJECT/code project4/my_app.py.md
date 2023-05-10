```.py

### Libraries

import re
from werkzeug.utils import secure_filename
from flask import Flask, make_response
app = Flask(__name__)
from flask import Flask, render_template, request, redirect, url_for
from datetime import datetime
from fpdf import FPDF
import os
from flask import send_file
import datetime
from My_library import encrypt_password, check_password,  database_worker


app = Flask(__name__)

# Create databases
def create_database():
    db = database_worker("social_net.db")
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
            clubs = request.form.getlist('clubs[]')
            clubs_str = ', '.join(clubs)
            f = request.files['file']
            filename = secure_filename(f.filename)
            f.save(os.path.join("static/images/", filename))


            if len(title) > 0 and len(content) > 0:
                new_post = f"""INSERT into posts(title, content, user_id, datetime,club, picture) values 
                        ('{title}','{content}',{user_id},'{date}','{clubs_str}','{filename}')"""
                db.run_save(new_post)

                # Update the count of posts for all users
                update_post_count = """UPDATE users SET posts = IFNULL((SELECT COUNT(*) FROM posts WHERE user_id = users.id), 0)"""
                db.run_save(update_post_count)

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

    else:
        return redirect(url_for("login"))




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


# First page - go direct to login page
@app.route('/')
@app.route('/index')
def index():
    return render_template("login.html")


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



# Register page

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
        existing_user = db.get(
            f"SELECT * from users where email = '{email}'")  # checks if email already exists in database
        if existing_user:
            message = "⚠️User with that email already registered."
        else:
            new_user = f"INSERT into users (email,password,uname, description,clubs) values ('{email}','{encrypt_password(passwd)}','{uname}','{bio}','{clubs_str}')"  # creates SQL query to insert new user into database
            db.run_save(new_user)  # executes SQL query to insert new user into database
            db.close()  # closes database connection
            return redirect(url_for('login'))  # redirects user to login page after successful registration

    return render_template("register.html", message=message)  # displays registration page with error messages if any


# Personal Profile
@app.route('/profile/<user_id>', methods=['GET', 'POST'])
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

#Statistics page
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



# feature to save pdf
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



# Log out
@app.route('/logout')
def logout():
    resp = make_response(render_template('login.html'))
    resp.set_cookie('user_id', "", expires=0)  # delete cookie
    return render_template("login.html")

#feature to delete posts
@app.route('/delete_post', methods=['POST'])
def delete_post():
    if request.cookies.get('user_id'):
        print("The cookie was found")
        user_id = request.cookies.get('user_id')

    post_id = request.form['post_id']
    db = database_worker("social_net.db")
    delete_post=f"""DELETE FROM posts WHERE id={post_id}"""
    delete_com=f"""DELETE FROM comments WHERE post_id={post_id}"""
    delete_like=f"""DELETE FROM likes WHERE post_id={post_id}"""
    update_post_count = """UPDATE users SET posts = IFNULL((SELECT COUNT(*) FROM posts WHERE user_id = users.id), 0)"""

    db.run_save(update_post_count)
    db.run_save(delete_post)
    db.run_save(delete_com)
    db.run_save(delete_like)
    return redirect(url_for('profile_user', user_id=user_id))


# students profile page
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


create_database()
if __name__ == '__main__':


    app.run()
```

```.html
<!DOCTYPE html>
<html>
<head>
	<title>Home</title>
	<link rel="stylesheet" href="/static/profile.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
<div class="container-top">
	<div class="logo">
		<img src="/static/logo (1).png" alt="Logo">
	</div>
	<div class="profile-buttons">
		<div class="logout-button">
			<a href="{{ url_for("home", user_id=user_id) }}"><img src="/static/logout.png" alt="Logout Icon"></a>
		</div>
        <div class="statistics-button">
            <a href="{{ url_for('save_pdf', user_id=user_id) }}"><img src="/static/dowload.png" alt="Dowload Icon"></a>
        </div>
	</div>
</div>
<div class="container-profile">
	<h2>{{ user_data[0] }}'s profile</h2>
    <p>Your username:{{ user_data[0] }}</p> {# username #}
    <p>Email:{{ user_data[1] }}</p> {# email #}
    <p>Biography: {{ user_data[2] }}</p> {# bio #}
    <p>Clubs:{{ user_data[3] }}</p> {# clubs #}
{% if show_warning %}
<div class="alert alert-warning" role="alert">
  ⚠️You have not posted anything in more than 7 days, Let's post something!⚠️
</div>
{% endif %}
</div>
<div class="container-posts">
	<h3>{{ user_data[0] }}'s posts</h3>
	{% for p in posts %}
  		<div class="post-container">
    		<span class="post-username">{{ p[7] }}</span>{# username #}
    		<span class="post-datetime">{{ p[6] }}</span>  {# datetime #}
    		<span class="post-title">{{ p[1] }}</span>{# title #}
    		<div>
        		{% if p[8] %}
            		<img src="{{ url_for('static', filename='images/' + p[8]) }}" alt="post image">
        		{% endif %}
    		</div>
    		<div class="post-info">
        		<span class="post-clubs">{{ p[3] }}</span>  {# clubs #}
        		<span>{{ p[2].title() }}</span> {# content #}
        		<form method="POST" action="{{ url_for('like_post', post_id=p[0]) }}">
          			<button class="like-button" type="submit">
            			<i id="like-icon" class="fa fa-heart-o"></i>
            			<span id="likes">{{ p[4] }}</span>
          			</button>
        		</form>
        		{% if p[5] %}
    				<div class="post-comments">
  						<h4>Comments:</h4>
  						{% for c in comments_dict[p[0]] %}
    						<div class="comment-container">
      							<span class="comment-username">{{ c[1] }}:</span>{# username #}
      							<span class="comment-content">{{ c[0] }}</span>{# content #}
    						</div>
  						{% endfor %}
  					{% endif %}
    			</div>
    			<div>
        			<form method="post" action="/delete_post">
        				<input type="hidden" name="post_id" value="{{p[0]}}">
        				<button type="submit"><span></span>Delete this post</button>
        			</form>
    			</div>
    		</div>
  		</div>
	{% endfor %}
</div>



```

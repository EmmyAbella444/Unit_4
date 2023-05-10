```.html
<!DOCTYPE html>
<html>
<head>
	<title>Home</title>
	<link rel="stylesheet" href="/static/home.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
<div class="container-top">
	<div class="logo">
		<img src="/static/logo (1).png" alt="Logo">
	</div>
	<div class="profile-buttons">
		<div class="logout-button">
			<a href="{{ url_for("logout") }}"><img src="/static/logout.png" alt="Logout Icon"></a>
		</div>
		<div class="profile-button">
			<a href="{{ url_for('profile_user', user_id=user_id) }}"><img src="/static/profile-icon.png" alt="Profile Icon"></a>
		</div>
        <div class="statistics-button">
			<a href="{{ url_for('statistics', user_id=user_id) }}"><img src="/static/statistics.png" alt="Profile Icon"></a>
		</div>
	</div>
</div>
<div class="container-newpost">
	<h2>Add New Post</h2>
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
</div>
<div class="container-posts">
  <h3>Recent Posts from your peers</h3>
  </div>
   {% for p in posts %}
  <div class="post-container">
    <span class="post-username">{{ p[7] }}</span>{# username #}
    <span class="post-datetime">{{ p[6] }}</span>  {# datetime #}
    <span class="post-title">{{ p[1] }}</span>{# title #}
    <div>
        {% if p[9] %}
            <img src="{{ url_for('static', filename='images/' + p[9]) }}" alt="post image">
        {% endif %}
    </div>
    <div class="post-info">
        <span class="post-clubs">{{ p[8] }}</span>  {# clubs #}
        <span>{{ p[2].title() }}</span> {# content #}
        <form method="POST" action="{{ url_for('like_post', post_id=p[0]) }}">
          <button class="like-button" type="submit">
            <i id="like-icon" class="fa fa-heart-o"></i>
            <span id="likes">{{ p[4] }}</span>
          </button>
        </form>
    {% if p[6] %}
    <div class="post-comments">
  <h4>Comments:</h4>
  {% for c in comments_dict[p[0]] %}
    <div class="comment-container">
      <span class="comment-username">{{ c[1] }}:</span>{# username #}
      <span class="comment-content">{{ c[0] }}</span>{# content #}
    </div>
    {% endfor %}

</div>
      <form action="{{ url_for('add_comment', post_id=p[0]) }} "method="POST" >
        <input type="hidden" name="post_id" value="{{ p[0] }}" required >
        <input type="text" name="comment" placeholder="Add a comment..."required>
        <button type="submit">Post</button>
      </form>
    </div>

    {% endif %}
  </div>
{% endfor %}


```

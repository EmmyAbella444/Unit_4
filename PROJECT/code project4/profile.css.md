```.css

/*Top container with logo*/
.container-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #f1c1e7;
  padding: 10px 20px;
}
/*background*/
body {
  background-color: #f5efef;
  font-family: Arial, sans-serif;
  margin: 0;
}

.container-profile {
  max-width: 450px;
  margin: 10px 10px 10px auto;
  padding: 20px;
  background-color: #ffffff;
  overflow-x: auto;
  horiz-align: right;
  float: left;
    border: 1px solid rgb(84, 83, 83);
    margin-left: 10px;

}
h2 {
  font-size: 24px;
  margin-bottom: 10px;
}

p {
  font-size: 16px;
  margin-bottom: 5px;
}

.alert {
  background-color: #ffc107;
  color: #fff;
  padding: 10px;
  margin-top: 20px;
  font-size: 14px;
  text-align: center;
}
/*all post title*/

h3 {
  color: rgba(0, 0, 0, 0.98);
    background-color: #f1c1e7;
  font-family: "Helvetica Neue", sans-serif;
  font-weight: 500;
  font-size: 1.3em;
  text-align: center;
  float: right;
    border-radius: 10px;
    padding: 15px;
    margin-right: 130px;
}
/*all post title*/
.container-posts {
  display: flex;
  flex-direction: column;
  align-items:center;
}

.post-container {
  margin: 10px auto;
  margin-right: 260px;
  width: 550px;
  background-color: #ffffff;
  border: 1px solid rgba(26, 25, 25, 0.98);
  font-family: Arial, sans-serif;
  border-radius: 29px;
    align-items:center;
      margin-bottom: 20px;

}


.post-container img {
  max-width: 80%;
    horiz-align: center;
    margin-left: 50px;
}

.post-username {
  display: block;
  font-weight: bold;
  margin: 10px;
  font-size:medium;
}

.post-datetime {
  display: block;
  margin: 10px;
  color: #999;
  font-size: 12px;
}

.post-title {
  display: block;
  font-weight: bold;
  font-size: large;
  margin: 10px;
    margin-left: 220px;
}

.post-info {
  padding: 10px;
}

.post-clubs {
  display: block;
  margin: 10px;
  color: #999;
  font-size: 12px;

}
.comment {
  margin: 10px;
  padding: 5px;
  border: 1px solid #ccc;
  background-color: #f5f5f5;
}

.comment p:first-child {
  font-weight: bold;
  font-size: medium;
  margin-bottom: 5px;
}

.comment p:last-child {
  font-size: 7px;
  font-size: medium;
  color: #999;
}


/*Form for submit new post and comment*/
input[type=text], textarea {
  width: 90%;
  padding: 10px;
  border: 1px solid #dbdbdb;
  border-radius: 3px;
  resize: vertical;
  font-size: 14px;
  right: 50px;
}

/*Submit button yo add new post*/
input[type=submit] {
  background-color: #a300c7;
  color: #fff;
  padding: 8px 16px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-size: 14px;
}

/*Buttons log out and profile*/
.logout-button, .profile-button,.statistics-button {
  display: inline-block;
  padding: 4px 8px;
  background-color: #a300c7;
  color: #fff;
  border-radius: 3px;
  text-decoration: none;
  font-size: 14px;
  margin-left: 10px;

}

.logout-button img, .profile-button img,.statistics-button img, .delete-button {
  height: 20px;
  width: 25px;
  margin-right: 6px;
}

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

@keyframes move_wave {
    0% {
        transform: translateX(0) translateZ(0) scaleY(1)
    }
    50% {
        transform: translateX(-25%) translateZ(0) scaleY(0.55)
    }
    100% {
        transform: translateX(-50%) translateZ(0) scaleY(1)
    }
}
.waveWrapper {
    overflow: hidden;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    top: 0;
    margin: auto;
}
.waveWrapperInner {
    position: absolute;
    width: 100%;
    overflow: hidden;
    height: 100%;
    bottom: -1px;
    background-image: linear-gradient(to top, #faaaea 20%, #ffffff 80%);
}
.bgTop {
    z-index: 15;
    opacity: 0.5;
}
.bgMiddle {
    z-index: 10;
    opacity: 0.75;
}
.bgBottom {
    z-index: 5;
}
.wave {
    position: absolute;
    left: 0;
    width: 200%;
    height: 100%;
    background-repeat: repeat no-repeat;
    background-position: 0 bottom;
    transform-origin: center bottom;
}
.waveTop {
    background-size: 50% 100px;
}
.waveAnimation .waveTop {
  animation: move-wave 3s;
   -webkit-animation: move-wave 3s;
   -webkit-animation-delay: 1s;
   animation-delay: 1s;
}
.waveMiddle {
    background-size: 50% 120px;
}
.waveAnimation .waveMiddle {
    animation: move_wave 10s linear infinite;
}
.waveBottom {
    background-size: 50% 100px;
}
.waveAnimation .waveBottom {
    animation: move_wave 15s linear infinite;
}
body {
  position: relative;
  z-index: 0;
}

.waveWrapper {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  z-index: -1;
}

.container-top,
.container-search,
.container-newpost,
.container-posts {
  position: relative;
  z-index: 1;
}

```

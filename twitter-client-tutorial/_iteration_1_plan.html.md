# Planning the app

The first thing an app developer does before he starts building the app is to plan it. The first step is to create [mockups](http://en.wikipedia.org/wiki/Mockup#Software_Engineering). But since we are replicating an already existing app, we know how it will look. So we can bypass the mockup creation step.

A good way to start is by building the app skeleton (just the user interface). 

* The first time you open a Twitter app, it shows the login screen. So we will build the interface for it first.
<br/>
<%= image_tag "twitter-client/login-screenshot.png", alt: "Login Screenshot", title: "Login Screenshot" %>
<p class="ac">Login Interface Screenshot</p>
<br/>

* Once logged in, we see the list of tweets of the users we follow, so we will build it next. There are multiple tabs like 'mentions', 'direct messages', 'profile' etc. but let's not worry about them in our first iteration.
<br/>
<%= image_tag "twitter-client/twitter-list-screenshot.png", alt: "Twitter List Screenshot", title: "Twitter List Screenshot" %>
<p class="ac">Twitter List Screenshot</p>
<br/>

* Clicking on a tweet shows up the details of that particular tweet. So we will build this feature after building the tweet list view described above.
<br/>
<%= image_tag "twitter-client/twitter-details-screenshot.png", alt: "Twitter Detail Screenshot", title: "Twitter Detail Screenshot" %>
<p class="ac">Twitter Detail Screenshot</p>
<br/>

<p class="ac"><%= link_to "Next Lesson", app_tutorial_lesson_with_token_path(@app_name, AppLesson.find_by_number(@current_lesson.number + 1).lesson.token), class: "btn btn-danger" %></p>

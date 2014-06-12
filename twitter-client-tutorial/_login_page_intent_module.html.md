
In the last module, you implemented **Click Listener** on login page button which simply updated the button text. Ideally it should open a new screen which provides us the list of tweets.

In this module, we are going to create a new Activity - TweetListActivity (we are going to build it too). This Activity will get launched when the user clicks the login button. 

<div style="clear:both"></div>
<div class="row-fluid">
	<div class="span5">
		<div class="ac vertical-align-me">
			<%= image_tag "twitter-client/login-screenshot.png", alt: "Login Screenshot", title: "Login Screenshot" %>
		</div>
	</div>
	<div class="span2">
		<div class="ac vertical-align-me">
			<%= image_tag "twitter-client/from-to.jpg", alt: "Login Screenshot", title: "Login Screenshot" %>
		</div>
	</div>
	<div class="span5">
		<div class="ac vertical-align-me">
			<%= image_tag "twitter-client/twitter-list-screenshot.png", alt: "Twitter Detail Screenshot", title: "Twitter Detail Screenshot" %>
		</div>
	</div>
</div>


You will learn how you can load a new Activity on the button click using **Intents**. Intent is the Android way of launching new Activity & even external apps from inside of an Android app. Usually Intent gets fired from button click, List item click or some other user interaction mechanism. 

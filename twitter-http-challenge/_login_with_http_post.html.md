## The app so far

> Update: If you were using HttpUrlConnection, our tests will eventually fail because of it. You need to use only DefaultHttpClient or AndroidHttpClient for HTTP calls

If you have completed the setup, you should have a dummy Twitter app, **CodelearnTwitterChallenge**, imported in your Eclipse. The app has three screens as shown below

<div class="row-fluid">
	<div class="span4">
		<div class="vertical-align-me">
			<%= image_tag "twitter-client/login-screenshot.png" %>
			<p class="ac">MainActivity.java</p>
		</div>
	</div>
	<div class="span4">
		<%= image_tag "twitter-client/twitter-list-screenshot.png" %>
		<p class="ac">TweetListActivity.java</p>
	</div>
	<div class="span4">
		<%= image_tag "twitter-client/twitter-details-screenshot.png" %>
		<p class="ac">TweetDetailActivity.java</p>
	</div>
</div>

The app has MainActivity as the Login screen. The EditTexts for username and password are dummy. The control would simply proceeds to the next screen regardless of the credentials entered by the user. A real Twitter app would send the data to an [API](https://en.wikipedia.org/wiki/Application_programming_interface) and decide its action based on the response.

##Setting up the login mechanism using an HTTP POST call

In this level, your task is to send the username and password data to the Codelearn Test API in the form of a JSON request object, handle the response and control the flow of the app to **TweetListActivity**


###API
The Codelearn Twitter API endpoint for login is available at

<pre>
http://app-dev-challenge-endpoint.herokuapp.com/login
</pre>

###Request
The JSON request object for the HTTP **POST** request can be as follows.
<pre>
{
"username" : "abcdefg",
"password" : "secret-password"
}
</pre>

Note that the field names must be **username** and **password**

###Response
The API will provide you a token as a JSON response

<pre>
{
"token" : "37dgdu37ehbdhyd73cccdh"
}
</pre>

###Tasks
* Modify the app to send the user data to the API endpoint when the user clicks the login button using an HTTP POST call.
* Once you receive a successful response, store the received token in SharedPreference, specifying the name of the preference file as **codelearn_twitter**
* Modify the app to skip showing the login screen when the token is already available in SharedPreference.

###Restrictions
* You must use either **AndroidHttpClient** or **DefaultHttpClient** library to do network call. Any other libraries are not supported.
* For JSON parsing, you can use **GSON** & **Jackson** libraries only
* The received token must be stored in a SharedPreference file named "codelearn_twitter"

Once you are done, run the app as **Android App Codelearn** & if you got the solution right, you will get a success popup that will take you the next level. All the best.

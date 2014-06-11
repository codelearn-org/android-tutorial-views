
We have built a Twitter app with three screens so far. It is just the User Interface. As we mentioned earlier, the first step of app development is to design the interface. We could add more screens, but let's just stick to the three screens - Login, Tweet List & Tweet Detail - that we have built & focus on handling data, storing it locally & updating it as & when needed. 

<div class="well pull-right" style="margin:5px; width:40%; font-size:small">
	<h3>Module Summary</h3>
	<ol>
		<li>Store login data locally & tweak the logic to not show the login screen again on app load</li>
		<li>Store tweets locally & show them as soon as Tweet List screen comes up.</li>
		<li>Modify Tweet List Activity & XML code to show data from locally stored tweets.</li>
		<li>Modify Intent & Tweet Detail Activity to show data of the individual tweet which is clicked.</li>
		<li>Hook up some methods which will simulate network calls & update locally stored tweets.</li>
	</ol>
	<div class="ac">
		<%= link_to @next_url, class: "btn btn-large btn-success" do %>
			<h3>Get Started</h3>
		<% end %>
	</div>
</div>

**Storing small data in Shared Preference**

Mobile web has some form of local data storage like cookies but they are only limited to handling user authentication data. If you log in once on a site, you do not have to login again on next visit. The data is stored in your browser & sent to the server on every request. Likewise, Android apps have **[Shared Preference]()** which can be used to store key value pair kind of small data. 

**Creating data model for bigger data & storing it in a file**

Also, we need to store the tweets locally. This is needed for better user experience. Unlike opening twitter on web browser, where the screen is blank initially & it takes time for data to load, twitter mobile client shows old tweets as soon as the app loads. This is possible as the tweets are locally stored. When the tweet list Activity is opened, the old tweets are rendered instantly. 

**Updating data through AsyncTask**

When the Tweet List Screen is opened, a network call is initiated in parallel which updates the local tweet data & refreshes the Activity to show the new tweets. This is achieved through **[AsyncTask]()** . AsyncTask lets you run a piece of code asynchronously. It is like running a piece of code in parallel which does not affect the Activity code flow. AsyncTask is normally used to perform tasks that are time-consuming, like network calls, sending sms/email etc which are essentially *one off time taking jobs*. 

**Modifying Activity & Intent code to show & pass variable data**

So far, we have shown just the dummy data on Tweet List & Tweet Detail Activity screens. We are now going to read from the locally stored tweet data. We need to show the data on the Tweet List Activity. We are going to change the java code for that. Also, the tweet data need to be passed from Tweet List Activity to Tweet Detail Activity through Intent. We are going to modify that part as well. 

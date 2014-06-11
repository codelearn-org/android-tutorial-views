
##Recap from module 1

In module 1, each tweet item had dummy data and its appearance was based on row_tweet.xml. We also created a TweetListAdapter with a `getView()` method which simply inflated the resource xml

`TweetAdapter.java`

	public class TweetAdapter extends ArrayAdapter {
		.
		.     
		 @Override
		 public View getView(int position, View convertView, ViewGroup parent){
			 return inflater.inflate(R.layout.row_tweet, parent, false);
		 }

	}

Because of the above step, all tweet items looked the same. In real life, each tweet item will hold a different value that comes from the twitter server. Since we are not doing network calls yet, we will populate some dummy but different data. 

The steps we are going to follow :-

**1. New Tweet model to hold data ** 

Good programming practice in Java mandates that any kind of data should be held in a Class. It is also referred as Model of Model View Controller architecture. Consider the Activity classes as Controllers & XML as Views. We will create a new class Tweet.java which will hold the tweet data.

**2. Populating the Tweet model **

In a real Twitter app, data would be fetched from the network. Since we are not doing network call here, we are just going to put some dummy data in our Tweet model. 

**3. Using Tweet model to show data on screen **

We are then going to pass the tweet model array to TweetAdapter & change the code to use the model data to show on the screen. 

## Creating Tweet Model

When we will do network calls to fetch tweets, all the tweets will have uniform structure. Each tweet will have an image, twitter handle, body, date etc. In Java, it is a good practice to create a Java class for this. Such an object is also known as **P**lain **O**ld **J**ava **O**bject (POJO) in Java. We can store multiple tweets as array of the Tweet object.


### Assignment - create Tweet model

** 1. Create Tweet.java **

The file needs to be in src -> org -> codelearn -> twitter -> models directory. You can either manually create it or follow the Eclipse steps below.

* Create new folder

<div class="row-fluid">
	<div class="span6">
		<%= image_tag "twitter-client/new-folder-src.png" %>
	</div>
	<div class="span6">
		<%= image_tag "twitter-client/create-folder-src.png" %>
	</div>
</div>

* Create Tweet.java inside org.codelearn.twitter.models

<div class="row-fluid">
	<div class="span6">
		<%= image_tag "twitter-client/new-class-folder-src.png" %>
	</div>
	<div class="span6">
		<%= image_tag "twitter-client/create-class-folder-src.png" %>
	</div>
</div>

* This is how the newly created Tweet.java will look

<%= image_tag "twitter-client/tweet.java.png" %>

**2. Create Tweet.java PoJo **

If you do not know what PoJos are, read about it [here](http://stackoverflow.com/questions/11722251/what-is-pojo-dojo-in-java)

For now, we are just going to have **id** (String), **title** (String) & **body** (String) fields in the Tweet model. You need to create a PoJo that lets you retrieve & set these fields. 

Create `getTitle()`, `setTitle()`, `getBody()`, `setBody()` & `getId()` functions in the PoJo that will get/set the appropriate fields. 

You should run your app & we are going to test if Tweet.java is present at org.codelearn.twitter.models & has appropriate functions & fields. **Make sure you keep the name of the file, location & fields exactly same as specified.**

# Serializing & writing to local file

** Writing to a local file **

Android lets you create local files - You can give it any name as you please. Writing to a file is a pretty straightforward process with the `FileOutputStream` object returned by `openFileOutput()`. 

	String FILENAME = "hello_file";
	String string = "hello world!";

	FileOutputStream fos = openFileOutput(FILENAME, MODE_PRIVATE);
	fos.write(string.getBytes());
	fos.close();

`MODE_PRIVATE` creates the file private to the Activity's context. It will be private to your application.

** Writing OBJECTS to local file **

In our case, we are going to dump an array of objects. We need `ObjectOutputStream` class for that. It automatically takes care of serializing the data before writing to the file. But before that, we need to ensure that Tweet class is serializable. The class declaration needs to implement Serializable

<pre>public class Tweet <span class="highlight">implements Serializable</span></pre>

Dont forget to `import java.io.Serializable` inside Tweet.java .

Also, just to be sure that Java doesn't run into trouble serializing and de-serializing objects of this class, it's generally a good idea to add a default serialization version UID member to the Tweet class.

    private static final long serialVersionUID = 1L;

The sample code now looks like as below.

<pre>
	FileOutputStream fos = openFileOutput(FILENAME, MODE_PRIVATE);
	<span class="highlight">ObjectOutputStream oos = new ObjectOutputStream(fos);
	oos.writeObject(tweets);
	oos.close();</span>
	fos.close();
</pre>

## Assignment - write dummy tweets to a local file

Put the above learning to use & modify TweetListActivity.java code to dump tweets array to a local file before it is passed to TweetAdapter & shown on the screen. 

As a good practice, you should put the name of the file in a private static final variable 

<pre>private static final String TWEETS_CACHE_FILE = "tweet_cache.ser";</pre>

Since it is serialized tweets, we hae put a **.ser** extension. You are free to put any extension that you like to. In your code, you should use TWEETS_CACHE_FILE variable to reference the tweets cached file. 

<div class="alert alert-danger">Make sure that you keep the name of the file as <b>tweet_cache.ser</b>. Otherwise, our tests will not be able to check if you are actually writing tweets to a file.</div>

Also note, to use `openFileOutput()` & `ObjectOutputStream()` you need to handle multiple exceptions. You need to put a try-catch block around your statements. Also, to check if you have successfully written to the file, you should use Log .

      try {
	  	//code to write into file
		Log.d("codelearn", "Successfully wrote tweets to the file.");
		//close operators
	  } catch (Exception e) {
	    Log.e("codelearn", "Error writing tweets", e);
	  }
		

After you write the objects into the file, check the LogCat output for "Successfully wrote tweets to the file." as shown in the below screenshot.

<%= image_tag "twitter-client/logcat-successfully-written-file.png" %>

Don't expect any change in the app behavior - You will still see the same list of tweets. However, depending on your phone's processing power, there may be a marginal delay in the appearance of the screen while the tweets are written to the file. In future lessons, we are going to move this bit to a asynchronous process to remove the delay.

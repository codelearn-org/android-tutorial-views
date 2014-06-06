##Connecting to the real Twitter API using Twitter4J library

So far, the challenge involved the usage of the Codelearn Twitter API, which provides dummy content. In this level, your task is to include [Twitter4J](http://twitter4j.org/en/index.html), a popular library for Java and Android, that simplifies the use of Twitter API, and replace the existing network calls with the ones provided by Twitter4J.

###API, Request and Response

Refer to the [Javadoc](http://twitter4j.org/en/javadoc.html) and [code examples](http://twitter4j.org/en/code-examples.html) provided by Twitter4J.

For using Twitter4J library, you need to register an app at [http://dev.twitter.com/apps](http://dev.twitter.com/apps). For your convenience, we have created an app & you can use the API key & secret (reproduced below). It is a good practice to create a separate class `TwitterConstants.java` and define these as static variables to be used in your app

     public static String CONSUMER_KEY = "pC3D9eMxb8pXNAPhBHAQFYLoS";
     public static String CONSUMER_SECRET = "8qhOLjLHiqLQJLLQUnBNSlnUoFtbLHjWQlnaxS5W3n6NkkUeOi";

    
### Tasks

1)  Modify MainActivity.java to have only one 'Sign in with Twitter' button . Remove the LinearLayouts containing username & password fields. Hook up the button with Twitter4J so that the user gets redirected to Twitter for authentication.

2) Our tests will not be able to access the webView & fill in the data once user gets redirected to Twitter. Our tests will be using @DroidChallenge user oAuth token to test your app. We need to mandate that you should store the token details in your app in **codelearn_twitter** SharedPreference with key **key_acc_token** for the token & **key_acc_token_secret** for the secret. We are simply going to write @DroidChallenge token values to these keys in the SharedPreference to test your app on our server.

**P.S. - We will not get your twitter account token details this way & the app will not post as you when run on our server. Just pause & think for a minute if you are still in doubt.**

It is a good practice to store these names in TwitterConstants.java

`TwitterConstants.java`

	public static final String SHARED_PREFERENCE = "codelearn_twitter";
	public static final String PREF_KEY_TOKEN = "key_acc_token";
	public static final String PREF_KEY_SECRET = "key_acc_token_secret"; 

& use it where it is required 

`MainActivity.java`

	prefs = getSharedPreferences(TwitterConstants.SHARED_PREFERENCE, MODE_PRIVATE);
	Editor editor = prefs.edit();
	editor.putString(TwitterConstants.PREF_KEY_TOKEN, accessToken.getToken());
	editor.putString(TwitterConstants.PREF_KEY_SECRET, accessToken.getTokenSecret());

2) Once the user gets authenticated with Twitter, he should automatically go to TweetListActivity where he can see his tweets. Modify the logic so that **only new tweets are fetched & appended to the tweet list**.

3) Create a new Activity **ComposeTweetActivity** to compose a tweet. Make sure to keep the name exactly the same, also the Activity should extend normal Activity & not ActionBarActivity. A corresponding layout file **activity_compose_tweet.xml** will get generated. Replace the content of the file with the content below


	<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
	    xmlns:tools="http://schemas.android.com/tools"
	    android:layout_width="match_parent"
	    android:layout_height="match_parent"
	    android:paddingBottom="@dimen/activity_vertical_margin"
	    android:paddingLeft="@dimen/activity_horizontal_margin"
	    android:paddingRight="@dimen/activity_horizontal_margin"
	    android:paddingTop="@dimen/activity_vertical_margin" >

	    <EditText
		android:id="@+id/fld_compose"
		android:layout_width="match_parent"
		android:layout_height="wrap_content"
		android:layout_marginLeft="5dp"
		android:layout_marginRight="5dp"
		android:layout_marginTop="15dp"
		android:hint="@string/hint_new_tweet"
		android:lines="5" />

	    <TextView
		android:id="@+id/char_count"
		android:layout_width="wrap_content"
		android:layout_height="wrap_content"
		android:layout_alignLeft="@id/fld_compose"
		android:layout_alignRight="@id/fld_compose"
		android:layout_below="@id/fld_compose"
		android:gravity="right" />

	    <Button
		android:id="@+id/btn_submit"
		android:layout_width="290dp"
		android:layout_height="wrap_content"
		android:layout_below="@id/char_count"
		android:layout_centerHorizontal="true"
		android:layout_marginTop="15dp"
		android:gravity="center"
		android:text="@string/lbl_submit"
		android:textSize="13sp"
		android:textStyle="bold" />

	</RelativeLayout>

  
  **Add the logic to post the tweet on button click.**

4) Add a menu item on TweetListActivity to take user to **ComposeTweetActivity**. Overall, there should only be two menu items - the first for Refresh of tweets, the second one for compose tweet. 

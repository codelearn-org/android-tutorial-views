
In the previous lesson, we implemented click listener for each tweet. Ideally, clicking on a tweet should show the tweet detail screen. In this lesson, we will be creating new Activity TweetDetailActivity & show the Activity on click of tweet item through intent. 

Let's get started

* Create new Activity. Right click on 'CodelearnTwitterApp' in the left pane package explorer window. New -> Other -> Android -> New Activity -> Blank Activity. Activity Name - TweetDetailActivity. It will auto-populate Layout Name as activity_tweet_detail which is fine. Hit on 'Finish'.

<div class="alert alert-info"><strong>Tip</strong>: You can also use <strong>Ctrl+N</strong> and start typing <strong>Activity</strong> to create a new Activity</div>

* The layout of the Tweet Detail screen should be as below

<%= image_tag "twitter-client/tweet-detail-layout-breakdown.png", alt: "Tweet Detail Layout Breakdown", title: "Tweet Detail Layout Breakdown" %>

* We've created a similar layout in row_tweet.xml . So this time, you can simply copy paste the below xml in activity_tweet_detail.xml. Remove all the other existing XML from the file before you add the below XML. 

`activity_tweet_detail.xml`

       <?xml version="1.0" encoding="utf-8"?>
       <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
           android:layout_width="match_parent"
           android:layout_height="match_parent"
           android:background="#b2b2b2"
           android:gravity="center"
           android:orientation="vertical" >
           
           <ImageView
               android:id="@+id/tweetImage"
               android:layout_width="100dp"
               android:layout_height="100dp"
               android:background="@drawable/user_profile"
               android:layout_gravity="center_horizontal" />
           
       	<LinearLayout 
       	    android:layout_width="match_parent"
       	    android:layout_height="wrap_content"
       	    android:orientation="vertical"
       	    android:layout_marginLeft="5dp"
       	    android:layout_marginRight="5dp"
       	    android:layout_marginTop="10dp"
       	    android:background="#fff"
       	    android:padding="10dp" >

       	        <TextView
       	            android:id="@+id/tweetTitle"
       	            android:layout_width="match_parent"
       	            android:layout_height="wrap_content"
       	            android:text="Header Text"
       	            android:textColor="#181717"
       	            android:textSize="19sp"
       	            android:textStyle="bold" />
       	        <TextView
       	            android:id="@+id/tweetBody"
       	            android:layout_width="match_parent"
       	            android:layout_height="wrap_content"
       	            android:layout_gravity="center_vertical"
       	            android:layout_marginTop="5dp"
       	            android:text="Tweet body text"
       	            android:textColor="#393939"
       	            android:textSize="14sp" />
       	        <TextView
       	            android:id="@+id/tweetDate"
       	            android:layout_width="match_parent"
       	            android:layout_height="wrap_content"
       	            android:layout_gravity="center_vertical"
       	            android:layout_marginTop="5dp"
       	            android:text="21st November, 2013"
       	            android:textColor="#615f5f"
       	            android:textSize="12sp" />
       	  </LinearLayout>
   
           
       
     </LinearLayout>




* Hook up TweetDetailActivity to each tweet item click through onListItemClick() method of TweetListActivity.

`TweetListActivity.java`
<pre>
.
.
@Override
 protected void onListItemClick(ListView l, View v, int position, long id) {
     <strike>TextView t = (TextView) v.findViewById(R.id.tweetTitle);
     t.setText("Tweet Clicked");</strike>
	 <span class="highlight">Intent intent = new Intent(this, TweetDetailActivity.class);
	 startActivity(intent);</span>
 }
 .
 .
</pre>

Deploy the app. Navigate past login. Click on any tweet to view the brand new Activity and layout we just created. 

This concludes the first iteration of our app where we have built some nicely arranged dummy screens. In the next iteration, we are going to capture user data in the login screen & store them locally in a file. We store data locally for better user experience like not showing the login detail again when the app is launched in case the user has already put in his login details. Also, the tweets are supposed to be fetched over the network. But storing last fetched tweets locally will instantaneously show the user some tweets while the fetching goes in the background asynchronously. 

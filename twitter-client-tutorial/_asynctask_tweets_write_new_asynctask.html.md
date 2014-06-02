# Moving writing of tweets to new AsyncTask

As mentioned earlier, reading & writing from files are slightly elaborate tasks & should be done in a separate thread to avoid affecting the main Activity flow. 

In this case, the primary purpose of AsyncFetchTweets is to fetch tweets & show them to the user. It is a good idea to move the code to write the tweets to the cache file into a separate AsyncTask outside AsyncFetchTweets.

## Assignment - write tweets to cached file in new AsyncTask

Since writing tweets to the cache file could potentially take quite some time, let's simulate it by adding a 5 second delay. We will undo this change later. 

* Introduce a 5 sec delay in AsyncFetchTweets in **doInBackground()** 

`AsyncFetchTweets.java`
<pre>
    protected void doInBackground(..) {
	  //5 sec sleep to simulate delay in fetching tweets
	  //dummy tweet creation
	  <span class="highlight">//5 sec sleep to simulate delay in writing to file</span>
	  //writing tweets to file
	}

    protected void onPostExecute(..) {
	//call to renderTweets()
    } 
</pre>

Remove the app from your phone & re-deploy. **You will see 10 seconds delay before the tweets show up.**

* Create a new class **AsyncWriteTweets** extending AsyncTask . Move the code to write to file & 5 sec sleep into the class.

`AsyncFetchTweets.java`
<pre>
    protected void doInBackground(..) {
	  //5 sec sleep to simulate delay in fetching tweets
	  //dummy tweet creation
	  <span class="highlight"><strike>//5 sec sleep to simulate delay in writing to file
	  //writing tweets to file</strike>
	  new AsyncWriteTweets(TweetListActivity object).execute(tweets);</span>
	}

    protected void onPostExecute(..) {
	//call to renderTweets()
    }
</pre>

<!--`AsyncWriteTweets.java`
<pre>
   protected void doInBackground(..) {
      <span class="highlight">//5 sec sleep
	  //writing tweets to file</span>
   }
</pre>-->

`AsynchWriteTweets.java`
<pre>
TweetListActivity test=null;
	public AsynchWriteTweets(<span class="highlight">TweetListActivity act</span>){
	 <span class="highlight">test=act;</span>
	}
	//use test object to write tweets into "tweets_cache.ser"
</pre>
Remove the app on the phone & deploy again. This time, the tweet list will show up in **5 seconds** straight
<div class="alert alert-warning">Make sure you keep the name of the class as <b>AsyncWriteTweets</b> and the constructor as shown in above code snippet. Otherwise, our tests will fail & we won't know if you have completed the assignment correctly</div>. 

* Once done, you should **remove the additional 5 sec delay from AsyncWriteTweets**.

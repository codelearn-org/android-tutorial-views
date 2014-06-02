# Show tweets after AsyncTask

The AsyncTask we created in previous lesson is simply simulating a network call to fetch new tweets. In case of an actual network call, new tweets will be fetched and we should update the tweet list screen to show them.

At first, the obvious thing to do is to call parent (TweetListActivity) methods at the end of **doInBackground()** method. But it will result in an error as you can not update View elements from a background thread. We are going to use `onPostExecute(..)` method to do the job. 

Once the background task is over, it can pass data to a member method `onPostExecute(result)`. The data passed **result** is object of type *Result*. Note **doInBackground()** should also have return data type as *Result*

<pre>
 private class MyAsyncClass extends AsyncTask&lt;<i>Params</i>,<i>Progress</i>,<i>Result</i>&gt; {

    protected <span class="highlight"><i>Result</i></span> doInBackground(<i>Params</i>... params) {
	  <span class="highlight"><i>Result</i> result;</i></span>
	  //do background job & populate result
	  <span class="highlight">return result;</span>
	}

	<span class="highlight">protected void onPostExecute(<i>Result</i> result) {
	  //pass result to main UI thread to show the final data
	}</span>
 }
</pre>



## Assignment - update tweets on UI screen from AsyncTask

We are going to call the tweet list update steps twice - once from inside onCreate() in TweetListActivity & again from AsyncFetchTweets. To keep our code DRY (don't repeat yourself), we should NOT be writing the code to show the tweets twice. Rather, we should simply put it in a method & call the same method from two places.

`TweetListActivity.java`
<pre>
   <span class="highlight">public void renderTweets(..) {
     //code to show tweets 
   }</span>

   protected onCreate(..) {
     //call AsyncFetchTweets
	 <span class="highlight"><strike>Remove the code to show tweets</strike>
	 renderTweets(..)</span>
   }
</pre>

You need to invoke renderTweets(..) from inside of AsyncFetchTweets as well. You should invoke it from inside onPostExecute() method.

<div class="alert alert-info"><b>Hint</b>: You already have a reference to TweetListActivity, passed as <b>parent</b> to the AsyncFetchTweets constructor. You can invoke renderTweets() as <b>parent.renderTweets()</b></div>

To test that your code works, uninstall and reinstall the app - A list of tweets should show up even on the first load of your app after a 5 second delay.

<div class="alert alert-warning">Uninstalling the app (or clearing the cache under app settings) is necessary before you go ahead & deploy the new app. Otherwise, the cached file from a previous load will be present</div>

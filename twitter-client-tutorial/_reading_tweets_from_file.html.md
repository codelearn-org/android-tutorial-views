
There are only three lines that are different while reading from a local file as against writing. 

<pre>
FileInputStream fis = openFileInput(<i>Name of the file</i>);
ObjectInputStream ois = new ObjectInputStream(fis);
tweets = ( List&lt;Tweet&gt; ) ois.readObject();
</pre>

As with writing, you DO NOT have to unserialize the data from the file to be stored in the tweets array. It happens automatically.

While serializing objects seems to be a relatively simple set of operations, bear in mind that you need to follow certain guidelines to make the best use of it —

* **Close open streams** Remember to close() all streams that you open for reading and writing. A better implementation is to use `finally()` block with try-catch to make sure you are closing files even in case of errors.

<pre>
    try {
		// open files
		// perform operations
	} catch (Exception e){
	   //log exceptions (at least)
	}<span class="highlight">finally {
	   try {
		//close file handles 
	   } catch (Exception e) {} 
	   //there can be errors while closing the file handles if it was'nt opened at the first place.
	   //but we do not really need to catch it. Hence nothing inside catch.
	}</span>
</pre>

* **Keep an eye on data size** Be sure that size of the object you're serializing isn't very large, because when an attempt to deserialize the data is made, the app might easily run out of memory and throw an OutOfMemory error.

### Assignment - read tweets from cached file

As we discussed earlier, going ahead, the main Activity thread will be responsible to read tweets from file & show on the screen. A separate parallel thread does network call, gets new tweets, shows it on the screen & eventually overwrites the file. 

**Assignment Steps** Let us replicate the flow, although sub-optimally. Change the TweetListActivity logic as shown below. 

1. The first step is to read the tweets from cached file. Store it in an array `tweetsRead`. 
2. Next is to generate the dummy tweets & store it in a separate array `tweetsWrite`. 
3. Write tweetsWrite to the cache file. 
4. Use tweetsRead to show the output on the screen.

Your code should look as below after the changes

`TweetListActivity.java`

<pre>
protected onCreate(..) {
  //tweetsRead = read tweets from cache file
  //tweetsWrite = create dummy tweets
  //write tweetsWrite to cache file
  //use tweetsRead to show output on the screen
}
</pre>

**How to test**

* Uninstall the app if you are using your phone. If using AVD, restart it. This is to ensure the cached file is deleted. 
* The first time you deploy the app, the Tweet List screen will be empty. You will see an error in LogCat because the cached file has not been created yet.

<%= image_tag "twitter-client/read-tweets-error.png" %>

* On subsequent visits to Tweet list screen, you will always see the tweets. 

This is how it will be in the actual app as well. The first time the app loads after installation, there are no tweets. From the next load, there will always be tweets in the file. Going ahead, we are going to move tweet generation & writing part (steps 2 & 3) into a separate thread. The reading tweet & showing it on screen (steps 1 & 4) will stay in the main Activity thread. 

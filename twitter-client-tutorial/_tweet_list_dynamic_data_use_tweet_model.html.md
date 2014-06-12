
In the previous lesson, we created a Tweet Model. In this lesson, we are going to populate it with dummy data & then use its content to show up on TweetListActivity. 

## Step 1 - Array of tweets initialization 

We will be holding a lot of tweets at a given time. So we need an array of Tweet model objects. 

	List<Tweet> tweets = new ArrayList<Tweet>();

While `List` is a generic array class in java (also called interface), `ArrayList` is simply an array implementation of List interface. Putting a `<Tweet>` typecasts it to an array of our Tweet class.

## Step 2 - Populating the array 

Presently, we create random data inside getView() when the user visits the TweetListActivity. Since we've created a new Tweet model, we will iterate over the Tweet objects, get each element's value like header, date, body etc & set the appropriate field in the inflated View. 

We don't have any tweets yet, so `tweets` will be empty. You can populate it with the code snippet below.

    for ( int i = 0; i < 20; i++ ) {
		Tweet tweet = new Tweet();
		tweet.setTitle("A nice header for Tweet # " +i);
		tweet.setBody("Some random body text for the tweet # " +i);
		tweets.add(tweet);
	}

The code above will put 20 Tweet objects in `tweets` array. We are using **setTitle()** and **setBody()** functions that we created in Tweet model in the previous lesson.

## Step 3 - Populating ListView with tweets array

Now that we have populated the tweets array, we need to show the data it holds on the ListView. 

A quick recap. Data is passed to the ListView through an Adapter. We had the below code in TweetListActivity.java .

<pre>tweetItemArrayAdapter = new TweetAdapter(this, new String[10]);</pre>

We were not actually passing any data to the Adapter. Just the size of the String array is used by the Adapter to create 10 tweet entries. Now we will be passing `tweets` array to TweetAdapter which will in-turn be used in getView() method to set the title, body & date in inflated View.

We also need to modify **getView()** method to use the tweets array. The method `getView()` returns an object of type View. Before returning the View, the content of the inflated View can be modified by accessing elements of the View using `findViewById()` method and setting the text using `setText(..)`. 


### Assignment

**step 1 ** 
Implement step 1 to instantiate array of tweets. You should have it as private class member in TweetListActivity as you would be needing the variable across the functions of class TweetListActivity. 

Make sure you add the appropriate import statement

     import org.codelearn.twitter.models.Tweet 

in TweetListActivity.java. Otherwise, Eclipse will not be able to understand that 'Tweet' actually stands for the Tweet class defined elsewhere.

**step 2 **
Initialize tweets array with dummy data as in step 2. Figure out the right place you should be initializing it.


**step 3**
Make tweets array created from step 2 accessible inside TweetAdapter's getView() function . 

Hint 1 - You should pass the array while initializing TweetAdapter in TweetListActivity. The variable becomes available inside constructor of TweetAdapter which you should store locally in TweetAdapter to be used in getView(..)

Hint 2 - TweetAdapter need to extend `ArrayAdapter<Tweet>` to be able to accept array of tweets as argument in the constructor.

Hint 3 - Inside getView(..), you should use `position` variable to get the appropriate Tweet object from the tweeets array

Once done, the app will look as below

<%= image_tag "twitter-client/different-tweets.png" %>

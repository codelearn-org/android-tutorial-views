# Passing data over Intent to Tweet Detail Screen

Each tweet item shows different tweet data. But clicking on a tweet item still shows the same old **activity_tweet_detail.xml** with the data hardcoded in the XML. 

<%= image_tag "twitter-client/tweet-list-tweet-detail-hardcoded.png" %>

In this lesson, we will learn how to pass data from one screen to another over Intent. We will be going to pass the Tweet model object associated with the tweet to the Tweet Detail Screen. It will use the data from the object to populate in the Tweet Detail XML view. 

<%= image_tag "twitter-client/tweet-list-different-tweet-activity.png" %>

## Intent with data

Passing data over intent is pretty straight-forward. 

<pre>
   Intent intent = new Intent(this,<i>Next Activity Name</i>.class)
   <span class="highlight">intent.putExtra("<i>key</i>", <i>value</i>)</span>
   startActivity(intent)
</pre>

While *key* can be any string, value can either be string, integer or even object of a class. 

To retrieve the data in the next Activity that gets loaded after **startActivity(...)**, the code below is needed

<pre>
//to retrieve string
<i>String</i> value = getIntent().getStringExtra("<i>key</i>")
//to retrieve object
<i>Data_Type</i> value = (<i>Data_Type</i>) getIntent().getSerializableExtra("<i>key</i>")
</pre>

### Assignment - show data on Tweet Detail screen from appropriate tweet object

Earlier, we had put an onClickListener for each tweets which started the Tweet Detail Activity on the tweet item click. 

`TweetListActivity.java`

    @Override
	protected void onListItemClick(ListView l, View v, int position, long id) {
		Intent intent = new Intent(this, TweetDetailActivity.class);
	    startActivity(intent);
	}

** 1. Modify onListItemClick() method to pass the tweet object to TweetDetailActivity **

Hint: You should extract the tweet object from the Adapter at `position`. There is `getListAdapter()` method available for ListActivity class. Use it. 

** 2. Use the tweet object to set title, body & date in TweetDetailActivity **

We already have the code to set title, body & date for individual tweets in TweetAdapter. Take inspiration from the code.

Once done, navigate to tweet list screen & click on each tweet to view the Tweet Detail page populate with data from the tweet item clicked. 

##Fetching tweets using HTTP GET calls and submitting new tweets

This level focuses on fetching tweets using the Codelearn Twitter API and displaying them in list in *TweetListActivity* and updating list to add new tweets when refreshed.

###API

Make an HTTP **GET** request call to fetch tweets using-
<pre>
http://app-dev-challenge-endpoint.herokuapp.com/tweets
</pre>

###Request

**Fetching tweets**: A simple GET request without any request parameters is sufficient to get a response.

###Response

**Fetching tweets**: The tweets endpoint will provide an array of tweets as a JSON response when a GET call is received.

<pre>
[ { "body" : "Content of Tweet 1",
    "id" : 1399538725,
    "title" : "Victoria"
  },
  { "body" : "Content of Tweet 2",
    "id" : 1399538726,
    "title" : "Judith"
  },
  { "body" : "Content of Tweet 3",
    "id" : 1399538727,
    "title" : "Ann"
  },
  .....
  { "body" : "Content of Tweet N",
    "id" : 1399538745,
    "title" : "Edgar"
  }
]
</pre>


The algorithm for fetching the tweets should be written such that the new listof tweets should get appended above the current list but in the same order 

## Example

In the JSON response above, the first tweet has title Victoria followed by Judith, Ann & Edgar. It should appear as the order below in TweetListScreen 

`order of tweets on TweetListActivity`
<pre>
Victoria
Judith
Ann
Edgar
</pre>

## On refresh

On refresh, lets say, you get four new tweets with title Josh, Marcus, John & Warren.

<pre>
[ { "body" : "..",
    "id" : ..,
    "title" : "Josh"
  },
  { "body" : "..",
    "id" : ..,
    "title" : "Marcus"
  },
  { "body" : "..",
    "id" : ..,
    "title" : "John"
  },
  { "body" : "..",
    "id" : ..,
    "title" : "Warren"
  }  
]
</pre>

 **The new tweets should be added on top of existing tweets & in the same order as fetched from network**.

`order of tweets on TweetListActivity`
<pre>
<span class="highlight">Josh
Marcus
John
Warren</span>
Victoria
Judith
Ann
Edgar
</pre>


###Tasks

1. Improve the login process by showing a **RelativeLayout** containing a **ProgressBar** while the login HTTP call is in progress. The RelativeLayout should be added **after Login button** in the same activity, should span height & width of screen & should have a child element ProgressBar. The ProgressBar should show up when the Login data is being sent to the server & should be hidden when the login process completes.

2. Modify TweetListActivity to make an HTTP GET call when the Activity is created to fetch tweets. Handle the received Tweet objects and render them in the ListView. **Assume that the url always return the new tweets & you should append the tweets to the items in the List**.

3. Add a refresh menu item which upon click should make an HTTP GET call to get new array of tweets and append the new data to list. The refresh should simply call the */tweets* url & append the tweets to the list.


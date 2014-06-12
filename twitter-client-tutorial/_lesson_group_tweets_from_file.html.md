
Now that we know how to show dynamic list of tweets, we are now going to go to the next level of storing the tweets in a local file & showing tweets from it.

## Why do we need to store

In a mobile app, use of local storage is important for a better user experience. In a real app, when the Tweet List screen comes up, the tweets are read from the file & shown instantaneously while another process starts & runs asynchronously to update the file with latest tweets. 

For now, we are simply going to write the dummy tweets that we created in the previous lesson into a local cache file, read from it & show it to the user when the Tweet List screen loads. In subsequent lesson, we are going to move the writing tweets part to an asynchronous process using AsyncTask. 



# Designing List of Tweet Screen

We successfully hooked 'No Tweet Found' screen after the login screen in the previous lesson. In this lesson, we will remove the 'No Tweet Found' message & populate the screen with a dummy tweet list. As usual, we will use some placeholder data to show some dummy list content.

Before we get on with the task of creating our list of Tweets, it would be a good idea to provide a brief introduction to the way a list view is created in Android. We are going to use `ListView` view element in xml file to show up the list of tweets.

<div class="alert alert-info">For more on ListViews, check out the <b><%= link_to "List View concept lesson", android_concept_lesson_path("android-listview"), target: "_blank" %></b></div>

`Layout XML`

    <ListView
        android:id="@+id/listViewId"
        android:layout_width="match_parent"
        android:layout_height="match_parent" >
    </ListView> 

ListView displays rows using an `Adapter`. It is like a data set. We will use the simplest of the Adapters called `ArrayAdapter`. 

`Java Activity Code`

        stringArray = new String[10];
        for(int i=0; i < stringArray.length; i++){
        	stringArray[i] = "String " + i;
		}
        arrayAdapter = new ArrayAdapter(this, android.R.layout.simple_list_item_1, stringArray);

We created an array of string & passed it to ArrayAdapter as the third parameter. The first parameter is the context. The second parameter `android.R.layout.simple_list_item_1` is a built-in Android layout resource for a simple list item (each row is a TextView). 
    
The arrayAdapter is now ready & need to be passed on the ListView that we created to populate the data inside ListView. It is done as below

`Java Activity Code`

      stringListView = (ListView) findViewById(R.id.listViewId);
      stringListView.setAdapter(arrayAdapter);
	  
The gist of the above content is illustrated in the following graphic.

<%= image_tag "twitter-client/list-view-flow.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

That was a quick overview. Let's implement the above steps to get the basic ListView working for us. We will then go ahead & refine the View to look like the actual tweet list.

## Follow the steps to build the basic Tweet List

* Remove 'No Tweet Found' TextView & add the ListView with id `tweetList` in res -> layout -> activity_tweet_list.xml 

`activity_tweet_list.xml`

<pre>
 .
 .
 <strike>&lt;TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/no_tweet_found" /&gt;</strike>
  <span class="highlight">&ltListView
        android:id="@+id/tweetList"
        android:layout_width="match_parent"
        android:layout_height="match_parent" >
  &lt;/ListView&gt;</span>
  .
</pre>


* Add the highlighted code in TweetListActivity.java. The variables are declared in the class but outside onCreate method. Inside onCreate, the ListView is populated. Remember that findViewById(R.Id.tweetList) should be called after setContentView(R.layout.activity_tweet) is called else the ListView will not be found. 

`TweetListActivity.java`

<pre>
.
.
public class TweetListActivity extends Activity {
	<span class="highlight">private ListView tweetListView;
	private String[] stringArray ;
	private ArrayAdapter tweetItemArrayAdapter;</span>

    @Override
    protected void onCreate(Bundle savedInstanceState) {
	  super.onCreate(savedInstanceState);
	  setContentView(R.layout.activity_tweet_list);

	  <span class="highlight"> stringArray = new String[10];
        for(int i=0; i < stringArray.length; i++){
        	stringArray[i] = "String " + i;
		}
      tweetItemArrayAdapter = new ArrayAdapter(this, android.R.layout.simple_list_item_1, stringArray);
      tweetListView = (ListView) findViewById(R.id.tweetList);
      tweetListView.setAdapter(tweetItemArrayAdapter);</span>
	}
.
.
</pre>

* Eclipse will show you errors in front of tweetListView & tweetItemArrayAdapter variable declaration. It is because ListView & ArrayAdapter classes are not included in the project. You can include it automatically by clicking on the red cross mark in Eclipse which will auto suggest the class names & add it to the java file. Or you can manually add them in the list of import statements on top of the TweetListActivity.java file

<div class="alert alert-info"><strong>Tip</strong>: Pressing <strong>Ctrl+1</strong> in Eclipse in any line with errors will provide suggestions and possible solutions</div>

`TweetListActivity.java`

<pre>
    package ....
	
	import android.os.Bundle;
	import android.view.Menu;
    <span class="highlight">import android.widget.ListView;
    import android.widget.ArrayAdapter;</span>
</pre>

Run the app. After login screen, you will see the ListView as shown below.

<%= image_tag "twitter-client/twitter_list_view.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





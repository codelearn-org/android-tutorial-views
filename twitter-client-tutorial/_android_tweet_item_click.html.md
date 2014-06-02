# Click Listener for individual tweet item

In the previous lesson, we integrated the custom layout row_tweet.xml with the ListView. The next step is to view each tweet in detail when the tweet item is clicked. For the detail screen, we will need a new Activity. We'll do that in a subsequent lesson. In this lesson, we'll see how to enable & capture click event for each item in a ListView. 

Android has a special class `ListActivity` which provides the method `onListItemClickListener(..)` that is called when a ListView child is clicked. TweetListActivity currently extends the Activity class. We need to change that to ListActivity. 

Changing the class to ListActivity has some repercussions though. [This](http://developer.android.com/reference/android/app/ListActivity.html) Android Developer Guide page says

ListActivity needs a ListView with id `@android:id/list` which it will populate through method `setListAdapater(..)`

<div class="alert"> Since ListActivity is a specialized Activity meant to display lists, all you need to do is set the id of the ListView element in XML to <strong>@android:id/list</strong>. ListActivity will internally use findViewById to fetch the ListView for you, and you can set an adapter to it using the <strong>setListAdapter</strong> method</div>

Let's go ahead & make the changes

* Change Activity to ListActivity in TweetListActivity.java .

`TweetListActivity.java`
<pre>
</strike><span class="highlight">
import android.app.ListActivity;</span>

public TweetListActivity extends <strike>Activity</strike><span class="highlight">ListActivity</span>

</pre>

* Update id in activity_tweet_list.xml to '@android:id/list'

`activity_tweet_list.xml`
<pre>
&lt;ListView
        android:id="<strike>@+id/listView</strike><span class='highlight'>@android:id/list</span>"
        android:layout_width="match_parent"
        android:layout_height="match_parent"&gt;
    &lt;/ListView&gt;
</pre>

* Change `setAdapter(..)` to `setListAdapter(..)`. Also, we no longer need the tweetListView variable and the code associated with it anymore. 

`TweetListActivity.java`
<pre>
public class TweetListActivity extends Activity {
    <strike>private ListView tweetListView;</strike>
    private ArrayAdapter tweetItemArrayAdapter;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
      super.onCreate(savedInstanceState);
      setContentView(R.layout.activity_tweet_list);

      tweetItemArrayAdapter = new TweetAdapter(this, new String[10]);
      <strike>tweetListView = (ListView) findViewById(R.id.tweetList);
      tweetListView.setAdapter</strike><span class="highlight">setListAdapter</span>(tweetItemArrayAdapter);
    }
}
</pre>

* We need to show the new TweetDetailActivity (yet to be created) when a tweet is clicked. For now, let's update the clicked tweet title to 'Tweet Clicked'. To do that, let's set a meaningful id to the header TextView in row_tweet.xml

`row_tweet.xml`
<pre>
&lt;LinearLayout ..&gt;

  &lt;ImageView ../&gt;

  &lt;LinearLayout&gt;

     &lt;TextView id="<strike>@+id/textView1</strike><span class='highlight'>@+id/tweetTitle</span>"
	 ./&gt;
	 &lt;TextView ../&gt;
	 &lt;TextView ../&gt;

  &lt;/LinearLayout&gt;

&lt;/LinearLayout&gt;
</pre>

* Add & override `onListItemClick(..)` method to TweetListActivity class. We will get the `tweetTitle` field of the tweet & change the text to 'Tweet Clicked' from 'Header Text'

`TweetListActivity.java`
<pre>
public class TweetListActivity extends ListActivity {
 .
 .
 public void onCreate() {
  .
  .
 }

 <span class="highlight">@Override
 protected void onListItemClick(ListView l, View v, int position, long id) {
     TextView t = (TextView) v.findViewById(R.id.tweetTitle);
	 t.setText("Tweet Clicked");
 }</span>
}
</pre>

The method onListItemClick gets parent ListView (l), child View which is clicked (v), position of the child View in the parent View (position) & id (the id of the row object - you'll hardly, if ever, use this). The new method introduced is `setText(..)`. This method sets the text of a TextView class object.

<div class="alert alert-info">If your project has no errors but the app does not seem to run as expected, refer the <b><%= link_to "Android Log concept lesson", android_concept_lesson_path("android-log"), target: "_blank" %></b> which introduces an effective way of debugging issues</div>

* Run your app. Navigate past the login screen to view the Tweet List screen. Tapping on a tweet item will update the tweet header to 'Tweet Clicked'. 

<%= image_tag "twitter-client/tweet_clicked.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





# Hooking up Login to 'No Tweet Found' Activity

We created a login button listener which simply updated the button label to 'I am Clicked' from 'Login'. Ideally, post login, the user should be able to see the tweets. We need to create a new Activity for that. Let us just create an empty Activity which showed 'No Tweets found'. 

## Creating new Activity 

* Inside Eclipse, right click on the 'CodelearnTwitterApp' project,navigate to New -> Other ->Expand 'Android' dropdown -> Select 'Android Activity'. Click Next.

* Select 'Blank Activity'. Click Next.

* Specify Activity Name as 'TweetListActivity' (the Activity is supposed to show the tweets hence the name), Layout Name will automatically gets populated as 'activity_tweet_list' which is good. Click Finish.

* The new Activity is created. We need to create a string value. Navigate to res -> values -> strings.xml . Inside 'Resources' tab, click on 'Add', select 'String', on the right side under 'Attribute for String', put Name as 'no_tweet_found' & Value as 'No Tweet Found'. Hit 'Control S' to save the file.

* Now the new string field need to be added in the activity_tweet_list.xml . Go to res -> layout -> activity_tweet_list.xml . It is by default showing 'Hello World' through `@string/hello_world`. Change it to @string/no_tweet_found . Save file & click on 'Graphical Layout' tab. You should see 'No Tweet Found' in the output preview.

<%= image_tag "twitter-client/no_tweet_found.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

## Undoing ActionBarActivity mess

<div class="alert alert-warning">
<p>With recent versions of the Eclipse ADT plugin, creating a new Activity leads to the creation of an Activity that extends <b>ActionBarActivity</b> with a fragment_[name].xml and a activity_[name].xml. Although this is a good practice, it's good to start with a simple Activity while learning. If you're facing this situation, read on for instructions to resolve it, or skip to the next section.</p></div>

Move the contents of `fragment_tweet_list.xml` into `activity_tweet_list.xml` and delete `fragment_tweet_list.xml`

`activity_tweet_list.xml`
<pre>
<strike>&lt;FrameLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/container"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="org.codelearn.twitter.TweetListActivity"
    tools:ignore="MergeRootFrame" /&gt;</strike>
<span class="highlight">&lt;RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="org.codelearn.twitter.TweetListActivity$PlaceholderFragment" &gt;

    &lt;TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/hello_world" /&gt;

&lt;/RelativeLayout&gt;</span>
</pre>

Change TweetListActivity to extend **Activity** instead of ActionBarActivity
<pre>
public class TweetListActivity extends <strike>ActionBarActivity</strike><span class="highlight"> Activity</span> {
</pre>

Remove all methods except **onCreate()** in TweetListActivity and delete the code in onCreate() after **setContentView(..)**
<pre>
public class TweetListActivity extends <span class="highlight">Activity</span> {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_tweet_list);

    <strike>if (savedInstanceState == null) {
      getSupportFragmentManager().beginTransaction().add(R.id.container, new PlaceholderFragment())
          .commit();
    }</strike>
  }


  <strike>@Override
  public boolean onCreateOptionsMenu(Menu menu) {

    // Inflate the menu; this adds items to the action bar if it is present.
    getMenuInflater().inflate(R.menu.tweet_list, menu);
    return true;
  }

  @Override
  public boolean onOptionsItemSelected(MenuItem item) {
    // Handle action bar item clicks here. The action bar will
    // automatically handle clicks on the Home/Up button, so long
    // as you specify a parent activity in AndroidManifest.xml.
    int id = item.getItemId();
    if (id == R.id.action_settings) {
      return true;
    }
    return super.onOptionsItemSelected(item);
  }

  /**
   * A placeholder fragment containing a simple view.
   */
  public static class PlaceholderFragment extends Fragment {

    public PlaceholderFragment() {}

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
      View rootView = inflater.inflate(R.layout.fragment_tweet_list, container, false);
      return rootView;
    }
  }</strike>

}
</pre>

Organise imports by pressing <b>Ctrl+Shift+O</b>    

## Hooking new Activity to Login

Now that we are done creating a new Activity, we need to show the activity when the Login button is clicked. We need to use **Intent** for this. Intent is a way of navigating app flow from one Activity to another. 

<div class="alert alert-info">Read more about Intents in the <b><%= link_to "Intents concept lesson", android_concept_lesson_path("android-intent"), target: "_blank" %></b></div>

* We need to hook up the TweetListActivity to show up after MainActivity once the Login button is clicked. We do so using Intent. We need to change a bit of code here.

`MainActivity.java`
<pre>
loginBtn.setOnClickListener(new View.OnClickListener() {
      @Override
      public void onClick(View v) {
	  	<strike>_loginBtn.setText("I am Clicked");</strike>
		<span class="highlight">//Add the following lines
		Intent intent = new Intent(MainActivity.this, TweetListActivity.class);
		startActivity(intent);</span>
      }
  });
</pre>

Please import the package **android.content.Intent** for using Intent class in your java code.

<div class="alert alert-info"><strong>Tip</strong>: In Eclipse, you can press <strong>Ctrl+Shift+O</strong> to automatically organize package imports</div>

Great. You are all set now. Run the app. You should see the Login screen. Click the Login button & you should see 'No Tweet Found' screen that you built before. 

You just learnt to use Intents in Android. Take a break & celebrate. 


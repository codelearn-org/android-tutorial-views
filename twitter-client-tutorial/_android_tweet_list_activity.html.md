# Layout for Tweet

In last lesson, we learnt how to show up a ListView with dummy data. We need the tweet list to look like as below 

<%= image_tag "twitter-client/row-tweet-screenshot.png", alt: "Tweet List Mockup", title: "Tweet List Mockup" %>
<%= image_tag "twitter-client/row-tweet-layout-breakdown.png", alt: "Tweet List Layout Breakdown", title: "Tweet List Layout Breakdown" %>

We used the Android in-built layout `android.R.layout.simple_list_item_1` to get the view in the last lesson. This time, we will build our own layout & pass it to the ArrayAdapter to get the desired view. 

* Right click on `CodelearnTwitterApp` project in Eclipse package Explorer. Select New -> Other. In the popup window, select 'Android XML Layout File'. In the next window, you need to specify the name. Let's give it the name 'row_tweet.xml'. By default, 'LinearLayout' will be picked which is fine as the Outer layout is LinearLayout as per our plan. Hit 'Finish'. Go to res -> layout -> row_tweet.xml. The file should look as below.

      <?xml version="1.0" encoding="utf-8"?>
      <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="vertical" >
        
    
      </LinearLayout>

* The LinearLayout element is what is 'Outer LinearLayout'. It has its children aligned horizontally. Let's update the value. Also, it has two children - ImageView and LinearLayout. We are adding ImageView first time here. We are going to use Graphical Layout this time. [Download user_profile.png]() image & save inside res -> drawable-ldpi folder. We need to provide the path to image when we add the ImageView. Click on row_tweet.xml. Navigate to 'Graphical Layout' tab. Inside 'Palette' on the left hand side, go to 'Image & Media'. Drag 'ImageView' to the layout window. Choose 'user_profile' & hit 'Ok'. You should see the image added in the layout. Go to the other tab which says 'row_tweet.xml'. You will see the XML code added. Modify it as shown below 

`row_tweet.xml`
<pre>
&lt;?xml version="1.0" encoding="utf-8"?&gt;
&lt;LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="<strike>vertical</strike>horizontal" &gt;

    &lt;ImageView
        android:id="@+id/<strike>imageView1</strike><span class="highlight">tweetImage</span>"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:src="@drawable/user_profile"
		<span class="highlight">android:layout_width="70dp"
        android:layout_height="70dp"
        android:layout_marginLeft="5dp"
        android:layout_marginTop="5dp"</span>
		/&gt;

&lt;/LinearLayout&gt;
</pre>

All we have done is to specified width & height of the image & provided margin on the left & top. Time to add the other child LinearLayout & its children.

* Open Graphical Layout tab for row_tweet.xml, go to 'Layouts' under 'Palette'. Drag LinearLayout to the right of the image. Go to 'Form Widgets', drag 'Large Text' for heading, drag 'Medium Text' for body & 'Small Text' for date. Switch over to the XML view. Refine the XML as highlighted below

<pre>
 .
 .
 &lt;LinearLayout
        android:layout_width="wrap_content"
        android:layout_height="match_parent"
        android:orientation="vertical" 
		<span class="highlight">android:layout_marginLeft="10dp"
		android:gravity="left"</span>
		&gt;

        &lt;TextView
            android:id="@+id/<strike>textView1</strike><span class="highlight">tweet_title</span>"
            android:layout_width="<strike>wrap_content</strike><span class='highlight'>match_parent</span>"
            android:layout_height="wrap_content"
            android:text=<strike>"Large Text"</strike><span class="highlight">Header Text</span>
			<span class="highlight">android:textSize="19sp"
            android:textColor="#222222"
            android:textStyle="bold"</span>
            <strike>android:textAppearance="?android:attr/textAppearanceLarge"</strike> /&gt;

        &lt;TextView
            android:id="@+id/<strike>textView2</strike><span class="highlight">tweet_body</span>"
            android:layout_width="<strike>wrap_content</strike><span class='highlight'>match_parent</span>"
            android:layout_height="wrap_content"
            android:text=<strike>"Medium Text"</strike><span class="highlight">Tweet body text here</span>
			<span class="highlight"> android:layout_marginTop="5dp"
            android:ellipsize="end"
            android:lines="3"
			android:textColor="#666666"                                                
            android:textSize="14sp"</span>
            <strike>android:textAppearance="?android:attr/textAppearanceMedium"</strike> /&gt;

        &lt;TextView
            android:id="@+id/<strike>textView3</strike><span class="highlight">tweet_date</span>"
            android:layout_width="<strike>wrap_content</strike><span class='highlight'>match_parent</span>"
            android:layout_height="wrap_content"
            android:text=<strike>"Small Text"</strike><span class="highlight">20 Nov 2013</span>
			<span class="highlight">android:layout_marginTop="5dp"
            android:textColor="#999999"
            android:textSize="12sp"</span>
            <strike>android:textAppearance="?android:attr/textAppearanceSmall"</strike> /&gt;

  &lt;/LinearLayout&gt;
  .
  .
</pre>

  

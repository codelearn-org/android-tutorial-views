# Layout for Tweet List - Part 2

In last lesson we added just the ImageView in the row_tweet.xml . We need to add child LinearLayout with its own children. 

* Navigate to res -> layout -> row_tweet.xml, go to 'Layouts' under 'Palette'. Drag LinearLayout to the layout, on the right side of the ImageView we added in the previous lesson.

[Insert Image]

* We will add child elements to the layout now as well. Go to 'Form Widgets', drag 'Large Text' for heading inside the LinearLayout, drag 'Medium Text' for body & 'Small Text' for date. 

[Insert Image]

* Switch over to the XML view. We are going to refine element attributes for the view to look as we intend it to. Although you can modify attributes in Graphical Layout, we are going to edit the XML directly. Refine the XML as highlighted below

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

A new attribute that we introduced here is `android:ellipsize="end"` & `android:lines="3"`. ellipsize terminates the text to fit three lines & append '...' at the end. 

* Deploy the app, navigate from login screen & it should look as below

[Insert Image]

* To provide spacing between two tweet rows the way it looked in the layout, do following changes in activity_tweet_list.xml

`activity_tweet_list.xml`
<pre>
.
.
&lt;ListView ..
  .
  <span class="highlight">android:dividerHeight= "10dp"  
  android:divider= "#e0e0e0"</span>
  /&gt;
 .
 .
</pre>

Run the app & the tweet list should look as below. In next lesson, we will attach click listener on each ListView row to show the details of the tweet. 

[Insert Image]

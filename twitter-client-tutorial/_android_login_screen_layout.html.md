# Login Screen Layout

So far, we already have a hello world application. In the earlier lesson, we have seen how the control starts from the `onCreate` method of the **MainActivity.java** file and how it renders the layout defined in **activity_main.xml** . 

In this lesson, we will start with designing the Login screen layout. A good way to start is by editing the **activity_main.xml** file. The onCreate method will still render the same XML file and hence we do not need to change any logic/code inside the **MainActivity.java** file. In the XML file, by default you see a **RelativeLayout** element with **TextView** element inside it as shown below.
 
    <RelativeLayout ...
	    .
		.>

		<TextView ..
		 .
		 .>

    </RelativeLayout>


The RelativeLayout element is the container for the UI element, where as TextView is a UI element. The TextView elements are placed relative to the parent or sibling element in Relative Layout. 

<div class="alert alert-info">To read about Layouts in detail, head over to the <b><%= link_to "Android Layouts concept lesson", android_concept_lesson_path("android-layout") ,target: "_blank" %></b></div>

Now,we are going to modify the same **activity_main.xml** file . The final screenshot & the pictorial representation of the Graphical Layout is shown below.

<%= image_tag "twitter-client/Twitter-front-font.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>
<%= image_tag "twitter-client/login-screen-pictorial.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

For this, we need to make two changes. First, let's make the text 'Hello World' span the complete screen width by changing layout_width to 'match_parent'. Second, we update 'Hello World' to 'Hello Twitter' in strings.xml by creating a new entry.

In our tutorials, we follow the convention of showing code blocks in the section as shown below. The striked text is to be replaced with the text written next to it. In our case, we replace "wrap_content" with "match_parent".

<div class="alert alert-info"><p><strong>Tip</strong>: Eclipse has a very useful autocomplete feature. While typing attribute names or values, Eclipse will automatically show a dropdown with possible options. If the dropdown does not appear, press <strong>Ctrl+Space</strong> to see autocomplete options. You may press Enter to select the right option. For example, typing 'm' and Ctrl+Space should be enough to select <strong>match_parent</strong></p>
<p>Autocomplete not only makes coding faster, it's also a great way to discover new stuff - Pressing <strong>Ctrl+Space</strong> in an empty line in an XML or Java file can lead you to new tags, attributes and methods</p></div>
`res/layout/activity_main.xml`

<pre>
&lt;RelativeLayout ...
  .
  .

  &lt;TextView
        android:layout_width="<strike>wrap_content</strike>match_parent"
        android:layout_height="wrap_content"
        android:text="@string/hello_world" /&gt;
  .
&lt;/RelativeLayout&gt;
</pre>

Any new piece of code to be added is highlighted as shown below :

`res/values/strings.xml`

<pre>
<span class="highlight">&lt;string name="hello_twitter"&gt;Hello Twitter&lt;/string&gt;
</pre>

Now, go back and change this reference in the XML as shown below.

<pre>
&lt;RelativeLayout ...
  .
  .

  &lt;TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/<strike>hello_world</strike>hello_twitter" /&gt;
  .
&lt;/RelativeLayout
</pre>

After doing the changes, save both the files by hitting 'Control S' on Windows or 'Command S' on Mac. Run the app & the app should look like as below.

<%= image_tag "twitter-client/hello-twitter.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





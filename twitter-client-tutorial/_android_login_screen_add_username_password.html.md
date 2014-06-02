# Adding Username label & input field

In the previous lesson, we got the header in place. In this lesson, we will add the input fields namely username & password. 

As per plan, we will be using horizontally aligned LinearLayout to hold the label 'Username' & the input field together & next to each other. Label is **TextView** element while input field is **EditText** in Android. 

<div class="alert alert-info">For commonly used View elements, refer the <b><%= link_to "Android Views concept lesson", android_concept_lesson_path("android-views"), target: "_blank"%></b></div>

Let's get to work. 

## Add the LinearLayout after 'Hello Twitter' 

`res/layout/activity_main.xml`

<pre>
&lt;RelativeLayout ...
  .
  .

  &lt;TextView <span class="highlight">
	android:id="@+id/header" </span>
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/hello_twitter" /&gt;

  <span class="highlight">&lt;LinearLayout android:id="@+id/uname_block"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/header"
        android:orientation="horizontal"&gt;  
  &lt;/LinearLayout&gt;</span>
  .
&lt;/RelativeLayout&gt;
</pre>

Add the 'id' attribute to the existing 'Hello Twitter' TextView and set its value as **header** . The LinearLayout is given id **uname_block** & it is positioned below the 'Hello Twitter' TextView through the **layout_below** attribute. The **orientation** is kept horizontal as the child elements label & input field need to be arranged next to each other. **layout_width** & **layout_height** are given default values 'wrap_content'.

## Add Username label & the input text field

`res/layout/activity_main.xml`

<pre>
&lt;RelativeLayout
 .
 .
 .
	&lt;LinearLayout android:id="@+id/uname_block"
			android:layout_width="wrap_content"
			android:layout_height="wrap_content"
			android:layout_below="@id/header"
			android:orientation="horizontal"&gt;  

			<span class="highlight">&lt;TextView android:id="@+id/username"
				android:layout_width="wrap_content"
				android:layout_height="wrap_content"
				android:text="@string/lbl_username"
			 /&gt;

			&lt;EditText
				android:id="@+id/fld_username"
				android:layout_width="wrap_content"
				android:layout_height="wrap_content"
				android:hint="@string/lbl_enter_username"
			/&gt;</span>

	&lt;/LinearLayout&gt;
 .
 .
&lt;/RelativeLayout&gt;
</pre>

The Username has id 'username' & the text is rendered from the string 'lbl_username'. The input field has id 'fld_username' & the hint is rendered from string 'lbl_enter_username'. Hint is Android's equivalent of placeholder text, shown only when the input field is empty. We need to add the string entries too. 


`res/values/strings.xml`

<pre>
&lt;resource&gt;
 .
 .
 <span class="highlight">&lt;string name="lbl_username"&gt;Username&lt;/string&gt;
 &lt;string name="lbl_enter_username"&gt;Enter your username&lt;/string&gt;</span>
&lt;/resource&gt;
</pre>

Once done, run the app. It should look like below.

<%= image_tag "twitter-client/twitter-username.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

It would be good to position and style the 'Username' label & input field better, but let us first complete the basic structure & then we can improve the styling of the UI elements.

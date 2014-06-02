# Styling Login Screen Elements

So far we have focussed on positioning the elements but ignored the width & height of the elements. We will address those issues in this lesson.

## Styling the header

We are going to add a few attributes to the various UI elements in Layout XML to style the content. 

Since the TextView with id "@+id/header" serves as the header, we need a bigger font-size which we will set using the **textSize** attribute. **textColor** sets the font color. **textStyle** can be used to make text bold, italicized and/or underlined. For the heading, we will set the **textStyle** as bold. Just for fun, let's give a black background color (wait, don't judge our color taste). It can be done through **background**. To make sure the text does not *stick* to the sides, we put a **padding** attribute. Padding adds additional space around the content on all directions. 

`activity_main.xml`
<pre>
&lt;TextView <span class="highlight">android:id="@+id/header"</span>
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
		android:text="@string/hello_twitter" 
        <span class="highlight">android:padding="10dp"
        android:textSize="20sp"
        android:textColor="@android:color/white"
        android:textStyle="bold"
        android:background="@android:color/black"</span>
     /&gt;
</pre>

**dp** stands for 'density-independent pixel' & represent **absolute** size. **sp** stands for 'scale (independent) pixel'. It takes into account user's font settings. It is usually good idea to use 'sp' for setting textSize of an Android UI element. For non-font related properties, using 'dp' is fine. 

Once done, save the file & deploy your app. It should look as below. 

<%= image_tag "twitter-client/twitter-header-font.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

## Styling the LinearLayout container

The two container LinearLayout elements with id 'uname_block' & 'pwd_block' are very close to each other. Its good to separate them out for spacious arrangement. We will use **layout_marginTop** attribute for it.

`activity_main.xml`
<pre>
    .
	.
&lt;LinearLayout android:id="@+id/uname_block"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        <span class="highlight">android:layout_centerHorizontal="true"</span>
        android:layout_below="@id/header"
        <span class="highlight">android:layout_marginTop="25dp"</span>
        android:orientation="horizontal"&gt;
		.
		.
		.
&lt;LinearLayout android:id="@+id/pwd_block"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/uname_block"
        <span class="highlight">android:layout_centerHorizontal="true"
        android:layout_marginTop="25dp"</span>
        android:orientation="horizontal"&gt;
	    .
		.
</pre>

## Styling the label TextViews

We will set textSize, textColor & center the label vertically using **layout_gravity**. layout_gravity positions the element relative to the parent element. We do not need to do anything to center the content as **layout_centerHorizontal** is set for the parent LinearLayout element.

<pre>
.
.
&lt;TextView android:id="@+id/username"
         android:layout_width="wrap_content"
         android:layout_height="wrap_content"
         android:text="@string/lbl_username"
         <span class="highlight">android:textSize="16sp"
         android:textColor="@android:color/black"
         android:layout_gravity="center_vertical"</span>
         /&gt;
.
.
&lt;TextView android:id="@+id/pwd"
         android:layout_width="wrap_content"
         android:layout_height="wrap_content"
         android:text="@string/lbl_pwd"
         <span class="highlight">android:textSize="16sp"
         android:textColor="@android:color/black"
         android:layout_gravity="center_vertical"</span>
         /&gt;
.
.
</pre>

## Styling the input fields

The input fields are empty by default. So layout_width should be set for them . To make them not stick to their label, **layout_marginLeft** should be set. Setting **layout_paddingLeft** field ensures that the text entered in the input box does not stick to the left edge. The other attributes added have already been explained earlier in this chapter.

Input fields have a special attribute **inputType**. The values are self explanatory. Specifying the input type allows Android to provide relevant keyboard options (In case of inputType `number`, the keyboard for entering digits is displayed). 

<pre>
&lt;EditText
         android:id="@+id/fld_username"
         android:layout_width="<strike>wrap_content</strike><span class="highlighted">200dp</span>"
         android:layout_height="wrap_content"
         android:hint="@string/lbl_enter_username"
         <span class="highlight">android:layout_marginLeft="8dp"
         android:inputType="textEmailAddress"
         android:paddingLeft="5dp"
         android:textSize="13sp"
         android:layout_gravity="center_vertical"</span> /&gt;
		.
		.
&lt;EditText
         android:id="@+id/fld_pwd"
         android:layout_width="<strike>wrap_content</strike><span class="highlighted">200dp</span>"
         android:layout_height="wrap_content"
         android:hint="@string/lbl_enter_pwd"
         <span class="highlight">android:layout_marginLeft="8dp"
         android:inputType="textPassword"
         android:paddingLeft="5dp"
         android:textSize="13sp"
         android:layout_gravity="center_vertical"</span> /&gt;
.
.
</pre>

## Styling the Login Button

Lastly, we will style the login button. Unlike the username and password fields, the button does not have a LinearLayout container. Therefore, to center it, we need to use **layout_centerHorizontal** attribute. 

To center the text 'Login' inside the button, we use **gravity**. Unlike **layout_gravity** which positions an element relative to its parent, gravity determines the positioning of its children within itself. 

<pre>
&lt;Button
        android:id="@+id/btn_login"
        android:layout_height="wrap_content"
        android:layout_below="@id/pwd_block"
        android:text="@string/lbl_login"
        <span class="highlight">android:layout_width="290dp"
        android:layout_centerHorizontal="true"
        android:gravity="center"
        android:layout_marginTop="15dp"
        android:textSize="13sp"
        android:textStyle="bold"</span> /&gt;
</pre>

Ok, that was quite a few styling changes but fret not, your effort will definitely 'show up good'. Save the file & run the app. The shiny new Activity with nicely styled elements should show as below.

<%= image_tag "twitter-client/Twitter-front-font.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





# Add Password & Login button

In the previous lesson, we added Username label & input field. For the password, we will simply replicate the LinearLayout for the Password label & input field. 

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

			&lt;TextView android:id="@+id/username"
				android:layout_width="wrap_content"
				android:layout_height="wrap_content"
				android:text="@string/lbl_username"
			 /&gt;

			&lt;EditText
				android:id="@+id/fld_username"
				android:layout_width="wrap_content"
				android:layout_height="wrap_content"
				android:hint="@string/lbl_enter_username"
			/&gt;

	&lt;/LinearLayout&gt;

	<span class="highlight">&lt;LinearLayout android:id="@+id/pwd_block"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/uname_block"
        android:orientation="horizontal"&gt;

        &lt;TextView android:id="@+id/pwd"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="@string/lbl_pwd"
         /&gt;

        &lt;EditText
            android:id="@+id/fld_pwd"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:hint="@string/lbl_enter_pwd"
         /&gt;

    &lt;/LinearLayout&gt;</span>
 .
 .
&lt;/RelativeLayout

</pre>

`res/values/strings.xml`

<pre>
&lt;resource&gt;
 .
 .
 &lt;string name="lbl_username"&gt;Username&lt;/string&gt;
 &lt;string name="lbl_enter_username"&gt;Enter your username&lt;/string&gt;
 <span class="highlight">&lt;string name="lbl_pwd"&gt;Password&lt;/string&gt;
 &lt;string name="lbl_enter_pwd"&gt;Enter your password&lt;/string&gt;</span>
&lt;/resource&gt;
</pre>


Note that since **id** needs to be unique, the second LinearLayout, TextView & EditText field have different ids. After this point, the app will look as below

<%= image_tag "twitter-client/twitter-password.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>

Let's add the Login button as well

`res/layout/activity_main.xml`

<pre>
&lt;RelativeLayout ..
 .&gt;
 .
 .
 &lt;LinearLayout ..
  .
  .
  .
  .
 &lt;/LinearLayout&gt;
 &lt;LinearLayout ..
  .
  .
  .
  .
 &lt;/LinearLayout&gt;
 
 <span class="highlight">&lt;Button
        android:id="@+id/btn_login"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/pwd_block"
        android:text="@string/lbl_login"
     /&gt;</span>

</pre>

`res/values/strings.xml`

<pre>
&lt;resource&gt;
 .
 .
 <span class="highlight">&lt;string name="lbl_login"&gt;Login&lt;/string&gt;</span>
&lt;/resource&gt;
</pre>

The login button is placed 'below' the password LinearLayout. With this step, the login screen design is complete. Run the app & the output should look as below.

<%= image_tag "twitter-client/twitter-login.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





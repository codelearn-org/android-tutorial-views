# Adding Listener to Login Button 

So far, we just have the interface of the login screen. As per plan, we will simply move to the next Activity when Login button is pressed. We will not capture any login information for now. Once we are done with our first iteration, we will revisit the Login Activity & add capturing of login information & validation of the user. 

To get started on this, we will register a **ClickListener** with the login button. 

A `ClickListener` is a callback facility provided by the Android framework to allow you to write in the logic to handle click event on a UI element (login button in this case). Almost every view element in an app screen can have a callback ClickListener associated with it. The general approach is to implement an [Anonymous Inner Class](http://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html) implementation for the ClickListener and pass it to the callback method.

<div class="alert alert-info">In case you missed it, check out the <b><%= link_to "Android Views concept lesson", android_concept_lesson_path("android-views") + "#Button-Click-Listener",target: "_blank" %></b> for a brief introduction to event listeners</div>

Follow the steps below to implement the ClickListener for the login button

* The code needs to go in MainActivity.java . First, we need to get reference of the login button from the Java code. The variable _loginBtn is a private variable for class MainActivity.

`MainActivity.java`
<pre>
  import android.view.View;
  import android.widget.Button;

  public class MainActivity extends Activity {
 <span class="highlight">
  Button _loginBtn;</span>

 @Override
  protected void onCreate(Bundle savedInstanceState) {
	super.onCreate(savedInstanceState);
	setContentView(R.layout.activity_main);<span class="highlight">
    _loginBtn = ( Button ) findViewById(R.id.btn_login);</span>
	.
	.
	}
   }	
</pre>
* Remember the login button has `android:id="@+id/btn_login"` in the activity_main.xml file. The `findViewById` method is like a lookup function that looks into your layout file, and retrieves the View instance associated with the ID you pass.

* The `Button` class is provided by the framework &ndash; **android.widget.Button** &ndash; and you can use it to invoke a bunch of methods that can modify the behaviour or state of the button. 

* The `R.id.btn_login` is an auto-generated encapsulation that the Android framework provides for all view IDs at a code level. Basically, whenever you compile your Android application, it generates a file called R.java located inside gen -> org.codelearn. This file contains all the IDs that you have defined in all your Layout files, and associates a Hex value with them. At runtime, these Hex values are used to provide a binding between the Java code and the XML elements.

* The code snippet that does the job is below. It needs to be called inside onCreate() of MainActivity.java as this method is executed first when the activity launches. 

<div class="alert alert-info">The <b><%= link_to "Android Activity concept lesson", android_concept_lesson_path("android-activity"),target: "_blank" %></b> has an explanation of onCreate() and the other Activity lifecycle methods</div>

`MainActivity.java`
<pre>
protected void onCreate(Bundle savedInstanceState) {
  .
  .

     <span class="highlight"> _loginBtn.setOnClickListener(new View.OnClickListener() {
      @Override
      public void onClick(View v) {
  		//This is a comment which does no good to your code. Feel free to remove it after you copy paste.
		//When the button is clicked, the control will come to this method.
		//To demonstrate this, let us try changing the label of the Button from 'Login' to 'I am clicked'
		
		_loginBtn.setText("I am Clicked");}
		
  });</span>
  .
  .
}
</pre>

A View object represents a rectangular area on the screen and is responsible for drawing and event handling. **setOnClickListener** registers a callback to be invoked when this view is clicked.

Once done, clicking on the Login button should update the text inside the button to 'I am Clicked' as shown below. In its fully functional form, clicking on the button will authenticate the user and either show an error message or take the user to the next screen. For now, we will assume that the user is authenticated, and move on to the next screen. The next lesson deals with building the screen shown after a successful login.

<%= image_tag "twitter-client/click-change.png", alt: "Login screen Layout overview", title: "Login screen Layout overview" %>





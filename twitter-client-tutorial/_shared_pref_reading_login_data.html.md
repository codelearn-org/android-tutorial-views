# Reading Login data from the View 

## Recap from module 1

Quick recap from module 1. The login screen is served by MainActivity.java . The login fields - username, password & login button - are defined in activity_main.xml . 

A login button listener is called when login button is clicked. We had earlier put the intent code inside the listener to navigate to the tweet list screen on login button click 

	_loginBtn.setOnClickListener(new View.OnClickListener() {
			  @Override
			  public void onClick(View v) {
				.
				// processing after button click happens here
				.
			  }
	});

## Reading the login data

The username & password are stored inside appropriate **EditText** View elements. Each element has its own `android:id` attribute. The data can be read using `findViewById` method as

<pre>EditText username = ( EditText ) findViewById(R.id.<i>id_of_the_username_field</i>)</pre>

`username` field now holds the EditText object. To get the text value from the View, we will use `getText()` method of EditText View element. 

<pre>String usernameValue = username.getText().toString();</pre>

`toString()` method converts the text value to string. 

### Assignment - read username & password in java code

Your task is to write code inside the `onClick()` method to get the username and password String values and log them. You can log the values & check them in LogCat by doing

     Log.d("Codelearn", "username caught - " + usernameValue)
     
     /* When "user123" is entered in the username EditText field
      * and the button is clicked, you'll see the LogCat message
      * "username caught - user123"
      */

<div class="alert alert-info">To know more on dumping data in the console & checking it in LogCat, head over to the <b><%= link_to "LogCat concept lesson", android_concept_lesson_path("android-log"), target: "_blank" %></b></div>

**Hint**: Make sure to insert the new lines of code to log the username and password **before** the lines that define and start an intent to the next Activity. Otherwise, `findViewById(..)` will not be able to find the expected EditText elements.



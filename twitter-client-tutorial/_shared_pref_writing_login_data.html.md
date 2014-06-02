# Writing login data to Shared Preference

Shared Preference is a good place to store app-specific data. It is the easiest form of local storage available in an Android app. SharedPreference uses a simple key-value pair format to store and retrieve data. Because it is meant for simple data, SharedPreference does not support storing complex Objects.

We first obtain an instance of SharedPreference through the code snippet below 

    SharedPreferences prefs = getSharedPreferences("codelearn_twitter", MODE_PRIVATE)

`getSharedPreferences()` method takes two arguments. The first string denotes the preference name. It should be different for different apps. The second string `MODE_PRIVATE` specifies that the preferences are private & other apps cannot access these values.

To write or read from SharedPreferences, create an instance of the SharedPreference Editor. 
 
    Editor editor = prefs.edit();

To write a key-value pair to SharedPreference, use the code below

<pre>editor.putString("<i>key</i>","<i>value</i>");
editor.commit();</pre>

The key may be any String. The value is associated with that key, and you can fetch the value from the SharedPreference by providing the key.

<div class="alert alert-warning">Make sure you call <b>commit()</b> on the Editor object! Writing to the app's SharedPreference is an intensive process, so any modifications made using the Editor  are not actually written until the <b>commit()</b> method is called</div>

To read from SharedPreference, you can do this

<pre>String valueStr = prefs.getString("<i>key</i>", null);
//valueStr will now contain the value we'd previously associated with the key</pre>

The second argument 'null' specifies what to return if no entry with *key* is found. It makes sense to keep it null.

### Assignment - write username & password to SharedsPreference

In the previous assignment, you grabbed the username & password fields & dumped them in LogCat. Now go ahead & write the username & password to SharedPreference.

<div class="alert alert-warning">You need to provide preference name as <b>codelearn_twitter</b> (as the first argument in the <b>getSharedPreferences(..)</b> method) so that our tests will be able to access SharedPreference & figure out if you are actually writing username & password to it</div>

**Additional help**

If you're having trouble completing this module, read on for some help.

To complete this module, you need to save the username and password in a SharedPreference. You've already extracted the username EditText content to usernameValue as a String. To write it to SharedPreference, obtain an instance of it, create an Editor object and save the usernameValue using a key of your choice.
<pre>
public void onClick(View v) {
    String usernameValue = username.getText().toString();
    SharedPreferences prefs = getSharedPreferences("codelearn_twitter", MODE_PRIVATE);
    Editor editor = prefs.edit();
    editor.putString("key_for_username",usernameValue);
    //Code for extracting password value and saving it in the SharedPreference
    editor.commit();
    //Code for showing next Activity using intent (unchanged)
}
</pre>
Using that for reference, your task is to save the password into the SharedPreference and complete the assignment. 


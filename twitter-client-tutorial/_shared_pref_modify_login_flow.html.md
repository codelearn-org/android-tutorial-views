# Do not show login screen again

A real twitter app does not show login screen after you have already logged in. On subsequent visits, it directly takes you to the tweet list screen as soon as you open the app.

The check to skip a screen completely should happen inside `onCreate()` method of the Activity.

<pre>
public class MainActivity extends Activity {
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		<span class="highlight">//check if the current Activity needs to be skipped {
		    Intent intent = new Intent(this, <i>Next Activity where the user should go</i>.class);
	        startActivity(intent);
		    finish();
		//}</span>
		super.onCreate(savedInstanceState);	
		.
		.
	}
	.
	.
}
</pre>

## Assignment - skip login screen if login information is already present.

As discussed earlier, once the username & password is stored, the user should not see the login screen again. Your task is to write the code to check if the current Activity must be skipped (when the username and password are available). To ensure that your code works, fill in some login data, press login, close the app & launch it again - you should be taken directly to the tweet list screen.

**Help**

If you're having trouble completing this module, read on for some help.

Since we save the username and password in SharedPreference, MainActivity can be skipped when the SharedPreference returns the saved username.
<pre>
SharedPreferences prefs = getSharedPreferences("codelearn_twitter", MODE_PRIVATE);
String savedUsername = prefs.getString("key_for_username", null);
</pre>

Similarly, retrieve the saved password. If the retrieved username and password are not null, it means that a login was performed previously, and the user can taken to the **TweetListActivity** directly.

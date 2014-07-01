## Executing HTTP requests
In this level, your task is to send different types HTTP requests to the Codelearn Test API and handle the response appropriately. We will be submitting and updating lift data and deleting a lift enitiy using the API endpoint.

###Lift creation API
The Codelearn LiftApp API endpoint for submitting the lift data is available at:

<pre>
http://codelearn-liftapp.herokuapp.com/api/create
</pre>

####Request
The JSON request object for the HTTP **POST** request can be as follows.
<pre>
{
"phone" : "9876543219",
"location" : "narnia",
"stime" : "8:15",
"etime" : 16:30"
}
</pre>

Note that the field names must be same as the ones given above.

####Response
The API will provide you with the lift id as a JSON response
Note that this id is unique for each lift entity stored in the database.
<pre>
{
"id" : "_sfdf3rcfht4t553"
}
</pre>

==================================================================================
###Lift updating API
For updating the lift data in the database, a **PUT** request encoded with the lift id can be sent to the API endpoint as follows:
<pre>
http://codelearn-liftapp.herokuapp.com/api/lifts/{{id}}
</pre>
Where ``{{id}}`` should be replaced with your lift id. For example:
<pre>
http://codelearn-liftapp.herokuapp.com/api/lifts/_sfdf3rcfht4t553
</pre>  

####Request

The JSON request object for the HTTP **PUT** request should be similar to the **POST** request.
<pre>
{
"phone" : "9876543219",
"location" : "narnia_new",
"stime" : "8:20",
"etime" : 16:40"
}
</pre>

===================================================================================
###Lift deletion API
For deleting a lift enitiy from the database a **DELETE** request encoded with the lift id could be sent to the API endpoint as follows:

<pre>
http://codelearn-liftapp.herokuapp.com/api/lifts/_sfdf3rcfht4t553
</pre>  


##Tasks

1. Modify the app the send the lift data to the API endpoint as a HTTP POST call on creating a lift in the CreateLiftActivity.
2. Once you receive a successful response, store the received id in SharedPreference, specifying the name of the preference file as **codelearn_liftapp** and the name of the preference key as **pref_lift_id**
3. For updating the lift data from the edit/create lift screen, a HTTP PUT call must be sent to the API endpoint.
4. Add a menu item to LiftListActivity which allows the user to delete the lift. On clicking the menu item a HTTP DELETE call should be made to the API endpoint.

##Restrictions
1. The lift id must be stored in a SharedPreference file named "codelearn_liftapp" with preference key, *"pref_lift_id".
2. You must use only DefaultHttpClient or AndroidHttpClient for HTTP calls
3. There must be exactly two items i.e edit and delete in the menu of LiftListActivity.

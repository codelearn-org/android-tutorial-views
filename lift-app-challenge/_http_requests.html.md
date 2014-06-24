## Executing HTTP requests
In this level, your task is to send different types HTTP requests to the Codelearn Test API and handle the response appropriately.

###Carpool creation API
The Codelearn LiftApp API endpoint for submitting the carpool data is available at:

<pre>
http://codelearn-carpool.herokuapp.com/api/create
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
The API will provide you with the carpool id as a JSON response
Note that this id is unique for each carpool entity stored in the database.
<pre>
{
"id" : "_sfdf3rcfht4t553"
}
</pre>

==================================================================================
###Carpool updating API
For updating the carpool data in the database, a **PUT** request encoded with the carpool id can be sent to the API endpoint as follows:
<pre>
http://codelearn-carpool.herokuapp.com/api/carpool/{{id}}
</pre>
Where ``{{id}}`` should be replaced with your carpool id. For example:
<pre>
http://codelearn-carpool.herokuapp.com/api/carpool/_sfdf3rcfht4t553
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
###Carpool deletion API
For deleting a carpool from the database a **DELETE** request encoded with the carpool id could be sent to the API endpoint as follows:

<pre>
http://codelearn-carpool.herokuapp.com/api/carpool/_sfdf3rcfht4t553
</pre>  


##Tasks

1. Modify the app the send the carpool data to the API endpoint as a HTTP POST call while creating a carpool in the CreateCarpoolActivity.
2. Once you receive a successful response, store the received id in SharedPreference, specifying the name of the preference file as **codelearn_liftapp** and the name of the preference key as **pref_carpool_id**
3. For updating the carpool data from the edit/create carpool screen, a HTTP PUT call must be sent to the API endpoint.
4. Add a menu item to CarpoolListActivity which allows the user to delete the carpool. On clicking the menu item a HTTP DELETE call should be made to the API endpoint.

##Restrictions
1. The carpool data must be stored in a SharedPreference file named "codelearn_liftapp".
2. You must use only DefaultHttpClient or AndroidHttpClient for HTTP calls
3. There must be exactly two items i.e edit and delete in the menu of CarpoolListActivity.

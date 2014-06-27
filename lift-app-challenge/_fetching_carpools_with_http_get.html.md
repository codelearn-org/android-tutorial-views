##Fetching carpools using HTTP GET calls.

This level focuses on fetching carpools using the Codelearn Carpool API and displaying them in list in *CarpoolListActivity* and firing up a new activity *CarpoolDetailActivity* which displays all the carpool data when a carpool item is clicked on the list.

###API

Make an HTTP **GET** request call to fetch carpool using-
<pre>
http://codelearn-carpool.herokuapp.com/api/carpools
</pre>

###Request

**Fetching carpools**: A simple GET request without any request parameters is sufficient to get a response.

###Response

**Fetching carpools**: The endpoint will provide an array of carpools as a JSON response when a GET call is received.

<pre>
[
  {
    "etime": "17:20",
    "stime": "14:20",
    "location": "narnia",
    "phone": "9876543210"
  },
  {
    "etime": "17:32",
    "stime": "14:32",
    "location": "hogwarts",
    "phone": "1234567890"
  },
  {
    "etime": "14:35",
    "stime": "8:35",
    "location": "mordor",
    "phone": "9999988888"
  },
  {
    "etime": "18:14",
    "stime": "10:14",
    "location": "pandora",
    "phone": "9538384545"
  }
]
</pre>

## Example

In the JSON response above, the first carpool has location narnia followed by hogwarts, mordor & pandora. It should appear as the order below in CarpoolListScreen 

`order of carpools on CarpoolListActivity`
<pre>
narnia
hogwarts
mordor
pandora
</pre>

##Carpool Details

While displaying minimal details about the carpools in the CarpoolListScreen, we need to fire up a new activity which diplays all the information of the carpool when the corresponding carpool is clicked on the list. We need to also allow the user to call or message the carpool number if the user needs to contact the carpool owner. The layout of the carpool detail activity can be as follows.


###Tasks

1. Modify CarpoolListActivity to make an HTTP GET call when the Activity is created to fetch carpools. Handle the received Carpool objects and render them in the ListView.

2. Register an **onListItemClick** listener which, on clicking a list item, fires up the activity **CarpoolDetailAcitivty** to display the corresponding carpool details. 

2. Add two buttons with ids **R.id.call** and **R.id.message** to call or message the carpool phone number repectively. The button click should launch the proper intents. 

###Restrictions
* You must only use **AndroidHttpClient** or **DefaultHttpClient** to do network calls as they can only be mocked & tested with Robolectric. Any other library is not supported.
* For JSON parsing, you can use **GSON** & **Jackson** libraries only

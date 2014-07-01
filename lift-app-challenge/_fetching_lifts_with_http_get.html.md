##Fetching lifts using HTTP GET calls.

This level focuses on fetching lifts using the Codelearn Test API and displaying them in list in *LiftListActivity* and firing up a new activity *LiftDetailActivity* which displays all the lift data when a lift item is clicked on the list.

###API

Make an HTTP **GET** request call to fetch lift using-
<pre>
http://codelearn-liftapp.herokuapp.com/api/lifts
</pre>

###Request

**Fetching lifts**: A simple GET request without any request parameters is sufficient to get a response.

###Response

**Fetching lifts**: The endpoint will provide an array of lifts as a JSON response when a GET call is received.

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

In the JSON response above, the first lift has location narnia followed by hogwarts, mordor & pandora. It should appear as the order below in LiftListScreen 

`order of lifts on LiftListActivity`
<pre>
narnia
hogwarts
mordor
pandora
</pre>

##Lift Details

While displaying minimal details about the lifts in the LiftListScreen, we need to fire up a new activity which diplays all the information of the lift when the corresponding lift is clicked on the list. We need to also allow the user to call or message the lift number if the user needs to contact the lift owner. The layout of the lift detail activity can be as follows.


###Tasks

1. Modify LiftListActivity to make an HTTP GET call when the Activity is created to fetch lifts. Handle the received Lift objects and render them in the ListView.

2. Register an **onListItemClick** listener which, on clicking a list item, fires up the activity **LiftDetailAcitivty** to display the corresponding lift details. 

2. Add two buttons with ids **R.id.call** and **R.id.message** to call or message the lift phone number repectively. The button click should launch the proper intents. 

###Restrictions
* You must only use **AndroidHttpClient** or **DefaultHttpClient** to do network calls as they can only be mocked & tested with Robolectric. Any other library is not supported.
* For JSON parsing, you can use **GSON** & **Jackson** libraries only

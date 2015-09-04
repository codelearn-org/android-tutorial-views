# What is Android ?

Android has come a long since its inception in 2009 - A lot of things have changed from Cupcake to KitKat. We have not only seen great Android Phones but a mature operation system and beautiful App experience.

Though a lot has changed since the launch of Android, the basic building blocks of Android app have remained the same. Let's look at some of the basic building blocks of an Android app in detail. Later, we will see how all these components come together to create an app, using the example of a Twitter application.

An Android Application is coded in Java and compiled into a single distribution package called as APK. APK is the executable file which is installed on your phone as Android app.  Let's walk through the various building blocks of the an Android application.

<br/>
<%= image_tag "android-introduction/picture-1.png", alt: "Building Blocks of Android", title: "Building Blocks of Android" %>

<p class="ac"><b>Building Blocks of Android</b></p>
<br/>

The basic building blocks of any Android app are - **Activities**, **Views** and **Intents**. These are a must in any Android app

Services, Content Provider and Broadcast are some of the advance features which add more functionality to your app

Let's go 1 by 1 into each of these components and get more details about them.

## Activity

This is the first Android component you will encounter as soon as you open an Android app. An Android app should have at least one Activity in it.

* So what exactly is Activity ? Every screen in an Android app is an Activity.
Activity will always have a User Interface (abbreviated as UI). It is not possible to have an Activity without an UI.

* Any Android app has one or more Activities. Out of these, one Activity will act as the entry point. The Activity will show up when the app starts.
This is usually referred to as the launcher Activity or the main Activity too. 

* Every Activity has its own lifecycle. You can read more about it in the <%= link_to "Activity Concept Lesson", android_concept_lesson_path("android-activity")  %> . 

* Every Android app has a Manifest.xml where all Activites are defined and one Activity is marked as Main Activity. One of the most common error developers commit when they start with Android development is forgetting to add a new Activity in Mainfest.xml file.

As a developer, Activity is a Java class file where you write the logic. Activity does not include the UI. Rather, one of the things you need to write in your Activity logic is - which UI to show. <br/>
<div class="ac">
 <%= link_to "Go to hands on tutorial on Acitivity", app_tutorial_module_with_token_path("twitter", LessonModule.find_by_lesson_number(4).lesson.token), class: "btn btn-success btn-large" %>
</div>

## User Interface / Views

User Interface or UI is what the user sees on the screen. The Activity has the responsibility to *set* the UI for the screen. UI comprises primarily of two type of sub-components. **Views** & **Layouts or ViewGroups**. 

View as the name suggest is the basic building block like buttons, label, input-box etc. Layout is the container for View elements. The Layout primarily defines the pattern in which the View element should show up. Eg. LinearLayout mandates that the View elements inside it either stack up horizontally or vertically while RelativeLayout lets each View element position itself relative to the parent or a sibling element. 

UI is defined as XML. The top XML element is a Layout element . Inside it, there can be either View elements or Layout elements. An example XML file is shown below.

     <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:orientation="horizontal" >
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Button 1" />
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Button 2" />
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Button 3" />
     </LinearLayout>

You may read more about Layouts & Views in our <%= link_to "Layout Concept Lesson", android_concept_lesson_path("android-layout")  %> & <%= link_to "View Concept Lesson", android_concept_lesson_path("android-views")  %>.
<div class="ac">
 <%= link_to "Go to hands on tutorial on Android UI", app_tutorial_module_with_token_path("twitter", LessonModule.find_by_lesson_number(4).lesson.token), class: "btn btn-success btn-large" %>
</div>
## Intents

To move from one Activity to another (or one screen to another), on user interaction like click of a button or click of a notification item, Intents are used. It is possible to pass data including whole objects with Intent. Using Intent you can also open another Android application.

> Apart from launching an Activity, Intent can also launch a Service.   

With Activity, Views and Intent; you can create a basic Android app. Lots of apps are made by using only these three concepts.

Let’s look into some of the advanced Android concepts. 

<div class="ac">
 <%= link_to "Go to hands on tutorial on Intents", app_tutorial_module_with_token_path("twitter", LessonModule.find_by_lesson_number(42).lesson.token), class: "btn btn-success btn-large" %>
</div>
## Services

Have you ever listened to Music on your phone? Have you observed that the music continues to play in the background when you go to the home screen from the Music app or close the app?

This is achieved using Services. Services is the Android way of keeping an operation going on in the background.  When you need to have long running tasks like playing music, downloading data or uploading photos; it is achieved through Service.
 
Service doesn’t have any UI. To show any information to the user from Service, Notifications are used. 

There are two ways in which you can create a Service. One way is to tie the Service with an Activity. In this case, the Service will end once Activity stops. The other way is to run a Service independent of any Application. This way, the Service keeps running in the background even after the application is stopped.   


## SQLite (Database) in Android 

Android ships with SQLite database support. Android apps can store data locally in the SQLite database. Every Android application can create its own private SQLite databases which it can use to store data for offline reference.

The purpose of storing data locally is primarily to provide a good user experience. Consider the example of the Android Twitter app. When you open the app, you immediately see the tweet list while there is a loading symbol shown which conveys that the tweets are still being fetched. The tweet list is stale, but you do not have to wait for the tweets to load because the app has stored the tweets locally.

There are other options apart from the database to store data in an Android app. Information of small sizes can be stored in Shared Preferences. You can also create local files & store data in it.  

## Content Providers

If your Android app wants to use data from another Android app, you may use Content Providers. 

A simple example of Content Provider is the Contacts app. You can get contacts in multiple applications like your SMS application, Dialer Application etc. 

If you are using SQLite/database in your app, you can either access it directly or through a Content Provider. Content Provider gives you encapsulated access.

## Notifications

Earlier in the Services section, we came across Notifications. If you have used an Android phone, you would have seen small notifications in the top part of your phone for missed call, SMS or email received etc.  These are Notifications. 

*    Notifications are simple messages which are used to display information to user that doesn’t require user’s immediate attention 
*    Typically notification comes with Text and Small icon, but newer version of Android support richer notification with buttons and images
*    User can tap on notification and can interact with it

Notifications are the most widely used functionality in Android, from SMS to missed call, from wifi network connection to Twitter notifications. They are used everywhere. 

## Broadcast Receivers

Broadcast receiver is a way to listen to systemwide events happening in your phone or tablet. Using Broadcast Receivers, we can create some great applications like Call Number finder, SMS blocker etc,  which works when some events happen in your device. 

Many systemwide events broadcast their information. For example 

*    When SMS / Call is received 
*    Battery low
*    Network state Changed
*    Photo captured from camera
*    Phone Starts

We can also generate custom broadcast from inside our application. Whenever you want to create any application which works with system events use broadcast receiver 

> Broadcast receivers work even if your application is not running. That means you can create functionality in your application which can be invoked automatically by Android if something happens without actually running any service or application in the background. 

So we have seen how different components are available to create any application in Android, now let's look into an application like twitter and see all these components in action. 

## Android Components in Twitter App 

We are going to demonstrate all the above components in a Twitter app. Below is the screenshot of the app screens with relevant components highlighted.

<br/>
<%= image_tag "android-introduction/twitter_android.png", alt: "Twitter Android", title: "Twitter Android" %>
<br/>

You can see the various components and how they are used in the Twitter app. Let's take one component at a time. 

###Starting up###
<div class="row-fluid">
 <div class="span8">
  <div style="margin:auto">
	<p>You clicked on the twitter blue icon to launch the Twitter app. This icon is called as Launcher icon.</p>
	<p>Once the application is started, it checks if you are logged in or not, if not you are presented with a login. If you are already logged in, you are redirected to your Twitter stream.</p> 
	<p>The login screen is the Main Activity defined in the Manifest.xml file of the Twitter app.</p>
  </div>
 </div>
 <div class="span4">
	<%= image_tag "android-introduction/startingup.png" %>
 </div>
</div>



###Login Screen###

<div class="row-fluid">
 <div class="span8">
  <div style="margin:auto">
    <p>Once you key in your login details & hit 'Sign In' button, Twitter app does a network call to verify your username & password. This is done using <b>AsyncTask</b>. AsyncTasks are the Android equivalent of Threads meant for short-term one-off operations (like HTTP network calls).  
	<p>After the user name and password are verified you see the <b>new Activity</b> which shows your Twitter stream. This is done using <b>Intent</b> that helps you to move from one activity to another. 
  </div>
 </div>
 <div class="span4">
	<%= image_tag "android-introduction/login.png" %>
 </div>
</div>


###Twitter Stream Home Screen###

<div class="row-fluid">
 <div class="span8">
  <div style="margin:auto">
   <p>On top of the screen, there is <b>Action Bar</b>. <b>Action Bar</b> is an example of <b>User Interface</b>. 
   <p>The list of tweets is <b>ListView</b> which is a <b>View</b> element. You can click on a tweet to go to the tweet detail screen which is again a <b>new Activity</b>. The navigation happens using the <b>Intent</b>. Notice that detail screen looks the same, only the content is changing. The content is passed through Intent when you click on the tweet.
   <p>Each item of the ListView is a ListItem. ListView is a complex UI View element comprised of multipe ListItems. Even a ListItem is a complex View element comprised of an ImageView & multiple TextView elements.  
  </div>
 </div>
 <div class="span4">
	<%= image_tag "android-introduction/twitter_home.png" %>
 </div>
</div>



###Services, BroadCast Receiver & Database###

<div class="row-fluid">
 <div class="span8">
  <div style="margin:auto">
    <p>Pulling down the ListView screen invokes a <b>Service</b> which runs in background to update the activity with new tweets. 
    <p>While this Service is activated, the Activity keeps showing a 'Loading' sign. The tweets are locally stored in the Twitter app. The Service is supposed to update the tweets in the SQLite database. A Broadcast Receiver is setup to listen to the event which is triggered when the Service ends. The Broadcast Receiver updates the tweet list & hides the 'Loading' sign too. 
   </div>
 </div>
 <div class="span4">
	<%= image_tag "android-introduction/twitter_services.png" %>
 </div>
</div>


###Content Provider for database access###

The tweets once loaded are accessible even when there is no network connection. As mentioned earlier, the tweets are stored in the database. Otherwise, it would not be possible to show the tweets when the app is offline.

Typically you never access a database directly. Instead Twitter app may be using Content Provider. Content Provider helps to provide abstraction over how data is stored and accessed in an application. 

###Notifications###

<div class="row-fluid">
 <div class="span8">
  <div style="margin:auto">
    <p>If you come out of the Twitter app, a Service is started in the background. This service occasionally checks for new tweets and displays a notification if there is an update. 
    <p>Service is one way but to prevent app from draining battery, the Twitter app might be using Push Notification. Push notification are a way to push data to application even if application is not running. 
   </div>
 </div>
 <div class="span4">
	<%= image_tag "android-introduction/notifications.png" %>
 </div>
</div>

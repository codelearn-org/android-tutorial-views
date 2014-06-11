#Android Activity

Android Activity is the basic building block of an Android App. We have already seen this in <%= link_to "the chapter detailing Android Basics", android_concept_lesson_path("android-introduction")  %>. Android Activity always has a User Interface. Android apps consist of one or many Activities. We also saw that to tell Android, which activity to open when the application is launched, we defined Main Activity in Manifest.xml. 

An Android Activity has a Lifecycle during which it performs a few things. The first question when reading about Lifecycle of Activity Lifecycle is - Why is it required ? Let's understand it with an example. 

Assume you are playing a game on your phone, you are at level 2 and suddenly some one calls you. When you get a call, your games stop and you see the Caller Id Screen. When you resume your game after the call ends, it gets resumed from the same point where you left it. 

Now assume you are a game developer. For you, there should be a way to save the game state. Right? How will this happen? To make developer's life easier, Android has something called **Activity Lifecycle**. Consider Lifecycle to be a collection of callback functions getting called whenever something happens to your application (or Activity to be more precise). 

##Activity Lifecycle

<br/>
<%= image_tag "activity_lifecycle/activity_lifecycle.png", alt: "android activity lifecycle", title: "Android Activity Lifecycle" %>

The above image shows various functions like 'onCreate()', 'onStart()' which gets called at various points of an Activity Lifecycle. Let's look at each of the methods/functions in detail.


###onCreate
`onCreate()` is called when your Activity is getting created for the first time. It is called only once during the entire Activity Lifecycle. One of the important things you are supposed to do is to set the Activity Layout through setContentView function.

Also, you can use onCreate to initialize your variables.  In any Android application, whenever you create an Activity, the minimum method which you need to override is onCreate. 

    class MainActivity extends Activity
        @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);
        }
    end

If you notice, OnCreate function is getting passed a variable of class Bundle. Bundle is typically used to store the state of your Activity. Take the example of screen rotation, during which your Activity gets killed and OnCreate is called again. You can determine if the Activity was already there using Bundle so that you do not have to create the Activity again. 

Why is this necessary, imagine you have a form and user has already filled some of the fields. Suddenly the user rotates his screen. Using Bundle, Android retains the values of these fields and re-populates the data after rotation automatically. The value of Bundle will always be null when Activity is getting created for the first time. 

###onStart:
`onStart` gets called just before the Activity becomes visible to the user. If you notice, onStart is called from two places - after onRestart and OnCreate. onStart is always followed by OnResume or OnStop.  You can use onStart to reset Activity data, reinitialize variables etc. 

###onResume:
`onResume` gets called when your Activity comes into the foreground, and it becomes visible to the user. At this point, the Activity is on top of the Activity stack, and the user can start interacting with the Activity. onResume is typically used to register Listeners, bind to Services etc. 

onResume is a good place to refresh your UI with any new changes which might have occurred during the period in which the Activity was not visible. For example, if you are polling a Service in the background (like checking for new tweets), onResume is a good place to update your screen with new results. 

###onPause:
`onPause` is called when another android activity comes on top of your Activity. Typically anything that steals your user away from your Activity will result in onPause.

In OnPause, we either release the resources, or save the application data, or stop background threads etc. 

It is always guaranteed that whenever your Activity is becoming invisible or partially invisible, onPause will be called. But once onPause is called, Android reserves the right to kill your Activity at any point. Hence you should not be relying on receiving any further events. 

###onStop: 

`onStop` is called when your Activity is no longer visible to the user, it is similar to onPause but here you will not see your android activity entirely.  You can use this method as well to store the state of your application and shut down time intensive or CPU intensive operations. This method is guaranteed to be called as of API level 11.

So what is the difference between onPause and OnStop ? If an Activity comes into the foreground and fills the screen such that your current activity is not at all visible, your current android activity will be called with both onPause and onStop . If, however, an Activity that comes to foreground does not fill the screen and your current Activity is partially visible, your current Activity will be called with only onPause. 

Typically whenever you see a dialog box which requires your attention like battery low, network connection your current android activity becomes partially visible and popup box comes on the top. This is the point where only onPause will be called. 

###onRestart:
It is similar to onCreate, but `onRestart` gets called only after onStop. This is the method which you can use to know if your application is starting afresh or getting restarted. 

In onRestart, you will get your application to save the state and reinitialize all the variables. onStart gets called after this.


###OnDestroy:
This is the method which will be called when your Activity is getting killed. This is the final call the Activity will receive in its Lifecycle.

When the user press back button on any Activity the foreground activity gets destroyed and control will return to the previous Activity. 

But remember the fact, there is no guaranty that `onDestroy` will be called. Only when the system is low on resources or user press the back button or if you use `finish()` explicitly in your code, onDestroy gets called. 

Even though you should always use onPause and onStop to clean up resources, release connections etc; onDestory is there to let your app have the final chance to clean things up before the Activity cease to exist. 

So we have seen the complete Activity Lifecycle functions. Lets see what are the different states of an Activity.

##Activity States

The Android OS uses a priority queue to assist in managing activities running on the device. Based on the state in which an Android Activity is, it will be assigned a priority within the OS. This system helps Android identify Activities that are no longer in use, allowing Android to reclaim memory and resources. Following are the states an Activity can go through during its lifetime:

###Active or Running 
<div class="row-fluid">
	<div class="span8">
		<p>Activities are considered active or running if they are in the foreground. This state denotes the top of the Activity stack. The Activity gets assigned the highest priority and will only be killed by Android in extreme situations, such as if the Activity tries to use more memory more than what is available on the device. It can cause the Activity to become unresponsive.</p>
	</div>
	<div class="span4">
		<%= image_tag "activity_lifecycle/activity_running.png", alt: "Android Activity lifecycle State", title: "Android Activity lifecycle State Running" %>
	</div>
</div>

###Paused
<div class="row-fluid">
	<div class="span8">
		<p>An Android Activity is in the Paused state if the device goes to sleep or if it is covered with another Activity partially or completely. Paused activities are very much alive, that is, they maintain all the states and member information. They remain attached to the window manager too. This is considered to be the second highest priority in the Android Activity stack. Paused Activites will only get killed by Android to keep the Active/Running Activity stable and responsive.</p>
	</div>
		<div class="span4">
		<%= image_tag "activity_lifecycle/activity_paused.png", alt: "Android Activity lifecycle State Paused", title: "Android Activity lifecycle State Paused" %>
	</div>
</div>

###Stopped
Android Activities that are completely obscured by another activity are considered stopped or in the background. Stopped activities still try to retain their state and member information for as long as possible, but stopped activities are considered to be the lowest priority of the three states.


##Android Activity Lifecycle Example App

We have seen various states of Android Activity and seen all the Lifecycle methods. Let's walk through a code example and see these Lifecycle methods in action.

Before proceeding, you should import **CodelearnActivityLifeCycle** project from [Codelearn Example apps on github](https://github.com/pranayairan/Code-Learn-Android-Example). If you are new to github, [download the zip](https://github.com/pranayairan/Code-Learn-Android-Example/archive/master.zip), unzip & import CodelearnActivityLifeCycle project in Eclipse. 


*    Import the project into workspace
*    Once imported, deploy the app & follow the steps below. 

###First Run

When your application runs for the first time, you will see onCreate, OnStart and onResume method gets called. Notice the messages which gets displayed. 

###Stopping

Press the home button and exit the app. You will notice that when you press the home button, onPause is called first followed by onStop

###Restarting

Now open the application again by clicking on the application icon. Notice that you will see onRestart getting called followed by OnStart and OnResume

###Destroy

Now once you saw onRestart, just press the back button, this will exit your application but notice that onDestory is called when you exit. And before onDestory, onPause and onStop is called. 

Summarizing the chapter, you understood why an Activity Lifecycle exists, what is its importance and what are the different Lifecycle states which an activity goes through.


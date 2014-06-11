#Android Log

## Beginner 

### Introduction 

To generate Android log statements we follow a different approach than other languages . In java, you can do `System.out.println()` to dump a message where you want to, but it does not work in Android. 

There is an Android Log class that lets you create log messages with one line of code

    Log.d("Tag Name", "Log Message")

`Tag Name` is a tag that you provide with a message that lets you filter the log messages. It helps you locate your `Log Message` in myriad of messages that Android outputs. 

You need to `import android.utils.Log` in appropriate Activity file where you are using Log function.

You can view the messages in `LogCat` window in Eclipse. It is located at the bottom of Eclipse.

<br/>
<%= image_tag "android-logging/logcat-screenshot.png", title: "Android Logcat Screenshot", alt: "Android Log Screenshot" %>

### Opening LogCat in Eclipse

LogCat window is by default available in the bottom window of Eclipse. Other windows in the pane are 'Problems', 'Javadoc', 'Declaration', 'Console'. In case you end up loosing the window (it is very easy for newbie Eclipse user to mess around his way), simply follow the steps below to get the window back. 

<div class="row-fluid">
	<div class="span6">
		<h3>Step 1</h3>
		<p>Window → Show View → Other...</p>
		<br/>
		<%= image_tag "android-logging/logcat-open-step1.png", title: "Android log Open Logcat step 1", alt: "Android log Open 1" %>
	</div>
	<div class="span6">
		<h3>Step 2</h3>
		<p>Open Android Dropdown → Logcat</p>
		<br/>
		<%= image_tag "android-logging/logcat-open-step2.png", title: "Android log Open Logcat step 2", alt: "Android log Open 2" %>
	</div>
</div>

### Message Filtering in LogCat

You should provide a tag for your log messages as it will make it easy for you to search for the message using the tag. 

For eg: 

    Log.d("MyTag","This is sample log message")

has `MyTag` as the tag attached to the log message. You can search for the message by putting **tag:MyTag** in the search field of LogCat

<br/>
<%= image_tag "android-logging/logcat-message-filtering.png", title: "Android Logcat Message Filtering", alt: "Android Log Message Filtering" %>

## Intermediate

###Logging Methods & Levels

We just used `Log.d` so far for dumping the log messages. There are different methods which corresponds to different log levels in Android. 

* Log.v - verbose
* Log.d - debug
* Log.i - info
* Log.w - warning
* Log.e - error

While you can always filter your log messages with tags, the different message levels is a good indication of **urgency level of your message**, error being the most urgent while verbose being the least. 

You can choose to filter messages based on urgency level depending on what state you are in. For eg - if you want to generate a message that is urgent & match urgency of an error notification, you should be using Log.e . 

###Message Filtering Parameters

LogCat is populated by log messages from various different apps, Android system etc & filtering is an important part of viewing the messages. You can filter log messages on various parameters. 

#### By Log Level

Change the message filter level (verbose, debug, info etc) in the dropdown next to input field in LogCat as highlighted in the screenshot below.

<br/>
<%= image_tag "android-logging/logcat-message-level-filtering.png", title: "Android Logcat Message Level Filtering", alt: "Android Log Message Level Filtering" %>

#### By Tag 

Already covered under [Beginner - Message Filtering in LogCat](#Beginner-Message-Filtering-in-LogCat) section . 

#### Others

You can filter/search messages through pid, application name, text or even Java regular expression. You need to provide appropriate prefix. pid - **pid:**, application name - **app:**, text - **text:** etc. For application name, you need to give complete application name like org.codelearn.twitterapp. 

One of the examples below

    app:org.codelearn.twitterapp

###Create Message Filter

Through the filter input, you can apply only one filter at one time (like filtering through pid, application name, text or regular expression). You can additionally filter using the log level (verbose, debug, info etc). If you need to create filters with multiple parameters, you are better off creating filters.

Click on the green '+' button next to 'Saved Filters' as shown below to create a new filter.  
<br/>
<%= image_tag "android-logging/logcat-create-new-filter.png", title: "Android log Create New Filter", alt: "Android log Create New Filter" %>

Add all your parameter in the popup window that shows.

> Do not add prefix 'tag:', 'app:' or 'pid:' in the input fields

<br/>
<%= image_tag "android-logging/logcat-new-filter.png", title: "Android log New Filter", alt: "Android log New Filter" %>

Once you save filter & a new entry gets created below **All messages (no filters)** . In the screenshot, it is named MyTagFilter. Clicking on the filter name will apply filter to log messages.

<br/>
<%= image_tag "android-logging/logcat-filter-created.png", title: "Android log Filter Created", alt: "Android log Filter Created" %>

###Saving & Clearing logs 

The save button next to the log level selection button lets you save the logs in a text file. The button with red cross next to it clears the log. Hover on the buttons to see their actions. 

<br/>
<%= image_tag "android-logging/logcat-save-clear-buttons.png", title: "Android Logcat Save Clear Buttons", alt: "Android Log Save Clear Buttons" %>

##Advanced

### LogCat without Eclipse

You can launch LogCat from command line with `adb` command or through a remote adb shell. You should probably head over to [offical Android docs on Logcat](http://developer.android.com/tools/debugging/debugging-log.html#startingLogcat) for this.



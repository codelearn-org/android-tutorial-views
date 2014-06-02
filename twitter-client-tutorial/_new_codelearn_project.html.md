# Creating A New Codelearn Twitter Project

In the previous lesson, we installed Codelearn Eclipse Plugin. Instead of following the regular process of creating a New Android project, the plugin comes with a **Codelearn Twitter App** project pre-bundled. **When you create a new Android project, it asks for quite a few parameters which is confusing for a newbie. We have condensed all those steps by providing default values.** 

Follow the steps below to create a new Codelearn Twitter App.

P.S. - If you are opening Eclipse from inside of your ADT bundle for the first time, you would see "Android IDE Screen" which you should minimize before proceeding.

<p><%= image_tag "twitter-client/eclipse-open-first-time.png", alt: "Package Explorer Screenshot", title: "Package Explorer Screenshot" %></p>

## 1. Create New Codelearn Project 

<div class="row-fluid">
	<div class="span6">
		You should have Eclipse open. Hit on <strong>File -> New -> Other</strong>
	</div>
	<div class="span6">
		Navigate to <strong>Codelearn Android Project -> Twitter App</strong>. Hit 'Ok'.
	</div>
</div>
<div class="row-fluid">
	<div class="span6">
		<p><%= image_tag "twitter-client/plugin-newproject-menu.png", alt: "Create new Project", title: "Create new Project" %></p>
	</div>
	<div class="span6">
		<p><%= image_tag "twitter-client/plugin-newproject-wizard.png", alt: "New Project Wizard", title: "New Project Wizard" %></p>
	</div>
</div>

<p>You should see an app with the name <strong>CodelearnTwitterApp</strong> in the Package Explorer window (the project navigation window on the left). Screenshot below.</p>
<p><%= image_tag "twitter-client/project-package-explorer.png", alt: "Package Explorer Screenshot", title: "Package Explorer Screenshot" %></p>

## 2. Running the app


<div class="well">If this is your first time with Android/Eclipse, <%= link_to "go through the steps to run an Android application", android_concept_lesson_path("android-hello-world") + "#Running-your-Application", target: "_blank" %> to view the process in detail.</div>

* You can either choose to **[right click on CodelearnTwitterApp] -> Run As -> Android App Codelearn ** or simply hit the **Run button** on the top of Eclipse which will show the popup below. *Remember to choose 'Android App Codelearn' option as against 'Android Application'*
<p>
<%= image_tag "twitter-client/plugin-newproject-run-menu.png", alt: "Codelearn Run Configuration", title: "Codelearn Run Configuration" %>
</p>

* You will need an Android device to run your app. If you have an Android phone, you should keep it jacked in through USB with your computer. Make sure you've enabled <%= link_to "USB debugging", android_concept_lesson_path("android-hello-world") + "#Deploying-app-on-phone", target: "_blank" %> . If you don't have a real device, you need to use the <%= link_to "Genymotion emulator", android_concept_lesson_path("android-hello-world") + "#Genymotion-emulator-setup", target: "_blank" %>. 

<div class="alert alert-info">We <b>strongly recommend</b> that you use an Android phone to test your app. If you choose to run your app on an emulator, consider setting up <b>Genymotion</b> rather than using the default Android emulator (AVD) as Genymotion emulator is much faster.</div>

* This is how the App Output on your phone/emulator should look like 

<%= image_tag "twitter-client/hello-world.png", alt: "Codelearn Hello World", title: "Codelearn Hello World" %>


## Possible Errors

**1. Unable to resolve 'android-19'** - The CodelearnTwitterApp project takes the latest Android API by default. Most probably, you are seeing this as your Android SDK is old. Quick fix is - checkout the Android API version in [Android SDK Directory] -> sdk -> platforms directory & modify `target=19` in **project.properties** file to your Android API version. 

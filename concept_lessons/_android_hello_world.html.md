# Android Hello World

In this tutorial, we will go through various steps of creating a sample android hello world app. Once our application is ready, we will launch the application and see it working in the emulator. We will then go through the folder structure and see various tools available with us in ADT.

## Creating Project From Wizard 

 Unlike other languages where you need to write code to run a basic hello world program, the Android Developer Tool (ADT) or Eclipse provides us a great way to create android applications using wizard. In Android, you just need to follow some simple steps and with a few clicks we get our first Android hello world project up and running. 

This tutorial will help you understand our process and various options in the wizard. 

> If you haven’t installed the ADT or eclipse plugin, please <%= link_to "go to tutorial 2", android_concept_lesson_path("android-setup")  %> and complete your setup. 

Alright , Let's Start then !

If ADT is not running, double click on ADT  to start the development environment. Once the ADT is launched, following these steps:

*    Click on File -> New and choose Android Application Project, you will see the first screen as 

### Screen 1

<br/>
<%= image_tag "hello-android/screen1.png", alt: "Android Hello World new application", title: "Android Hello World New Application" %>

This is the first Screen for creating a new android project. Let's cover each field shown above individually and try to understand their importance. 

*    **Application Name:** application name is nothing but the name of your app. This name is visible on the screen when the app is installed. The application name is also shown in Google Play Store when you upload your application.
*    **Project Name:** Project name is the name of your project that gets created in eclipse. You can give any name to your project. 
*    **Package Name:**  This is very important. Package name is used to uniquely identify your application on Play Store. You should follow the java package convention for the package name . The package name is not shown to the user but should not change ever. A good approach to choose package name is to use the reverse of your company domain name. For example in codelearn, the url is codelearn.org so the ideal package name would be org.codelearn.android
*    **Min Required SDK:**  As you might know, Android started with version 1.5 and its current version is 4.4. These numbers represents different flavors of Android, like 2.3 is termed Gingerbread, 4.1 as Ice Cream Sandwich etc. These names are used for marketing the OS, while version numbers are of interest to developers. Min Required SDK field gives you the flexibility to decide which version of android at minimum you want to support. For example, if you create an application for android 2.3 it will work on android 4.4. In general, it is advisable to have minimum support of 2.3.3 API Version 9. 
*    **Target SDK:** This setting tells android that even though your app will be able to run on its previous android version, but it is explicitly tested with version specified here in this field.
*    **Compile With:**  This option gives lets you choose the version of SDK you want to compile with. Typically,the highest version which is available in your ADT should be chosen here. This will compile your app with the latest code and optimizations. 
*    **Theme:**  If you are creating apps for version 4.X and above you can have an application wide theme. These themes are nothing but some pre defined color schemes, which you can use to improve your application's User Interface.

<div class="alert alert-info">Once you upload an application to the Play Store, you cannot change its package name. So choose your package name wisely</div>

Now, Click on Next: 


### Screen 2

<br/>
<%= image_tag "hello-android/screen2.png", alt: "Android Hello World New Application project config", title: "Android Hello World New Application project config" %>

This screen is use to configure various project settings, lets go 1 by 1 to see all these options 

*    **Create Custom Launcher Icon:** Do you remember how you launch an android app ? Well, we do so by clicking on the application icon. This icon is nothing but the launcher icon. If this option is checked ADT will provide you a wizard to create a launcher icon. Keep this option selected. 
*    **Create Activity:** With this option selected, ADT will create 1st activity for you, this will be your main activity and will have a reference in mainifest. In later chapters, you will get to learn what main activity is, but just to brief you - most of the android applications are built with multiple activities, but whenever you open any application it always starts with the same activity which is termed as your main activity. Through this activity,you tell the Android OS that out of all these activities from my app, open this particular activity whenever the app gets started. 
*    **Mark This project as Library:** Any android project can be of 2 types, library project or a non library project. A library project is a reusable project which is used by other non library projects. Library project cannot be installed. They're different from JAR files in that library projects can contain resources and assets.
*    **Create Project in Workspace:** When you open Eclipse/ADT for the first time, it asks you to choose a workspace. Workspace is nothing but a location on your hard disk where all your projects will be saved. With this checkbox selected, you are telling ADT to save this project in the current location. If you want to store your android project at some other location you can uncheck this option and select your own path to save the app
*    **Add Project to working sets:** When you start working in different projects, your eclipse/ADT workspace will have a lot of projects. So it is difficult to work on a new or existing project, as you have to scroll down on a big list of projects, which you are not even working with. To solve this issue Eclipse has an excellent concept of working set. Working Set  can be used to Group Similar projects together. When your number of projects in ADT starts increasing, you can group them together into working sets to avoid seeing all projects while working. You can easily switch between different working sets without restarting eclipse. 

Click Next

### Screen 3

<br/>
<%= image_tag "hello-android/screen3.png", alt: "Android Hello World New Application Launcher icon", title: "Android Hello World New Application Launcher icon" %>

If you have checked the create custom launcher check box, screen 3 will be for the creation of launcher icon.


On this screen, you can configure different options to create a launcher icon. You can choose your own image, Text or even your clip-arts. In the Right pane, you can see the demo of the icon. 

You can experiment with different options like background color, shape etc and finalize a icon based on preview. 

Click on Next


### Screen 4

<br/>
<%= image_tag "hello-android/screen4.png", alt: "Android Hello World New Application Activity Template", title: "Android Hello World New Application Activity Template" %>

Screen 4 is an activity template screen. ADT comes pre bundled with some activity templates for you. These templates have predefined structures and they automatically generate required code for you.

*    Blank Activity:  this will create a blank activity with just 1 textview. 
*    Full Screen Activity: This is typically used by games. This activity hides the status bar and then your activity takes all screen space.
*    Master Detail Flow: This template creates advanced navigation, based on fragments, which will work on both tablets and phones without any change 

Select Blank activity and Click Next

### Screen 5

<br/>
<%= image_tag "hello-android/screen5.png", alt: "Android Hello World New Application Activity Config", title: "Android Hello World New Application Activity Config" %>

This screen is an Activity configuration screen. Since you asked ADT to create an activity for you, this screen helps you in configuring relevant options.

*    **Activity Name:** this will be the name of your activity which will be created.
*    **Layout Name:** In further chapters you will read that an activity will always have User interface with it. Since ADT is creating activity for you, it will also create a layout for you to bind it with the activity.
*    **Navigation Type:** in future chapters you will read about different navigation which you can put it in your apps like tabs dropdown etc. This option lets you choose the navigation type for your activity.
Click Finish

Once you click Finish ADT will create your new project and will open Java code and Layout code for you. 

<br/>
<%= image_tag "hello-android/screen_new_project.png", alt: "Android Hello World  New Project", title: "Android Hello World New Project" %>

## Running your Application

### 1. Run as Android App 

Right click on your project in **Package Explorer** window on the left and choose **Run As => Android Application** as shown below.

<br/>
<%= image_tag "hello-android/deploy-app.png", alt: "Android Hello World Deploy", title: "Android Hello World Deploy" %>
<br/>
<br/>

You can also choose to deploy the app by clicking on the **green play button** on the top bar

<br/>
<%= image_tag "hello-android/green-play-button.png", alt: "Android Hello World Green Play Button", title: "Green Play Button" %>
<br/>


### 2. Watch deployment preparation

Once you deploy your app, **check bottom-right of Eclipse** for deployment progress. It should say something like `Launching HelloCodelearn: (xx%)`

<br/>
<%= image_tag "hello-android/deployment-in-progress.png", alt: "Android Hello World Deployment In Progress", title: "Android Hello World Deployment In Progress" %>
<br/>
<br/>

Depending on your PC configuration & how recently you have deployed an app, this step will take somewhere around 1 to 10 sec. 

### 3. Deploy on a Device

Once Eclipse has done preparing for the deployment, you will see a popup as shown below. 

<br/>
<%= image_tag "hello-android/noavd.png", alt: "Android Hello World No_AVD", title: "Android Hello World No_AVD" %>
<br/>
<br/>

From here on, you have multiple options. You can choose to 

* Jack in an Android phone, turn on **USB debugging** if not enabled & deploy the app on the phone
* Create a Genymotion emulator & deploy on it
* Create an **Android Virtual Device (AVD)** which ships with the Android SDK & deploy the app in it

> We recommend deploying on phone as the most preferred option. If you do not have an Android phone or you need to test your app on a different Android version, go for Genymotion. AVD is painfully slow option.

If you have multiple options configured, you will see a device chooser popup

<br/>
<%= image_tag "hello-android/android-device-chooser.png", alt: "Android Hello World Android Device Chooser", title: "Android Hello World Android Device Chooser" %>
<br/>
<br/>

Select the device & click 'Ok'. Your app will now be deployed on your device. It will look as below if deployed in an AVD. 

<br/>
<%= image_tag "hello-android/emulator.png", alt: "Android Hello World Emulator", title: "Android Hello World Emulator" %>
<br/>
<br/>

Congratulations. You have successfully deployed your first Android App. 

## Deploying app on phone

You should keep your phone connected to your PC through USB. While deploying the app, your phone would be shown as an option to which you can deploy 

>If you are planning to deploy the Android app to your phone, it is essential to turn on USB Debugging in your Android phone.

* On most devices running Android 3.2 or older, you can find the option under **Settings > Applications > Development**.
* On Android 4.0 and newer, it's in **Settings > Developer options**.

> Watchout: On Android 4.2 and newer, Developer options is hidden by default. To make it available, go to "Settings > About phone" and tap Build number seven times. Return to the previous screen to find Developer options.

## Genymotion emulator setup

Depending on your computer, the emulator images of the Android platforms provided by Google can be quite slow. If you're interested in using a faster (albeit more experimental) emulator, check out Genymotion.

 * Head over to [genymotion.com](http://genymotion.com/), sign up for a free account and download and install Genymotion ( You may need to install VirtualBox if you're not using Windows - Refer the [Genymotion user guide](https://cloud.genymotion.com/page/doc/) ).

 * <p>Launch Genymotion and download a virtual device. We recommend **Motorola Moto X - 4.4.2 API 19**</p><p><%= image_tag "android_setup/virtual_device.png", alt: "Genymotion virtual device", title: "Genymotion Virtual Device" %></p>
 
 * <p>Install the Genymotion Eclipse plugin in Eclipse by opening Help → Install new software → Add and enter <pre>http://plugins.genymotion.com/eclipse</pre> and follow the next steps.</p><p><%= image_tag "android_setup/genymotion_eclipse_plugin.png", alt: "Genymotion Eclipse plugin installation", title: "Genymotion Eclipse plugin installation" %></p>
 
 * <p>After a restart, Eclipse should now show a new icon of Genymotion.</p><p><%= image_tag "android_setup/genymotion_icon.png", alt: "Genymotion Virtual Devices Manager icon in Eclipse", title: "Genymotion Virtual Devices Manager icon in Eclipse" %></p><p>You can launch a Genymotion emulator by clicking on it and choosing the virtual device you previously installed</p><p><%= image_tag "android_setup/genymotion_avd_manager.png", alt: "Genymotion Virtual Devices Manager", title: "Genymotion Virtual Devices Manager" %></p>
 
 * <p>You can run an Android application project on the Genymotion virtual device by clicking the "Run" icon or right-clicking the project → "Run as" → Android App Codelearn</p><p><%= image_tag "android_setup/genymotion_emulator.png", alt: "Genymotion Virtual Device", title: "Genymotion Virtual Device" %></p>
 
For more information, check out the [Genymotion user guide](https://cloud.genymotion.com/page/doc/)

<div class="alert alert-info">When you run an Android app, don't expect the Android emulator or the Genymotion emulator to be brought to the foreground. Refer to the output console and open the emulator to see your app in action</div>


## Deploying on AVD

Android gives an option to test your application against any version of android,  without depending on a real device. This is possible through Android Virtual Device (AVD), which is an emulator or a test device that runs on your machine. 

Let's see how we can create an emulator. 

*    Click on Windows in menu option, and choose Android Virtual Device Manager. 

AVD manager dialog will open, in recent versions of ADT you get 1 avd pre bundled. But in case of old ADT, you might not have any AVD. 

<br/>
<%= image_tag "hello-android/avd_manager.png", alt: "Android Hello World AVD Manager", title: "Android Hello World AVD Manager" %>

Lets create a new AVD of our own. Click on New in AVD Manager to see AVD Creation dialog. 

<br/>
<%= image_tag "hello-android/create_avd.png", alt: "Android Hello World Create AVD", title: "Android Hello World Create AVD" %>

Let’s go through the elements of this dialog 

*	**AVD Name:** is the name of your emulator 
*	**Device:** this is the Size of the screen which you want. In case your emulator is not opening up reduce the size to make it work
*	**Target:** What version of Android you want in your emulator, choose the latest version, don’t choose the Google API version
*	Leave all other options to default, 
*	You can give the size of an SD card if you want 

Click on OK to create the AVD

<div class="alert alert-danger">Make sure your RAM size in AVD is not too high corresponding to the RAM available on your system. A good thumb rule is to allocate no more than a quarter of your system RAM. On the lower end, 200 MB is a fair amount of RAM for the AVD</div>

Once the AVD is created, you will see your newly created AVD in the AVD manager. Now you can go and launch your application to run in your new AVD



## Android Folder Structure

Till now we have seen how to create a hello world application and test it in new emulator. Now, lets see how android folder structure looks like. Before getting deep into the folder structure, just click on the down arrow present at the left of your project to expand it to see all your folders in the project. 
<br/>
<%= image_tag "hello-android/folder_structure.png", alt: "Android Hello World App Folder Structure", title: "Android Hello World App Folder Structure" %>

Lets go via each folder and see what each one is use for 

*    **src:** src is your main folder in which all your JAVA code will go. All your android application logic will go into SRC folder as java class files 
*    **gen:** gen is a system folder which you should not touch, Android SDK uses this folder to generate mapping of resource files.  
*    **R.java:** you see a R.java file in gen folder, this file is mapping of your resources into code. This is system generated file and you should not modify or delete it 
*    **assets:** asset folder is use to keep files which you want to pre bundle with your application like sound, mp3, fonts etc 
*    **bin:** this is the standard java bin folder where all your compile classes will go 
*    **libs:**  In android you can use libraries build by others to make the process of developing application faster, all your libraries(.jar) files goes into lib folders
*    **res:** res is very important folder for your android app, all your images, styles and layouts go into resource folder. Let us go 1 by 1 into each folder and see what it is used for 
*    **drawable-xxxdpi** all this folders represent different screen sizes for android devices, this folder will contain all your images which you want to use into your android app, the reason to have multiple folder is to get the same image in different size so proper image can be used based on screen size 
*    **layout:** layout will contain all your UI for any application, this will have XML files in which your UI is defined 
*    **menu:** this folder will contains menu XML, menus are simple hidden information for any app which appears when the user press menu button on their phone
*    **values-xxx:** values folder contains all your strings, dimensions and style for any application, the reason to have multiple folder is based on screen size and android version , but you can change these values. 
*    **Manifest.xml:** Manifest is the settings file of your android app, as you have read earlier, each application can have only 1 manifest file. This contains all your application settings like name, permissions etc

Ignore all other files 

> Watchout: Lot of time during your project work you might get R.java error, the best way to resolve that is to do a clean build and make sure correct R is imported in your activity

## Other Tools: 

When you install android plugins or start using ADT you get a few more tools. Let's see some other tools which are available in ADT.  

### Console

The console gives you all the information about events happening in ADT. Whether you launch an application, generate an apk, create new application or resources, all information is printed in the console. 

To open the console if it is not visible you can open it from Windows-> Show View -> Others -> General -> Console

<br/>
<%= image_tag "hello-android/console.png", alt: "Android Hello World Console", title: "Android Hello World Console" %>

Console helps in knowing what is happening in your development environment 

### LogCAT
<br/>
<%= image_tag "hello-android/logcat.png", alt: "Android Hello World LogCat", title: "LogCat" %>

An excellent tool which comes with ADT is logcat. It gives you all information about what is happening in your Android Emulator or Phone if you are using a android phone for testing your applications

Locate displays filterable messages that show you what is happening in your android device. You can filter messages with verbose, warnings, errors etc. 

Logcat is the place where all your errors in application will be printed, whenever you launch your application you can refer logcat to see what is happening, in case of any error or force close all your error message will be printed on logcat. 

To open the LogCat if it is not visible you can open it from Windows-> Show View -> Others -> Android -> LogCat. Don't use the Deprecated logcat

### DDMS
<br/>
<%= image_tag "hello-android/ddms.png", alt: "Android Hello World DDMS", title: "DDMS" %>

DDMS is a very powerful perspective which comes with ADT, it lets you control and access different information from a device or emulator. To open DDMS, go to Windows -> Open Prespective -> DDMS

*	get heap dump
*	Know threads and their information 
*	Change Network to do performance and load testing 
*	Explore files via file explorer 
*	Get system information like CPU load, memory usage etc 

DDMS also comes with a nice tool of emulator control, this option lets you control the emulator behavior, here are few things which you can do with this

*	Send a Voice call mimicking a specific number 
*	Send SMS to emulator, this comes in handy when you want to test some capabilities based on SMS 
*	Mock GPS location to test your application if it is using GPS 

In this chapter, we have learned how to create hello world application and how to launch the same using emulator. Also we saw how to create a virtual device. We also got to learn about the android project folder structure and had a glimpse of the tool to assist us in the faster development.

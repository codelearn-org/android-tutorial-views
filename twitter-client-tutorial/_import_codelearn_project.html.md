In this setup lesson, you will be provided with an app that you can download & try the current module. This is helpful if you are directly jumping to this module or if you have messed up your app somewhere & want to start afresh but not from the start of the Twitter App tutorial.

> If you have been following our Twitter App tutorial from the start & has a perfectly running app at the end of the previous module, you may simply skip this setup lesson.

1. <%= link_to "Download CodelearnTwitterApp project", download_import_project_zip_path(@current.lesson_module.lesson.token, @current.lesson.token) %> and import it in Eclipse. This is the app a user would have built if he has followed our tutorial till the end of the previous module.

	Note that if you already have CodelearnTwitterApp project in your Eclipse, you will not be able to import this project in the workspace. You would either need to remove the previous project by deleting it or unzip the downloaded project & change the project name inside `<name>CodelearnTwitterApp</name>` in .project file & then import the project into Eclipse.

	**Possible Error - Unable to resolve 'android-19'** - The CodelearnTwitterApp project takes the latest Android API by default. Most probably, you are seeing this as your Android SDK is old. Quick fix is - checkout the Android API version in [Android SDK Directory] -> sdk -> platforms directory & modify `target=19` in **project.properties** file to your Android API version. 

2. If this is your first time with Codelearn App tutorial, we would like to tell you about the Custom Eclipse Launcher that we have built to let you evaluate your app at the end of a tutorial lesson. 

	On the Eclipse project, **[right click on CodelearnTwitterApp] -> Run As -> Android App Codelearn ** or simply hit the **Run button** on the top of Eclipse which will show the popup below. *Remember to choose 'Android App Codelearn' option as against 'Android Application'*. The Launcher will do the normal Android App deployment & will send a copy of your app to our server for evaluation.

<p>
<%= image_tag "twitter-client/plugin-newproject-run-menu.png", alt: "Codelearn Run Configuration", title: "Codelearn Run Configuration" %>
</p>


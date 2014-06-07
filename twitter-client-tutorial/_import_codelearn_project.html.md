# Import Codelearn Twitter Challenge Project

In the previous level, we installed Codelearn Eclipse Plugin.

Follow the steps below to import an Android project, which will be used by you for the rest of the challenge.

1. <%= link_to "Download CodelearnTwitterChallenge Eclipe project", "/android-tutorial/#{@current.lesson_module.import_file}" %> and import it in Eclipse.

2. From next lesson onwards you will be building your application on this imported project. So to run it from next lesson you can either choose to **[right click on CodelearnTwitterApp] -> Run As -> Android App Codelearn ** or simply hit the **Run button** on the top of Eclipse which will show the popup below. *Remember to choose 'Android App Codelearn' option as against 'Android Application'*. Now you can go to the next lesson.
<p>
<%= image_tag "twitter-client/plugin-newproject-run-menu.png", alt: "Codelearn Run Configuration", title: "Codelearn Run Configuration" %>
</p>
## Possible Errors

**1. Unable to resolve 'android-19'** - The CodelearnTwitterApp project takes the latest Android API by default. Most probably, you are seeing this as your Android SDK is old. Quick fix is - checkout the Android API version in [Android SDK Directory] -> sdk -> platforms directory & modify `target=19` in **project.properties** file to your Android API version. 

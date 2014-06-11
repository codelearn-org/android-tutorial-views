#Android Development Setup

In the first chapter, we have seen fundamentals of an android app, from activities to services and broadcast receivers. This is an important building block and essential to learn if you want to make good android apps.

In next few chapters, we will look into each concept in detail while   doing some exciting hands on coding.

Before diving deep into the upcoming chapters, we must prepare our development environment to try out sample applications and concept lessons. Let's get started.


##Prerequisite 

Android development does not require any specially built hardware. The development environment is based on Eclipse IDE and works on any platform. Here are some prerequisites to help you decide the version to be installed :

* OS: Android IDE works on Windows XP, 7, 8, Linux, and MAC OSX.
The Minimum requirement is Java (JDK 6)


##Download Links

* For Java - [refer here](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)
* For ADT (Android Developer Tool) [please check here](http://developer.android.com/sdk/index.html). Click on 'Download the SDK' button

> Watchout: Android requires complete Java Development kit(JDK) and will not work with Java Runtime Environment(JRE) alone.

##Android Development Setup Kit

The following video will guide you through the download and installation process of JDK and ADT . Even though this video is for windows 7, the steps are mostly same for all other platforms. 

<iframe width="560" height="315" src="//www.youtube.com/embed/SFGF3_r9YIA?list=UUbL5gei-5kK8hHf5q3andnw" frameborder="0" allowfullscreen></iframe>

<br/>


Lets learn to setup step by step by following the video.


### JDK Setup

> You can check if you have JDK already installed on your computer. Go to Command line and type 'javac -version'. If you get a version which is 1.6 or above, then you can skip this JDK Setup step.

Go to [this JDK download link](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html). Select appropriate Java SE Development Kit based on your Operating System and its version - 32 bit (X86) or 64 bit (X64).

Once the file is downloaded, double click on it to start the installation. Let the default options be selected, and follow the wizard to complete the installation process.

> Watchout: A lot of times Oracle JDK installation wizard is bundled with ASK toolbar. Make sure you notice the wizard and uncheck the installation of ASK toolbar to save yourself from bloatware. 

### ZIP utility

The ADT package which you downloaded from developer.android.com is compressed, you need to extract the package in order to access the setup files. Linux or MAC users can skip this section. For windows users, if you have used zip utilities such as WinZIP, WINRAR etc. , you can skip this section too.

If you do not have an unzip software and are using Windows, follow these steps :

* Go to [7 zip download link](http://www.7-zip.org/download.html) and download .msi file for your windows machine.
* Double click on the msi file and install the 7zip software.
* When asked for associating known extensions, let the default option be selected and finish the installation. 


###ADT (Android Development Toolkit)

Now that we have the JDK and Unzip utility installed, let's go and install the ADT.

*Go to the file which gets downloaded from developer.android.com. The file name will start from **adt-bundle-**
*Right click and unzip the zip packaged. In Linux or MAC you can use the unzip command on the terminal
*You will get a new folder with name adt-bundle-xxxx created. The exact name will depend on your OS and its version (32/64 bit). 

> Watchout: In the above video you see the presenter doing a cut paste after the above step, you can skip that part if you do not want to change the location of your ADT installation. If you want to move your setup to a different location, you can do cut and paste.

When ADT is installed you will notice that the installation is self contained. This means you just need to have the ADT folder to run the development environment.

##Understanding ADT Folders

Now that we have unzipped the ADT installation, lets go inside the ADT folder to see its contents.

###Eclipse Folder

As discussed earlier, ADT is nothing but Eclipse IDE with Android plugin already installed and configured for you. Eclipse folder contains the executable to launch our development environment.

If you double click on eclipse folder, you will see various other folders. These folders are required to run the executable properly

Double click on Eclipse.exe or Eclipse Application file to launch the development environment.


###SDK Folder

SDK folder will contain all your android related installations. This is the folder which has your Android SDK, tools, and different Virtual device images. 

You will not be accessing this folder explicitly. But it is internally referred by eclipse to find the android SDK path. 

###SDK Tools 

There is a Tool folder inside SDK, which comes pre-bundled with a set of useful tools to perform a variety of interesting operations like log analysis, systrace, layout viewing etc. While covering some advanced concepts later, we will learn to use these tools.  

Now that you have your Android IDE up and running, follow the video integrated at the top of this lesson to understand various features of IDE and try to learn things you find interesting. 

> You can skip the above video after 8 minutes. 

Great then ! You can proceed to the next chapter for creating your first hello world application !

> Caution :  For Windows 8 , the installation instruction doesn't change much, but sometimes you might encounter some problem in correctly running the ADT. This is mostly due to incorrect installation of the JDK, make sure you install the correct version of JDK by choose the correct version (32-bit or 64 bit).

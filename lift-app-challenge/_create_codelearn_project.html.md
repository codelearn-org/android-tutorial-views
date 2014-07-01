
This challenge involves creating a basic car lift app for office-goers. We will be fetching the list of lifts and submitting new lifts using network calls.
In this level, we will create a new Android project, **CodelearnLiftApp** with the following attributes:
* **Package name:** org.codelearn.liftapp
* **Minimum SDK required:** 9 (Android 2.3)
* **Target SDK :** The latest android SDK 
* **Initial Activity:** The initial activity of the app should be called **MainActivity**
 
## Designing the basic layout

The app should now have MainActivity as the initial screen. We need to design the basic layout for MainAcitivty in it's corresponding layout file, **main_acitivity.xml**. We need to link two other activites from the MainActivity to create/edit a lift and fetch the list of all lifts created by other users.


##Tasks

1. Create two blank activites called **CreateLiftActivity** and **LiftListActivity.**
2. Create two buttons in the MainActivity layout with ids, **R.id.create** and **R.id.skip** which launch intents to the **CreateLiftActivity** and **LiftListActivity**, respectively.

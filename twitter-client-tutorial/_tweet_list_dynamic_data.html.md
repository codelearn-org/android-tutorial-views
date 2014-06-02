# Dynamic Data for Tweet List Screen

We are done storing login data from previous lessons. It is time to handle data for Tweet List Screen. 

In this module, we will add the feature - each tweet item should have different data. We will create a Tweet model which will store the data corresponding to each tweet. In subsequent lessons, we will learn how to serialize & read/write the Tweet model object array to a local file. 

> In this module, you will going to learn how to access & modify data in a ListView & best practices of storing data using models in Java/Android. 

1. <%= link_to "Create Tweet model", app_tutorial_lesson_with_token_path(@app_name, AppLesson.find_by_number(@current_lesson.number + 1).lesson.token) %> - A quick intro on how data models are created in Java & why we need it for our case followed by assignment to actually create it. 

2. <%= link_to "Populate the Tweet model & use it in the Activity", app_tutorial_lesson_with_token_path(@app_name, AppLesson.find_by_number(@current_lesson.number + 2).lesson.token) %> - Once the model is created, it is populated & the data with dummy data & the data is shown on the TweetListActivity. 

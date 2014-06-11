
Reading and writing tweets from/to file are time consuming tasks. These tasks should not be handled in the main thread so as not to give a *hung app* experience to the user.

You can always compensate the delay by showing a loading/spinner but that is a bad app design. It is like blocking the app flow. The code should be written in such a way that blocking the app flow should only happen if the user's next action is dependent on the current action. The choice is personal on the part of programmer too. For example - fetching tweets from network should never be blocking but publishing a tweet can be. The user might or might not want to wait till the tweet is published. If you do not block the app, you should show some kind of notification which will let user come back to the publish tweet screen to publish it again. 

In the last lesson, we were reading & writing the tweets in the same thread. In this lesson, we are going to move the steps of creating new tweets & overwriting the cached file into a separate thread using **AsyncTask**.
<div>
<% lessons_of_mod_5 = AppLesson.find_all_by_module_number(5) %>
<% count = 1 %>
<% lessons_of_mod_5.each do |l| %>
	<%= count %> .
	<% count = count + 1 %>
	<%= link_to l.lesson.title, app_tutorial_lesson_with_token_path(@app_name, l.lesson_module.lesson.token, l.lesson.token) %>
		<br/>
	<% end %>
</div>


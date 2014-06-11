
We are done storing login data from previous lessons. It is time to handle data for Tweet List Screen. 

In this module, we will add the feature - each tweet item should have different data. We will create a Tweet model which will store the data corresponding to each tweet. In subsequent lessons, we will learn how to serialize & read/write the Tweet model object array to a local file. 

> In this module, you will going to learn how to access & modify data in a ListView & best practices of storing data using models in Java/Android. 

<div>
<% lessons_of_mod_3 = AppLesson.find_all_by_module_number(3) %>
<% count = 1 %>
<% lessons_of_mod_3.each do |l| %>
	<%= count %> .
	<% count = count + 1 %>
	<%= link_to l.lesson.title, app_tutorial_lesson_with_token_path(@app_name, l.lesson_module.lesson.token, l.lesson.token) %>
		<br/>
	<% end %>
</div>

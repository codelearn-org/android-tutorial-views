# Setup Virtual Assistant in 5 minutes

To assist you better during the development cycle, we have created an Eclipse plugin that tests your app at every step to ensure you are doing it right. Our intent is to be able to show you very relevant error messages (& possible solution).

Please follow our step by step process to get started. 

<h2> 1. Download & Unzip Android SDK <small><a href="http://developer.android.com/sdk/index.html#download", target="_blank", style="color:#57A3E8", id="sdkdnld" >download link</a></small></h2>
Download Android SDK from [official Android SDK download page](http://developer.android.com/sdk/index.html#download). **You just need to download & unzip the SDK.**

> You need to have the latest Android SDK installed on your computer. Ignore this step if you already have the latest SDK.

<h2> 2. Download Virtual Assistant <small><%= link_to "download link", plugin_getzip_path, target: "_blank", style: "color:#57A3E8", id: "pluginziplink" %></small></h2>
<ol style="text-align:left">
	<p>Its around 4 MB in size, thus very light weight.</p>
	<li> <strong>Unzip the downloaded dropin-dependencies.zip file</strong>. You will see 4 files inside it.</li>
	<li>
		<p><strong>Copy the extracted files to the dropins directory</strong> under <strong>[Unzipped Android SDK Directory] -> [eclipse directory] -> [dropins directory]</strong>. The dropins directory exists for you to manually 'drop' an Eclipse plugin there.
		<p><%= image_tag "twitter-client/dropins-location.png", alt: "Dropins with all the jars copied", title: "Dropins with all the jars copied" %></p>
		</p>
	</li>
	<li> <strong>Start Eclipse</strong> (restart if already running) by double clicking Eclipse executable <strong>[Unzipped Android SDK Directory] -> [eclipse directory] -> [Eclipse]</strong>. In the above image, it is the file with green icon below dropins directory. 
		<small><ul>
			<li>You should see an <%= link_to "Eclipse popup to select workspace", image_path("twitter-client/plugin-installation-workspace.png"), target: "_blank" %>.</li> 
			<li>Once done, you will see a message in your Eclipse intimating that data has been sent to the server. Come back here & you will see a popup intimating this lesson is done.</li>
		</ul>
		<p>
		<div class="row-fluid ac">
			<div class="span6">
				<div class="vertical-align-me">
					<%= image_tag "twitter-client/plugin-installation-welcome-popup.png" %>
					<p>Eclipse popup</p>
				</div>
			</div>
			<div class="span6">
				<%= image_tag "twitter-client/browser-popup.png" %>
				<p>Browser popup</p>
			</div>
		</div>
		</p>
		</small>
	<li>Once a lesson is complete, the <%= link_to "Next >", "#", class: "btn btn-inverse" %> button at the bottom of the lesson gets activated. Also a green bar with <%= link_to "< Prev", "#", class: "btn btn-inverse" %> & <%= link_to "Next >", "#", class: "btn btn-inverse" %> buttons appear on the top of the lesson with a message telling that you have completed the lesson.</li>
    <p><%= image_tag "twitter-client/green-navigation-bar.png" %></p>
</ol>

<div class="alert alert-info">More elaborate setup instructions are available in the <b><%= link_to "Android Setup page", android_concept_lesson_path("android-setup") %></b></div>

## Troubleshoot

**1. Java Runtime not found while launching Eclipse.** Android SDK needs Java SDK to run. You will see this error while launching Eclipse first time. Please refer <%= link_to "Java SDK Installation Guide", android_concept_lesson_path("android-setup") + "#Setup-Guide-JDK-Setup", target: "_blank" %>

**2. No popup in Eclipse post restart.** 
<ol>
	<li>Make sure that you copied the plugin files directly under dropins directory. Do not create any intermediate folder between dropins & the files.</li>
	<li>If you had Eclipse already & you installed ADT plugin or if either Eclipse or ADT plugin is upgraded, sometimes our plugin fails to work in the setup. You are advised to download the latest ADT bundle. You may keep your existing Eclipse with ADT as it is as the ADT bundle needs no installation. You simply need to unzip & use the Eclipse from within the ADT bundle.</li>
</ol>

**3. No popup on the website.**
<ol>
	<li>Try refreshing the page. If the green bar appears on the top intimating the lesson is done, you are good.</li>
	<li>There is a possibility that your plugin & browser have become disconnected probably because you downloaded the plugin from a different browser or you cleared your browser cookie. Follow the steps to check it.
		<small ><ol style="margin-left: 3.2em">
			<li>Open config.properties inside dropins (part of plugin) in a text editor.</li>
			<li>Check the value of <b>id</b> field in it. Append <code>?id=true</code> to this page url & reload to view the id on the top right of the page.</li>
			<li>If they are different, set the id field in config.properties to the id value shown in your browser. Set <b>executedOnce</b> value to false in config.properties. Save the file & restart Eclipse.</li>
			<li><b>id</b> field links the plugin with the browser. If you have downloaded the plugin from a different browser or if you end up clearing your cookies, you will get a different id in the browser as against the one in the plugin.</li>
		</ol></small>
	</li>
</ol>

**4. Connection to http://www.codelearn.org refused.** It is an error due to proxy settings. Eclipse is unable to communicate the data to our server. Follow the steps
<ol>
	<li>In your Eclipse, go to ADT -> Preference . Inside preference popup, look for General -> Network Connections.</li>
	<li>Setup proxy by following <a href="http://www.mkyong.com/web-development/how-to-configure-proxy-settings-in-eclipse/" target="_blank">Mkyong tutorial</a></li>
	<li>Make sure you clear Socks proxy <a href="http://stackoverflow.com/questions/5857499/how-do-i-have-to-configure-the-proxy-settings-so-eclipse-can-download-new-plugin" target="_blank">as mentioned on the stackoverflow thread</a>.</li>
	<li>Open config.properites inside dropins in a text editor. Set <b>executedOnce</b> to false. Save the file & restart Eclipse.</li>
</ol>

**5. 'Class org.apache.http.entity.mime.MultipartEntity does not implement the requested interface org.apache.http.HttpEntity'. **If you find this in ErrorLog of your eclipse, most probably your Android SDK is old. To resolve this you need to download latest Android SDK from <a href="http://developer.android.com/sdk/index.html#download", target="_blank", style="color:#57A3E8", id="sdkdnld" >this link</a></small>. There is no need to uninstall your current eclipse. Download the latest SDK, extract the zip and you are good.

**6. 'App can not be opened because it is from unidentified developer' issue in Mac.** If this is your first time with Android SDK, launching Eclipse will show you a Mac popup. Follow the <a href="http://osxdaily.com/2012/07/27/app-cant-be-opened-because-it-is-from-an-unidentified-developer/" target="_blank">osxdaily link</a> to change your computer's security settings.


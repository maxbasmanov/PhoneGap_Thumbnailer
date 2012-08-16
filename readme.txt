<b>This plugin is made for Phonegap for Android to create Thumbnails for images or video.</b>

<b>Why:</b>
When using PhoneGap or writing any HTML application, application uses 
local domain "" or "file:///android_asset/www/index.html" or "http://127.0.0.1".
When You try to makke photo or video than are saved to local(EXTERNAL) storage
and access image or video canvas to save it to thumbnail (Popcorn can do it) You 
will get security error of "Same domain" issue because of different domains of
application and files.

To fix this issue i have made this plugin using native Android class ThumbnailUtils.

<b>It consist:</b>
- Android native code plugin
- JavaScript plugin part to include into phonegap project

<b>Installation:</b>
1. Copy Thumbnailer.java into org/apache/cordova/api/Plugin folder of Your project.

2. Copy thumbnailer.js into assets/www/js of Your project.

3. Add the following string to res/xml/config.xml into <Plugins> section
<plugin name="Thumbnailer" value="org.apache.cordova.plugin.Thumbnailer" />

4. Clean and Rebuild Your project

You are ready to use.

Usage:
Plugin has two functions for creating thumbnails for video and image files.
Thumbnail is created and adds ".jpg" to the end of original file path.

To create image thumbnail use this:
<code><br>
//Create and get Image Thumbnail<br>
window.plugins.thumbnailer.createImageThumbnail(pathToImage,<br>
	function(thumbPath) {<br>
    		alert(thumbPath); // should alert created thumbnail image path<br>
 		if (thumbPath.toLowerCase().indexOf("file://")!=0){<br>
			thumbPath ="file://"+thumbPath; <br>
		}<br>
 		var thumbFileName = thumbPath.substring(thumbPath.lastIndexOf("/")+1);<br>
 		var origFileName = thumbFileName.substring(0,thumbFileName.lastIndexOf("."));<br>
 		var origFilePath = thumbPath.substring(0,thumbPath.lastIndexOf("."));<br>
    		<br>
		//do something with files<br>
			<br>
 		});<br>
</code>

To create video thumbnail use this:
<code><br>
//Create and get Image Thumbnail<br>
window.plugins.thumbnailer.createVideoThumbnail(pathToVideo, <br>
	function(thumbPath) {<br>
   		alert(thumbPath); // should alert created thumbnail image path<br>
 		if (thumbPath.toLowerCase().indexOf("file://")!=0){<br>
			thumbPath ="file://"+thumbPath; <br>
		}<br>
 		var thumbFileName = thumbPath.substring(thumbPath.lastIndexOf("/")+1);<br>
 		var origFileName = thumbFileName.substring(0,thumbFileName.lastIndexOf("."));<br>
		var origFilePath = thumbPath.substring(0,thumbPath.lastIndexOf("."));<br>
    		<br>
		//do something with files<br>
			<br>
 		});<br>
</code>
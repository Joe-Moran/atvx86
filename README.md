# atvx86

Android TV based on Android-x86  -  Updated by Foxtrotdragon to Android Oreo

This assumes you are using vanilla android-x86 oreo  

Edited the original files from android-x86 8.1 based on files from Ric96

Android TV based on Android-x86


Step 1: Clone android-x86 Oreo:
	In a terminal type;
	
	$ mkdir android-x86
	$ cd android-x86
	$ repo init -u git://git.osdn.net/gitroot/android-x86/manifest -b $branch
	$ repo sync --no-tags --no-clone-bundle



Step 2: Replace files:
   Copy the "common" inside the device folder to androidtv-x86/device/generic/ and overwrite any existing files
   
Step 3 Edit manifest to add sync necessary files and updated : 
	(assuming vanilla android x86) navigate to /.repo/manifests/android-x86.xml 
	replace <remove-project name="device/google/atv" />
	with <!--remove-project name="device/google/atv" /-->
	
	In terminal;
		$ repo sync --no-tags --no-clone-bundle
     
Step 4: 
   Find latest version of Launcher binary in following link. (make sure you download oreo binaries)
   https://developers.google.com/android/nexus/drivers#fugu
   extract tgz onto the source, then run the script file, which will download; 
   leanback launcher, remote service and tv service to vendor/google/...
   
   Source: https://github.com/peyo-hd/device_brcm_rpi2/wiki#how-to-apply-android-tv-leanback-launcher
   
Step 5:
   Copy and Replace MainFragment.java to ``` packages/apps/TVSettings/Settings/src/com/android/tv/settings/ ```
  
Step 6:
	in a terminal ; 
	
	```	$ . build/envsetup.sh
		$ lunch
			Select what version you use ex android_x86_64-userdebug
			
		$ m -jX iso_img
			X= number of physcal cores + 1 IE ryzen 1600 6 core 12 thread
			m -j7 iso_img ``` 

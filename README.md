# Debugging-Global-Shutter-Camera-in-Win-System
Debugging global shutter camera for high-speed capture
If you need to conduct experiments or debug a high frame rate camera to capture high-speed moving objects, capture video streams, and use it, there are many ways to achieve it. You need a high frame rate global shutter camera as a prerequisite. You can complete the functions by programming yourself, or you can also use some tools to easily and quickly complete them. This article is about the latter.
This article explains under the Windows 10 system, similar to other Windows systems.
1. Download ffmpeg from the official website
Go to the Download FFmpeg website（https://ffmpeg.org/download.html） and click to download the Windows version of FFmpeg (click on the green line at the bottom left)
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/72e991e2-09ea-464c-a7bc-5f2c11dc1d9c)
Select a version to download from the first green box of release builds
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/fcbb7e28-3461-40e8-878c-bd1dd5461ed7)
2. Configuration
After downloading, unzip the compressed file:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/1d895f70-83a3-497e-890c-e148fb64a12a)
Click to enter ffmpeg, and the following interface will appear:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/f1df3e49-eaf6-4eb1-87fd-fad778fa2e36)
There will be three exe files in the bin file, copy the current address：
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/30f19fb8-e117-44b1-b4bc-137fc7325817)
Open Computer Settings, click on Advanced System Settings in the Properties section, and then click on System:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/33487304-26f2-401b-8f2c-bcf4fe6a322d)
Find information about:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/9c33f881-e30e-4ff3-8fa9-7ba324075cdf)
Pull down to open advanced system settings:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/8c8d9c8e-d3fe-4382-937e-c2ae5a4a45f3)
Open environment variables:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/74315870-15a8-4548-b1ed-f354a447f15f)
Find Path in the system variable:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/264abf2c-3065-45f7-afba-701652b6766c)
Double click to open, click on New:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/11940a3b-be70-4ee2-b4f0-c52f23fb175d)
Paste the first copied address back in and click OK:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/d4060358-5c1f-4e3e-8daf-39971ab96f22)
Then click three more to confirm.
After saving, open any shell and enter ffmpeg version. If the version number is output normally, it indicates successful installation.
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/287bf43e-2a69-434d-a929-b352ea84849a)

3. We use videocap. exe to debug parameters and capture videos (tracking the target is the rotating fan)
When static:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/669d6383-58a4-4864-9c1c-4b4205bfe5dc)
Automatic exposure parameters:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/27e66567-ff8e-4b2a-b43b-ef6518a3784d)
capture->start capture,In a few seconds，stop capture
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/8a0b564e-1f98-4c8f-a0da-5683fa81a309)
Obtain video data, which can be named 123.avi,Obtain each frame of the image using the ffmpeg tool. The command is: ffmpeg -i C:\Users\Administrator\Desktop\123.avi data-0/%010d. png
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/6e4f1c70-17e9-49e9-a7c8-441d52cc7b9e)
The analyzed data is as follows:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/785e80d9-5cc0-4fa8-b81b-ba4c9479d3d5)
Of course, due to the unadjusted parameters, the rotating blades were not captured：
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/09ce8198-b989-477b-8b16-cc050f5667d6)
Adjusting parameters:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/b77bc63e-549e-44e0-a266-92138bf110ec)
Enhance brightness:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/cccb63fc-1a52-4e77-9709-4d9ce4d55204)
Repeat the same parameters as before, intercept the video stream and use ffmpeg to process each frame of the video:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/be883d7e-35fd-4491-b5dc-3708ae84eeda)
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/84b3f2e8-fcee-46ad-84d1-9245810981d2)
The effect has improved, continue to adjust the exposure parameters:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/3f7346c1-bc61-4163-b54b-2e175d773275)
Due to the short exposure time, we added some supplementary lighting and obtained the following images:
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/56009aca-83a2-4efc-a6f6-e9d7fb1f841d)
![image](https://github.com/Mike-chunsheng/Debugging-Global-Shutter-Camera-in-Win-System/assets/169350690/2fe19e6d-feba-454f-9a86-f40511079f84)
Improved image capture.

If you need to further reduce the exposure time, you will need more supplementary lighting to complete it. You can try it yourself




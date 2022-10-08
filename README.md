# Logs

### Definition
Record of an activity during the work

### Structure of a log
A log contains,
- Unique ID
- Time when it recorded
- Date when it recorded
- Duration it took to complete 
- Audio file path of the log
- Text of the log

### Properties of a log
- The text of the log can be edited
- A  log cannot be deleted when it is in a sequence of a routine
- It allows only owner to access the audio path

# Routine

### Definition
A Sequence of activity regularly followed

### Structure of a routine
A routine contains,
- Unique ID
- Name of the routine
- Time when it's created
- Date when it's created
- Array of sequenced activity
- Version of the routine
- Owner  ID

### Properties of a routine
- The routine created cannot be edited
- The routine can be deleted. 
- The text of the routine activity(log) can be edited
- There can be multiple version of the same routine.

# Routine group
It's a collection of routines.  For a team, the routine group is tagged with domain id.  For a single person, the routine group is tagged with the user id.  The routine group is maintained in the realtime nosql database.  every changes made by the owner of the routine is updated at instance.  Changes of a routine can only done by the owner of the routine.  Note that, domain id is checked whether it is private or public and the audio of the activity is not shared.  Only private domain id is allowed for team.  The routine group is synced within team after log in.  Every time a routine is created or deleted from the device, it is synced with the database.  If the single user log into another device then his/her routine are synced.

# Hands free setup and requirement
After log in, the app asks to **nod the head** of the user to check whether your Air pod is connected with the device.  Next it asks to enable all the Siri shortcuts required.  Next it asks required permission to continue.  If the device iOS version is 16.0 then the Siri shortcuts are enabled automatically(Zero user setup).  The app will check for the iOS version.

# Create routine
After Hands free setup, the user will view a Siri Tip saying to **create routine**,  After saying the Siri suggested command, it asks for the  routine name.  After saying the routine name to the Siri, it checks for whether the routine is already available or not in the routine group.  If the routine is already available then it is mentioned as latest routine.  If the routine is not available then it is  mentioned as root routine.  After checking, a screen is opened and a Siri Tip saying to **add activity** for the routine.    Every time when the add activity Siri command is said the microphone function is triggered and starts to record the activity said by the user and converted the audio into text using the speech recognition service.  With the text, audio path, time ,date and duration taken the activity is logged.  If the mic and speech recognition permission is not provided then it prompts for the permission when the microphone  function is triggered.  If the speech recognition is wrong then the user can say again the activity by tapping the activity.  The routine created are automatically saved and synced with the database.  The duration taken by the activity is shown as linear bar.

#  Guide routine
A Siri tip saying **guide routine** will be shown after successfully creating a routine successfully.  The user can view about the Siri shortcuts in the settings.  After saying the command suggested, the Siri asks the routine name to initiate the guidance.  If the routine is available then guidance is initiated,  else Siri prompts routine not available.  If there are many version of the routine, then latest routine is accessed by the Siri.  A Siri tip saying **confirm activity** will be shown to confirm the activity step by step.  A activity ring is shown when the user is doing the activity.  According to the work status of the activity the colour changes for the linear time bar and activity ring.  There are 3 work status for the activity they are, to do, doing, done.  After confirming the activity the Siri says the next activity to do.  The confirmed activity status is changed to done and the next activity said by the Siri status is converted from to do to doing.  After guidance completion, the Siri will say guidance completed.

# User feedback and bugs
By saying the Siri command, 
- **Send feedback** the user can send the feedback.  The feedback said by the user are collected in the **AWS S3 Bucket** with their identity.  A session is opened with the user identity and response is made.
- **Send bug report** the user can send the bug report.  The bug report said by the user are collected in the **AWS S3 Bucket** with their identity.  A session is opened with the user identity and response is made.

# User analytics
The data are stored in the cloud, so the metrics like log count, user information, user activity can be taken using **AWS lambda** and reports can be automatically generated and sent to slack via slack bot.enter link description here

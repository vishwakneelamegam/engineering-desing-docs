# Content

### Log

#### Definition
Record of an activity during the work

#### Structure of a log
A log contains,
- Unique ID
- Owner ID
- Time when it recorded
- Date when it recorded
- Duration it took to complete
- Audio file path of the log
- Text of the log

#### Properties of a log
- The text of the log can be edited
- A log cannot be deleted, because it is in a sequence
- It allows only owner to access the audio path
- It allows only owner to edit the text of the log

### Routine

#### Definition
A Sequence of activity regularly followed

#### Structure of a routine
A routine contains,
- Unique ID
- Owner ID
- Name of the routine
- Time when it's created
- Date when it's created
- Array of sequenced activity
- Version of the routine

#### Properties of a routine
- The logs of the routine cannot be sorted
- The routine can be deleted
- There can be multiple version of the same routine and note that if the routine is already created by other user in a team, then it is considered as new version.
- It allows only owner to delete the routine
- The routines are stored in the routine group
- empty routines are not accepted

### Routine group

#### Definition
It's a collection of routines

#### Structure of a routine group
A routine group contains,
- Unique ID
- Owner ID
- Array of routines

#### Properties of a routine group
- The routines can be deleted from routine group
- The routine group is maintained in the device locally with core data and realtime nosql database simultaneously
- If any network failure occurs, the latest routine group will be synced with the realtime database on next successful network connection.
- The routine group are instantly updated in the real time database and local core data when any changes made in the routine group

# Users

### User authentication

#### Definition
User authentication verifies the identity of a user attempting to gain access to a team or his/her routine group

#### Structure of user authentication
The user authentication contains,
- Email
- Domain of the Email provided
- First Name
- Last Name
- Owner ID
- Is proxy Email
- Is public Email
- User Count

#### Properties of user authentication
- The proxy email(@privaterelay.appleid.com) provided by the user is not allowed to access the application.  The user will be asked to provide email id.
- If the user provides non proxy email then the domain of the email id is checked whether it is private email or public email
- If the user email is found to be public email(@gmail.com, @icloud.com) then the user is considered as single User
- If the user email is found to be private email(@sailors.ai) then the user is considered as team user
- The user count is measured only for the private email
- The user count should be less than 25.
- Each and every user details provided are stored in the realtime login database
- A Unique owner ID is provided to the user after successful login

### User data store

#### Definition
It is a repository where the routine group of a team or single user is stored and maintained

#### Properties of user data store
- The user data is maintained in the device locally with core data and realtime nosql database simultaneously
- The changes made in the routine are updated instantly in device and in the realtime nosql database
- If the user is single then the data is tagged with the owner ID and maintained
- If the user is found to be a team, then the data is tagged with team domain and owner ID
- The user who created the routine can only make changes and delete the routine
- The audio data is not shared, It is available only in the user local device who created the routine
- If the app is reinstalled and logged in, the user can only get the routine group without audio.  The data in the realtime nosql data base is downloaded and updated in local device.

# Interface

### Siri Shortcuts

#### Definition
It's a macro for executing specific function.  There are four siri Shortcuts to create routine, add activity to a routine, initiate guidance of a routine and confirm activity step by step.

#### Properties of siri shortuct
- Before using the siri shortcut the app says to enable all the shortcut required
- If the iOS version is 16.0 or higher then the shortuct will be enabled automatically
- When the app is initiated it asks for microphone permission and speech recognition permission
- If the iOS version is 16.0 or higher then it shows Siri Tip in the application
- The user interaction will only via with Siri shortcuts
- Only deleting routine, Editing the activity of the routine, Viewing routines can be interacted with touch
- 

# Log Consumable

- A log is record of an activity that happened.
- A log is a dictionary which contains unique id, time, date, log text, duration of the log and it has a dictionary which contains the file path of audio/image/video of the log.
- A log is immutable(cannot make changes after creating).
- After creating the log, it is stored in the routine(A routine is a group of log in a sequence).
- A specific log in a routine cannot be deleted, because it follows a sequence.
- When a routine is deleted, then log related to it are deleted.

# Device Token

- Every time if a user creates logs or delete logs or any changes made to logs, then it is updated to the realtime document logs, tagged with device token and the changes reflets who accessed the data.
- If a user reinstalls the app, their logs will be updated to the device, with the help of device token(if the device data is available in the document logs).
- If the user have share their logs to other user, then they have to share their device token. If they provide the device token, first the system checks whether it's valid then it makes the connection to the realtime nosql cloud and fetches the logs and updates to the device.
- Only 10 shared device token can be accessed with a device.
- If the user removes the shared device tokens then logs relevant to it also removed.
- If any network failure occurs, after successful network connection the latest logs are updated to the cloud.
- The audio/video/images of the log are not shared to others.
- The devices who access the data can only read the logs(can't make changes to it).

# Conversation Threads

- There are four transactional states which is used to create a routine, add logs to a routine, initiate routine guidance and confirm the logs step by step.
- There will be a transactional manager, who manages the transactions happening between Siri and the application. Note : The conversation happening between Siri and user will be handeled by the Siri framework, The siri communicates with the transactional manager only if the conversation is successful, If the transactional manager is in android then it will manages the transactions between google assistant and the application.
- The transactional manager receives the action to do from Siri, which is said by the user and performs the action.
- The transactional manager is a singleton, so it can perform any functionality from any environment.
- Transactional manager checks if the transactions dependant to other transactions(example add log needs create routine).  If the dependancy is wrong then it will inform the user.

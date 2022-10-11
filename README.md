# Log Consumable

- A log is record of an activity that happened.
- A log follows structure and protocol(it's a blueprint, which is adopted by the log structure) which contains unique id, time, date, log text and media path of the log while creating a log.
- A log is immutable(cannot make changes after creating).
- There is a log encoder and decoder which follows the protocol.
- If a log is created then the log encoder encodes and provides to storage service.
- When a logs are fetched from the storage service, using log decoder it is decoded to the log structure.  The protocol checks the structure while decoding the log.  if it doesn't follows the protocol then it is destroyed.
- The storage service is used to read and write the logs to the file.
# Device Token

- Every time if a user creates logs or delete logs or any changes made to logs, then it is updated to the cloud as document logs, tagged with device token and the changes reflets who accessed the data.
- If a user reinstalls the app, their logs will be updated to the device, with the help of device token(if the device data is already available as document logs).
- If the user have to share their logs to other user, then they have to share their device token. If they provide the device token, first the system checks whether it's valid then it makes the connection to the cloud and fetches the logs and updates to the device.
- Only 10 shared device token can be accessed with a device.
- If the user removes the shared device tokens then logs relevant to it also removed from the device.
- If any network failure occurs, after successful network connection the latest logs are updated to the cloud.
- The audio/video/images of the log are not shared to others.
- The devices which access the data of others can only read the logs(can't make changes to it).

# Conversation Threads

- Transactional manager, handles the handshake between siri and the application.
- The transactional manager is a singleton, so it has the access to all functions in the application.
- The transactional manager get intent and their parameters as input from Siri/shortucts and ask the application to perform the actions according to the intent requested.
- Transactional manager checks if the intent is dependant to other intent(example add log needs create routine) before performing an action.  If the dependancy is wrong then it will inform the user else it executes the function.
- If the user wants to switch from one intent to another intent(create routine to guide routine) the manager confirms from the user and switches the intent.
Note : the failure occured by the Siri/shortcuts are handled from the framework.

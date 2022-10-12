# Log Consumable

- A log is instant record of an activity.
- A log follows structure(UUID,log,time,date) while creating a log.
- A log is immutable(cannot make changes after creating).
- There is a log encoder and decoder which follows the structure.
- If a log is created then the log encoder encodes and provides to system.
- When a logs are fetched from the system, using log decoder it is decoded to the log structure.  The structure checks the log while decoding.  if it doesn't follows the structure then it is destroyed.

# Device Token

- If a user wants to share their logs to other users, then the logs will be shared with the device token.
- Before the user access the logs the device token is verified, If the token is valid then the logs are provided else it informs the system that the device token is invalid.
- These device tokens are immutable(if a user reinstall the application it's not changed).  The device tokens are unique from other device tokens.
- The device tokens are encoded, inserted in a deep link and it's shared.
- If the same users 

# Conversation Threads

- There is a service called external communication and execution service(shortly called as ECE), which handles the the handshake between our application and other service like siri, shortcuts spotlight search etc.
- The ECE is a singleton, so it has access all over the application environment.
- The service like Siri / shortcuts communicates with the ECE.
- The ECE gets intent ID and it's parameter from the service like siri / shortcut.
- The ECE checks the intent ID in intent dictionary.
- If the intent ID is available, then it checks the intent provides parameter, whether the intent is dependant to another intent.  Next it executes the fuction.
- else, the ECE informs the issue to the external services.
- The intent dictionary has information about intent ID with what functionality should be executed, whether the intent has parameter or not and whether the intent is dependent to other intent.
- The ECE has a intent state variable which tracks the intent.  The intent state variable is used to check the intent state while switching from one state to another.

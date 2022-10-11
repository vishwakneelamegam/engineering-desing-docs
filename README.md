# Log Consumable

- A log is record of an activity that happened.
- A log follows structure and protocol(it's a blueprint, which is adopted by the log structure) which contains unique id, time, date, log text and media path of the log while creating a log.
- A log is immutable(cannot make changes after creating).
- There is a log encoder and decoder which follows the protocol.
- If a log is created then the log encoder encodes and provides to storage service.
- When a logs are fetched from the storage service, using log decoder it is decoded to the log structure.  The protocol checks the structure while decoding the log.  if it doesn't follows the protocol then it is destroyed.
- The storage service is used to read, write and delete the logs to the file.
- The log can be deleted by providing the unique id of the log to the storage service.

# Device Token

- If a user wants to share their logs to others then it can be shared using their device token.

# Conversation Threads

- Transactional manager, handles the handshake between siri and the application.
- The transactional manager is a singleton, so it has the access to all functions in the application.
- The transactional manager get intent and their parameters as input from Siri/shortucts and ask the application to perform the actions according to the intent requested.
- Transactional manager checks if the intent is dependant to other intent(example add log needs create routine) before performing an action.  If the dependancy is wrong then it will inform the user else it executes the function.
- If the user wants to switch from one intent to another intent(create routine to guide routine) the manager confirms from the user and switches the intent.
Note : the failure occured by the Siri/shortcuts are handled from the framework.

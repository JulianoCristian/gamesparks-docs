# Spark

The Spark object that is available to all scripts is the entry point into the GameSparks API.

It can be used for getting access to objects and functions within the GameSparks platform.

This interface is available in all scripts using the notation "Spark."

e.g.

To return a JSON representation of the Object being acted upon

<pre rel="highlighter" code-brush="js" contenteditable="false">var data = Spark.getData();</pre>


## getPlayer
_signature_ getPlayer()</p>
_returns_ [SparkPlayer](../Spark/SparkPlayer.md)</p>
<b>validity</b> All except Global Message Scripts
Returns a SparkPlayer object that represents the player who either sent, or is going to receive the object that is invoking this script.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var player = Spark.getPlayer();</pre>

## loadPlayer
_signature_ loadPlayer(string playerId)</p>
_returns_ [SparkPlayer](../Spark/SparkPlayer.md)</p>
<b>validity</b> All Scripts
Returns a SparkPlayer object that represents the player with the supplied ID.
<b>params</b>
playerId - the unique player identifier.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var player = Spark.loadPlayer(myplayerid);</pre>

## getChallenge
_signature_ getChallenge(string challengeInstanceId)</p>
_returns_ [SparkChallenge](../Spark/SparkChallenge.md)</p>
<b>validity</b> All Scripts
Allows a script to load a SparkChallenge object by it's ID.
This is mainly used on LogChallengeEventRequests where the ID of the SparkChallenge can be retrieved using Spark.data.challengeId.
<b>params</b>
challengeInstanceId - the unique challenge identifier.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var myChallenge = Spark.getChallenge(Spark.data.challengeId);</pre>

## sendMessage
_signature_ sendMessage(JSON data, [SparkPlayer](../Spark/SparkPlayer.md)[] players)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players.
The 'data' attribute of the SparkMessage will match the data parameter supplied.
<b>params</b>
data - the JSON Data to send.
players - the SparkPlayer array to send the message to.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessage({"alert" : "You've just won a car!"}, myplayers);</pre>

## sendMessageExt
_signature_ sendMessageExt(JSON data, string extCode, [SparkPlayer](../Spark/SparkPlayer.md)[] players)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players.
The 'data' attribute of the SparkMessage will match the data parameter supplied.
The extCode parameter will be used to look up the configuration for the message from ScriptMessage Extensions
<b>params</b>
data - the JSON Data to send.
extCode - The short code of the ScriptMessage extension, if not found, the default ScriptMessage will be used.
players - the SparkPlayer array to send the message to. If empty or null no message will be sent.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessageExt({"alert" : "You've just won a car!"},"CODE1" ,myplayers);</pre>

## sendMessageWithoutPush
_signature_ sendMessageWithoutPush(JSON data, [SparkPlayer](../Spark/SparkPlayer.md)[] players)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players. Push notifications will be supressed for this message
The 'data' attribute of the SparkMessage will match the data parameter supplied.
<b>params</b>
data - the JSON Data to send.
players - the SparkPlayer array to send the message to.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessage({"alert" : "You've just won a car!"}, myplayers);</pre>

## sendMessageById
_signature_ sendMessageById(JSON data, string[] playerIds)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players.
The 'data' attribute of the SparkMessage will match the data parameter supplied.
<b>params</b>
data - the JSON Data to send.
playerIds - An array of player id strings to send the message to.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessage({"alert" : "You've just won a car!"}, myplayerids);</pre>

## sendMessageByIdExt
_signature_ sendMessageByIdExt(JSON data, string extCode, string[] playerIds)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players.
The 'data' attribute of the SparkMessage will match the data parameter supplied.
The extCode parameter will be used to look up the configuration for the message from ScriptMessage Extensions
<b>params</b>
data - the JSON Data to send.
extCode - The short code of the ScriptMessage extension, if not found, the default ScriptMessage will be used.
playerIds - An array of player id strings to send the message to.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessage({"alert" : "You've just won a car!"}, myplayerids);</pre>

## sendMessageByIdWithoutPush
_signature_ sendMessageByIdWithoutPush(JSON data, string[] playerIds)</p>
_returns_ void</p>
<b>DEPRECATED use Spark.message(extCode)</b>
<b>validity</b> All Scripts
Sends a ScriptMessage to one or more spark Players.
The 'data' attribute of the SparkMessage will match the data parameter supplied. Push notifications will be supressed for this message
<b>params</b>
data - the JSON Data to send.
playerIds - An array of player id strings to send the message to.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendMessage({"alert" : "You've just won a car!"}, myplayerids);</pre>

## message
_signature_ message(string extCode)</p>
_returns_ [SparkMessage](../Utils/SparkMessage.md)</p>
<b>validity</b> All Scripts
Creates a SparkMessage object using the default configuration from the portal.
Providing an ext code allows different configurations to be used as th template.
<b>params</b>
extCode - (Optional) The extCode of a scriptMessageExtension, if null or not found the standard ScriptMessage configuration will be used.
<b>returns</b>
a SparkMessageobject
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.message("myExtCode"));</pre>

## save
_signature_ save(string collectionName, JSON document)</p>
_returns_ boolean</p>
<b>validity</b> All Scripts
Saves a document to the named collection.
<b>params</b>
collectionName - the collection name to save the document to.
document - the document to save. If the document contains and _id field, and the collection already contains a document with the same _id it will be updated.
<b>returns</b>
true if the save was successful, false if there was an error
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.save("myCollection", {"key":"value"});</pre>

## remove
_signature_ remove(string collectionName, JSON query)</p>
_returns_ boolean</p>
<b>validity</b> All Scripts
Removes a document or documents from the named collection based on the query.
<b>params</b>
collectionName - the collection name to remove the document from.
query - the query that determines what documents to remove
<b>returns</b>
true if the save was successful, false if there was an error
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.remove("myCollection", {"key":"value"});</pre>

## find
_signature_ find(string collectionName, JSON query)</p>
_returns_ JSON</p>
<b>validity</b> All Scripts
Performs a query on the named collection using find (without a projection).
http://docs.mongodb.org/manual/reference/method/db.collection.find
<b>params</b>
collectionName - the collection to query
query - the mongo query. For details see http://docs.mongodb.org/manual/core/read-operations/
<b>returns</b>
The result of the query, can be a simple document or a list
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.find("myCollection", {"key":"value"});</pre>


_signature_ find(string collectionName, JSON query, JSON projection)</p>
_returns_ JSON</p>
<b>validity</b> All Scripts
Performs a query on the named collection using find (with a projection)
http://docs.mongodb.org/manual/reference/method/db.collection.find
<b>params</b>
collectionName - the collection to query
query - the mongo query. For details see http://docs.mongodb.org/manual/core/read-operations/
projection - the projection,
<b>returns</b>
The result of the query, can be a simple document or a list
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.find("myCollection", {"key":"value"}, {"projectionKey":"projectionValue"});</pre>

## lock
_signature_ lock([SparkChallenge](../Spark/SparkChallenge.md) challenge)</p>
_returns_ void</p>
<b>validity</b> All Scripts
Locks a challenge for writing. Whilst the script 'owns' this lock no other script can modify the challenge
Useful for situations where there may be concurrent access required to a SparkChallengeObject.
Other scripts can continue to read the Challenge
If a Script gains a lock to the object, it will be released once the release method is called, or if the release method is not called, when the script terminates.
<b>params</b>
challenge - the challenge to lock
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.lock(mychallenge);</pre>

## unlock
_signature_ unlock([SparkChallenge](../Spark/SparkChallenge.md) challenge)</p>
_returns_ void</p>
<b>validity</b> All Scripts
Unlocks the challenge.
This makes it available for other scripts to acquire a lock on it.
<b>params</b>
challenge - the challenge to unlock
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.unlock(mychallenge);</pre>

## hasScriptErrors
_signature_ hasScriptErrors()</p>
_returns_ boolean</p>
<b>validity</b> All Scripts
Allows the script to detect if there have been any script errors set during the request or response.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var hasErrors = Spark.hasScriptErrors();</pre>

## setScriptError
_signature_ setScriptError(string key, JSON value)</p>
_returns_ void</p>
<b>validity</b> All Scripts
Allows an error to be added to either the request or a response being acted upon.
In the case of requests this will cause the request to be rejected. This is useful if you have some custom logic that needs to determine whether GameSparks should process the request.
The 'error' object of the Response or Message objects will contain an entry that matches the supplied parameters.
<b>params</b>
key - the key to the data
value - the data, can be either complex JSON or simple types
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.setScriptError("myerrorkey", {"test":12345});</pre>

## getScriptError
_signature_ getScriptError(string key)</p>
_returns_ JSON</p>
Gets the value of the script error for the given key.  In the case of response scripts this may have been set in the request.
<b>params</b>
name - The name in the name value pair
<b>returns</b>
a JSON object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var error = Spark.getScriptError("name");</pre>

## removeScriptError
_signature_ removeScriptError(string key)</p>
_returns_ void</p>
Removes a value from a name value pair structure containing any script errors that have previously been set.
<b>params</b>
name - The name in the name value pair
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.removeScriptError("name");</pre>

## removeAllScriptErrors
_signature_ removeAllScriptErrors()</p>
_returns_ void</p>
Removes all script errors that have been set
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.removeAllScriptErrors();</pre>

## getLog
_signature_ getLog()</p>
_returns_ [SparkLog](../Utils/SparkLog.md)</p>
<b>validity</b> All Scripts
Provides access to a SparkLog interface
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var logger = Spark.getLog();</pre>

## getPlayerIds
_signature_ getPlayerIds()</p>
_returns_ string[]</p>
<b>validity</b>Global Message Scripts
Messages are targeted to multiple players.
This method gives access to the ID's of all the target players.
This can be accessed in both Global Message Scripts and User Message Scripts
The ID's can in turn be used with getPlayer to access the player details
<b>returns</b>
 An array of Id's
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var playerIds = Spark.getPlayerIds();</pre>

## logEvent
_signature_ logEvent(string eventKey, JSON values)</p>
_returns_ void</p>
<b>validity</b> All Scripts
Allows a script to post a LogEventRequest on behalf of the current player.
Can be useful to post a score to a global leaderboard when a score has been posted to a challenge.
<b>params</b>
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.logEvent("HS", {"HS":234});</pre>

## getHttp
_signature_ getHttp(string url)</p>
_returns_ [SparkHttp](../Comms/SparkHttp.md)</p>
<b>validity</b> All Scripts
<b>params</b>
Provides access to a SparkHttp interface
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var httpSender = Spark.getHttp();</pre>

## dismissMessage
_signature_ dismissMessage(string messageId)</p>
_returns_ boolean</p>
<b>validity</b> All Scripts
Allows a script to dismiss a given message. 
Returns true if a message was dismissed. This method does not check if the message belongs to the current user.
<b>params</b>
messageId - the id of the message to dismiss
<b>returns</b>
true if the message was dismissed
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.dismissMessage("528b3411e4b09c9ee8497949");</pre>

## runtimeCollection
_signature_ runtimeCollection(string collectionName)</p>
_returns_ [SparkMongoCollectionReadWrite](../Mongo/SparkMongoCollectionReadWrite.md)</p>
<b>validity</b> All Scripts
Gets a runtime collection by name, this collection has bot read and write access and can be interacted with using SparkMongoCollectionReadOnly and SparkMongoCollectionReadWrite methods.
<b>params</b>
collectionName - the name of the collection you wish to access
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var myRuntimeCollection = Spark.runtimeCollection("runtimetest");</pre>

## metaCollection
_signature_ metaCollection(string collectionName)</p>
_returns_ [SparkMongoCollectionReadOnly](../Mongo/SparkMongoCollectionReadOnly.md)</p>
<b>validity</b> All Scripts
Gets a metadata collection by name, this collection is read only and can be queried using the methods defined in the SparkMongoCollectionReadOnly object.
<b>params</b>
collectionName - the name of the collection you wish to access
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var myMetaCollection = Spark.metaCollection("metatest");</pre>

## getFiles
_signature_ getFiles()</p>
_returns_ [SparkFiles](../Utils/SparkFiles.md)</p>
<b>validity</b> All Scripts
Provides access to file operations via a SparkFiles interface
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var files = Spark.getFiles();</pre>

## uploadedXml
_signature_ uploadedXml(string uploadId)</p>
_returns_ [SparkXmlReader](../Utils/SparkXmlReader.md)</p>
<b>DEPRECATED use Spark.getFiles().uploadedXml(uploadId)</b>
<b>validity</b> All Scripts
Provides access to an uploaded file via a SparkXmlReader interface
<b>params</b>
uploadId - the id of the uploaded file
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var reader = Spark.uploadedXml("myUploadId");</pre>

## uploadedJson
_signature_ uploadedJson(string uploadId)</p>
_returns_ JSON</p>
<b>DEPRECATED use Spark.getFiles().uploadedJson(uploadId)</b>
<b>validity</b> All Scripts
Provides access to an uploaded file via a JSON object
<b>params</b>
uploadId - the id of the uploaded file
<b>returns</b>
A JSON object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var reader = Spark.uploadedJson("myUploadId");</pre>

## downloadableXml
_signature_ downloadableXml(string shortCode)</p>
_returns_ [SparkXmlReader](../Utils/SparkXmlReader.md)</p>
<b>DEPRECATED use Spark.getFiles().downloadableXml(shortCode)</b>
<b>validity</b> All Scripts
Provides access to a downloadable file via a SparkXmlReader interface
<b>params</b>
shortCode - the short code for the downloadable file
<b>returns</b>
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var reader = Spark.downloadableXml("shortCode");</pre>

## downloadableJson
_signature_ downloadableJson(string shortCode)</p>
_returns_ JSON</p>
<b>DEPRECATED use Spark.getFiles().downloadableJson(shortCode)</b>
<b>validity</b> All Scripts
Provides access to a downloadable file via a JSON object
<b>params</b>
shortCode - the short code for the downloadable file
<b>returns</b>
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var reader = Spark.downloadableJson("shortCode");</pre>

## sendGrid
_signature_ sendGrid(string username, string password)</p>
_returns_ [SendGrid](../Comms/SendGrid.md)</p>
<b>validity</b> All Scripts
Send an email via the SendGrid email delivery provider
<b>params</b>
username - your SendGrid accounet username
password - your SendGrid account password
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendGrid(username, password);</pre>

## getScheduler
_signature_ getScheduler()</p>
_returns_ [SparkScheduler](../Utils/SparkScheduler.md)</p>
<b>validity</b> All Scripts
Utility to schedule execution of a module in the future
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getScheduler();</pre>

## getCache
_signature_ getCache()</p>
_returns_ [SparkCache](../Utils/SparkCache.md)</p>
<b>validity</b> All Scripts
Utility to cache complex objects in memory
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getCache();</pre>

## sendRequest
_signature_ sendRequest(JSON request)</p>
_returns_ JSON</p>
<b>validity</b> All Scripts
Sends a Request to the platform, this mimics the process a client uses to send requests
The request is sent as the current player, if there is no current player the method will fail.
returns - The response as would be returned to the client
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendRequest({"@class": ".LogEventRequest", "eventKey": "SOT", "SC": "1000"});</pre>

## sendRequestAs
_signature_ sendRequestAs(JSON request, string playerId)</p>
_returns_ JSON</p>
<b>validity</b> All Scripts
Sends a Request to the platform, this mimics the process a client uses to send requests
The request is sent as the player identified by playerId, if there playerId is invalid the requst will fail.
returns - The response as would be returned to the client
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.sendRequestAs({"@class": ".LogEventRequest", "eventKey": "SOT", "SC": "1000"}, "1234567890");</pre>

## getRedis
_signature_ getRedis()</p>
_returns_ [SparkRedis](../Spark/SparkRedis.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkRedis object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getRedis();</pre>

## getLeaderboards
_signature_ getLeaderboards()</p>
_returns_ [SparkLeaderboards](../Spark/SparkLeaderboards.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkLeaderboards object, used to access the leaderboards for this game.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getLeaderboards();</pre>

## getConfig
_signature_ getConfig()</p>
_returns_ [SparkConfig](../Misc/SparkConfig.md)</p>
<b>validity</b> All Scripts
Returns configuration information about the currently published game.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var myGameConfig = Spark.getConfig();</pre>

## getTeams
_signature_ getTeams()</p>
_returns_ [SparkTeams](../Spark/SparkTeams.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkTeams object, used to access the teams for this game.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getTeams();</pre>

## getMultiplayer
_signature_ getMultiplayer()</p>
_returns_ [SparkMultiplayer](../Spark/SparkMultiplayer.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkMultiplayer object, used to access the platform's multiplayer capabilities.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getMultiplayer();</pre>

## getProperties
_signature_ getProperties()</p>
_returns_ [SparkProperties](../Spark/SparkProperties.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkProperties object, used to access the Properties and Property Sets configured against a game.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getProperties();</pre>

## getBulkScheduler
_signature_ getBulkScheduler()</p>
_returns_ [SparkBulkScheduler](../Spark/SparkBulkScheduler.md)</p>
<b>validity</b> All Scripts
Returns a reference to a SparkBulkScheduler object, used to perform operations on multiple players at once.
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.getBulkScheduler();</pre>

## getScriptData
_signature_ getScriptData(string name)</p>
_returns_ JSON</p>
Gets the value from a name value pair structure that allows custom data to be attached to the challenge. This data can either be complex JSON or simple values.
<b>params</b>
name - The name in the name value pair
<b>returns</b>
a JSON object
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var userName = Spark.getPlayer().getScriptData("name");</pre>

## setScriptData
_signature_ setScriptData(string name, JSON value)</p>
_returns_ void</p>
Allows arbitrary data to be added to the object being acted upon.
Sets a value into a name value pair structure that allows custom data to be attached to the challenge. This data can either be complex JSON or simple values.
The data is visible to the client
This data is sent to the player(s) in the 'scriptData' attribute of the Request, Response or Message object.
When scriptData is set to a request, it gets set against the response that will be returned to the player. This allows basic communication between request and response scripts.
<b>params</b>
name - The name in the name value pair
value - The value to set in the name value pair
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var userName = Spark.getPlayer().setScriptData("name", "value");</pre>

## removeScriptData
_signature_ removeScriptData(string name)</p>
_returns_ void</p>
Removes a value from a name value pair structure that allows custom data to be attached to the challenge. This data can either be complex JSON or simple values.
<b>params</b>
name - The name in the name value pair
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var userName = Spark.getPlayer().removeScriptData("name");</pre>

## removeAllScriptData
_signature_ removeAllScriptData()</p>
_returns_ void</p>
Removes all script data that has been set
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">Spark.removeAllScriptData();</pre>

## getRemainingMilliseconds
_signature_ getRemainingMilliseconds()</p>
_returns_ number</p>
Gets the number of milliseconds this script has left to run before a longRunningScriptError is thrown

## getData
_signature_ getData()</p>
_returns_ JSON</p>
<b>validity</b> All Scripts
A JSON version of the object being scripted. Can be either a Request, Response or Message.
The structure of the JSON is as the Client either receives or sends it. Attributes can be read, but not changed
<b>example</b>
<pre rel="highlighter" code-brush="js" contenteditable="false">var userName = Spark.getData().userName;</pre>

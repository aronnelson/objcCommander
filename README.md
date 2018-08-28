# objcCommander
NSUserActivity for Siri Shortcut in Objective C

These are the steps to create a Siri Shortcut using Objective C. Very easy and quick on iOS12

1: Enable Siri in Capabilities tab of your project.

2: Add the Intents framework in the Linked Frameworks and Libraries tab.Under target->General

3: In the project plist, add an entry: NSUserActivityTypes with string = project bundle ID.activity name. For example: com.awesomeapps.myawesomeapp.myactivity

4: Create a NSUserActivity and make it current once. Set two variable to true, setEligibleForSearch and setEligibleForPrediction. 
This will make it available to Siri.
 
5:Handle the activiy in: -(BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler
	You can query the userActivity.title to verify the activity.
	

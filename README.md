# objcCommander
NSUserActivity for Siri Shortcut in Objective C

These are the steps to create a Siri Shortcut using Objective C. Very easy and quick on iOS12

1: Enable Siri in Capabilities tab of your project.

2: Add the Intents framework in the Linked Frameworks and Libraries tab. Under target->General

3: In the project plist, add an entry: NSUserActivityTypes with string = project bundle ID.activity name. For example: com.awesomeapps.myawesomeapp.myactivity

4: Create a NSUserActivity. Set two variables to true, setEligibleForSearch and setEligibleForPrediction. Make it current once.

This will make it available to Siri.

For example: (k_activityID is your bundle ID+activity name For example: com.awesomeapps.myawesomeapp.myactivity)

 NSUserActivity *theActivity = [[NSUserActivity alloc]initWithActivityType:k_activityID];
    theActivity.title = @"Run Me";
    [theActivity setEligibleForSearch:true];
    [theActivity setEligibleForPrediction:true];
    theActivity.persistentIdentifier = k_activityID;
    theActivity.suggestedInvocationPhrase = @"Run Me";
    self.view.userActivity = theActivity;
    [theActivity becomeCurrent];
    
 
5:Handle the activiy in: -(BOOL)application:(UIApplication *)application continueUserActivity:(NSUserActivity *)userActivity restorationHandler:(void (^)(NSArray<id<UIUserActivityRestoring>> * _Nullable))restorationHandler
	You can query the userActivity.title to verify the activity.
	
if ([theActivity.title isEqualToString:k_activityID]){
        // do the activity
        
    }
    

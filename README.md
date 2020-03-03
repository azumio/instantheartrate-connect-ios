# Azumio Connect SDK
Enables heart rate measurements in your app.
  
 
## How it works
1. User presses a button in your app
2. Instant Heart Rate is launched, user measures his heart rate
3. Result is returned to your app.

## How to implement
 

1. Copy AzumioConnect folder with files AZConnect.m/.h to your project

2. Add new URL schema to your info file. We recommend using your Bundle identifier which should be in the reverse domain notation ( com.azumio.iphone.AzumioConnectExample in our example app )
Hint: Step 5 at http://mobile.tutsplus.com/tutorials/iphone/ios-sdk-working-with-url-schemes/
2. Add `si.modula.instantheartrate.free` and `si.modula.instantheartrate` to `LSApplicationQueriesSchemes` in your Info.plist file 

3. Handle openUrl and redirect it to AZConnect
 -(BOOL)application:(UIApplication *)application openURL:(NSURL *)url sourceApplication:(NSString *)sourceApplication annotation:(id)annotation{
    
    [[AZConnect instance] openURL:url];

    return YES;

}


4. Register a callback to receive the heart rate
 [[AZConnect instance] setHeartRateCallback:^(double heartRate) {
        heartrateLabel.text = [NSString stringWithFormat:@"%d bpm", (int)heartRate];

    } andSchema:@"com.azumio.iphone.AzumioConnectExample"];


5. Trigger the measurement
[[AZConnect instance] measureHeartRate];
 

 
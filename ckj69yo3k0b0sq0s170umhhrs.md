## Flutter: Most effective way to check if your device is connected to the internet

When you build an application that requires data from an online server, it is important to check the internet connection status of the user. 

This will ensure that the user doesn’t wait forever for the request to your online server to fail/timeout due to internet connection before they get an error message. 

In this article, I will unveil the most effective way to implement this in a Flutter application.


# Implementation

[Data_connection_checker](https://pub.dev/packages/data_connection_checker) is a flutter package that has an effective implementation for device internet connection check. The package opens a socket connection to some list of DNS (safe and secured addresses like Google DNS) and if any of the DNS returns data it’s then marked that the device is connected to the internet. 

#### Step 1: 
Add the package to your pubspec.yaml file

    data_connection_checker: ^0.3.4

>    Note: this package version might have been updated when you’re
> reading this article, please always install the latest version.

#### Step 2: 

Initialize the DataConnectionChecker (this is a singleton, so you will always get the same instance at any point in your application) and called the 
```
.hasConnection
``` 
 method to check for the connection status before you make any request to an online server.

The 
```
.hasConnection
``` 
will return true if the device is connected or false if it’s not. That’s all, it’s simple and more effective.

See the example in the code snippet below;


    bool result = await DataConnectionChecker().hasConnection;
    if(result == true) {
      print('YAY! Request for data from your online server');
    } else {
      print('No internet, please check your internet connection ');
      print(DataConnectionChecker().lastTryResults);
    }



> 
NOTICE: Please always try to check for the device connection status before you make a request to the online server.

YAY!!!!! I hope this article was informative, please encourage me by leaving a comment in the comment section and also like and share where it’s necessary. Thank you for your time.
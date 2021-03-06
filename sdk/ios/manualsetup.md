---
title: SDK Setup Options
---

# SDK Setup Options

The AWS SDK contains [high level client interfaces](./start) for quickly adding common features and functionality to your app. You can also manually add the generated AWS service interfaces for direct interaction if you have custom or advanced requirements.

## CocoaPods setup

The AWS Mobile SDK for iOS is available through [CocoaPods](https://cocoapods.org). Install CocoaPods by running the following commands from the folder containing your projects `*.xcodeproj` file:

```bash
gem install cocoapods
pod setup
pod init
```

In your project directory (the directory where your `*.xcodeproj` file is), open the empty text file named `Podfile`. Replace `myAppName` with your app name. You can also remove pods for services that you don't use. For example, if you don't use `AWSAutoScaling`, remove or do not include the `AWSAutoScaling` pod.

```ruby
source 'https://github.com/CocoaPods/Specs.git'

platform :ios, '9.0'
use_frameworks!

target :'YOUR-APP-NAME' do
    pod 'AWSAuth'
    pod 'AWSAuthCore'
    pod 'AWSAuthUI'
    pod 'AWSAutoScaling'
    pod 'AWSCloudWatch'
    pod 'AWSCognito'
    pod 'AWSCognitoAuth'
    pod 'AWSCognitoIdentityProvider'
    pod 'AWSCognitoIdentityProviderASF'
    pod 'AWSCore'
    pod 'AWSDynamoDB'
    pod 'AWSEC2'
    pod 'AWSElasticLoadBalancing'
    pod 'AWSFacebookSignIn'
    pod 'AWSGoogleSignIn'
    pod 'AWSIoT'
    pod 'AWSKMS'
    pod 'AWSKinesis'
    pod 'AWSLambda'
    pod 'AWSLex'
    pod 'AWSLogs'
    pod 'AWSMachineLearning'
    pod 'AWSMobileClient'
    pod 'AWSPinpoint'
    pod 'AWSPolly'
    pod 'AWSRekognition'
    pod 'AWSS3'
    pod 'AWSSES'
    pod 'AWSSNS'
    pod 'AWSSQS'
    pod 'AWSSimpleDB'
    pod 'AWSUserPoolsSignIn'
end
```

Once complete, run `pod install` and open the `*.xcworkspace` with Xcode and **build** your project to start using the SDK. Once you have created a workspace, always use `*.xcworkspace` to open the project instead of `*.xcodeproj`.

Whenever a new version of the SDK is released you can update by running `pod update` and rebuilding your project to use the new features.

## Carthage setup

The AWS Mobile SDK for iOS is available through [Carthage](https://github.com/Carthage/Carthage). Install the latest version of [Carthage](https://github.com/Carthage/Carthage#installing-carthage).

Add the following to your `Cartfile`:

```bash
github "aws-amplify/aws-sdk-ios"
```

Once complete, run `carthage update` and open the `*.xcworkspace` or `*.xcodeproj` file with Xcode and chose your `Target`. In the `General` tab, find `Embedded Binaries`, then choose the `+` button.

Choose the `Add Other` button, navigate to the `AWS<#ServiceName#>.framework` files under `Carthage > Build > iOS` and select `AWSCore.framework` and the other service frameworks you require. Do not select the `Destination: Copy items` if needed check box when prompted.

* AWSAuth
* AWSAuthCore
* AWSAuthUI
* AWSAutoScaling
* AWSCloudWatch
* AWSCognito
* AWSCognitoAuth
* AWSCognitoIdentityProvider
* AWSCognitoIdentityProviderASF
* AWSCore
* AWSDynamoDB
* AWSEC2
* AWSElasticLoadBalancing
* AWSFacebookSignIn
* AWSGoogleSignIn
* AWSIoT
* AWSKMS
* AWSKinesis
* AWSLambda
* AWSLex
* AWSLogs
* AWSMachineLearning
* AWSMobileClient
* AWSPinpoint
* AWSPolly
* AWSRekognition
* AWSS3
* AWSSES
* AWSSNS
* AWSSQS
* AWSSimpleDB
* AWSUserPoolsSignIn

Under the `Build Phases` tab in your `Target`, choose the `+` button on the top left and then select `New Run Script Phase`.

Setup the build phase as follows. Make sure this phase is below the Embed Frameworks phase.

```bash
Shell /bin/sh

bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/AWSCore.framework/strip-frameworks.sh"

Show environment variables in build log: Checked
Run script only when installing: Not checked

Input Files: Empty
Output Files: Empty
```

Now **build** your project to start using the SDK. Whenever a new version of the SDK is released you can update by running `carthage update` and rebuilding your project to use the new features.

> Note: Currently, the AWS SDK for iOS builds the Carthage binaries using Xcode 10.1.0. To consume the pre-built binaries your Xcode version needs to be the same, else you have to build the frameworks on your machine by passing `--no-use-binaries` flag to `carthage update` command.

## Frameworks setup

Download the [latest SDK](https://sdk-for-ios.amazonwebservices.com/latest/aws-ios-sdk.zip). Older SDK versions can be downloaded from `https://sdk-for-ios.amazonwebservices.com/aws-ios-sdk-#.#.#.zip`, where `#.#.#` represents the version number. So for version 2.10.2, the download link is [https://sdk-for-ios.amazonwebservices.com/aws-ios-sdk-2.10.2.zip](https://sdk-for-ios.amazonwebservices.com/aws-ios-sdk-2.10.2.zip).

With your project open in Xcode, select your `Target`. Under `General` tab, find `Embedded Binaries` and then click the `+` button.

Click the `Add Other...` button, navigate to the `AWS<#ServiceName#>.framework` files and select them. Check the `Destination: Copy items if needed` checkbox when prompted.

* `AWSAuth.framework`
* `AWSAuthCore.framework`
* `AWSAuthUI.framework`
* `AWSAutoScaling.framework`
* `AWSCloudWatch.framework`
* `AWSCognito.framework`
* `AWSCognitoAuth.framework`
* `AWSCognitoIdentityProvider.framework`
* `AWSCognitoIdentityProviderASF.framework`
* `AWSCore.framework`
* `AWSDynamoDB.framework`
* `AWSEC2.framework`
* `AWSElasticLoadBalancing.framework`
* `AWSFacebookSignIn.framework`
* `AWSGoogleSignIn.framework`
* `AWSIoT.framework`
* `AWSKMS.framework`
* `AWSKinesis.framework`
* `AWSLambda.framework`
* `AWSLex.framework`
* `AWSLogs.framework`
* `AWSMachineLearning.framework`
* `AWSMobileClient.framework`
* `AWSPinpoint.framework`
* `AWSPolly.framework`
* `AWSRekognition.framework`
* `AWSS3.framework`
* `AWSSES.framework`
* `AWSSNS.framework`
* `AWSSQS.framework`
* `AWSSimpleDB.framework`
* `AWSUserPoolsSignIn.framework`

Under the `Build Phases` tab in your `Target`, click the `+` button on the top left and then select `New Run Script Phase`. Then setup the build phase as follows. Make sure this phase is below the `Embed Frameworks` phase.

    Shell /bin/sh
        
    bash "${BUILT_PRODUCTS_DIR}/${FRAMEWORKS_FOLDER_PATH}/AWSCore.framework/strip-frameworks.sh"
        
    Show environment variables in build log: Checked
    Run script only when installing: Not checked
        
    Input Files: Empty
    Output Files: Empty

Now **build** your project to start using the SDK. Whenever a new version of the SDK is released you can update by selecting the previously imported AWS frameworks in `Project Navigator` in Xcode and pressing 'delete' on your keyboard. Then select `Move to Trash` and follow the installation process above to include the new version of the SDK.

## AWS SDK Version vs. Semantic Versioning

The AWS SDK for iOS does not follow semantic versioning. Instead, it increments the patch-level version for both backward-compatible bug fixes *and* non-breaking changes, and increments the minor version for breaking changes. Major version changes are rare, and usually indicate a dramatically different programming model.

For comparison, Semantic versioning increments the patch level for backward-compatible bug fixes, the minor version for backward-compatible new features, and the major version for breaking changes.

## Direct AWS Service access

You can call AWS service interface objects directly via the generated SDK clients. You can use the client credentials provided by the [AWSMobileClient](./authentication) when using the `.default()` method on a service object (e.g. `AWSSQS.default()`). This will leverage short term AWS credentials from Cognito Identity. Alternatively, you can call the constructors manually.

**Note:** If you are relying on the AWSMobileClient as the credentials provider, then initialize the AWSMobileClient before constructing any other service client. The AWSMobileClient will attach itself as the credentials provider for all default clients. However, if you attach a default credentials provider before initializing the AWSMobileClient, then you cannot rely on the AWSMobileClient to vend credentials used to authenticate the service client's API calls.

To work with service interface objects, your Amazon Cognito users' [IAM role](https://docs.aws.amazon.com/cognito/latest/developerguide/iam-roles.html) must have the appropriate permissions to call the requested services.
{: .callout .callout--warning}

For example, if you were using [Amazon Simple Queue Service (SQS)](https://aws.amazon.com/sqs/) in Swift you would first add `AWSSQS` to your `Podfile` and install the dependencies with `pod install` (alternatively follow the instructions for [Carthage](#carthage-setup) or [Frameworks](#frameworks-setup)). Next, update your `awsconfiguration.json` like so:

```json
    "SQS" : {
        "Default": {
            "Region": "XX-XXXX-X"
        }
    }
```

**Note**: The key is `SQS` and not `AWSSQS` as the `awsconfiguration.json` file does not prefix keys with `AWS`.

Next, import `AWSSQS` in your Xcode project and create the client:

```swift
import AWSSQS

func addItemSQS() {
        let sqs = AWSSQS.default()
        let req = AWSSQSSendMessageRequest()
        req?.queueUrl = "https://sqs.XX-XXXX-X.amazonaws.com/XXXXXXXXXXXX/MyQueue"
        req?.messageBody = "hello world"
        sqs.sendMessage(req!) { (result, err) in
            if let result = result {
                print("SQS result: \(result)")
            }
            if let err = err {
                print("SQS error: \(err)")
            }
        }
    }
```

You could then call `self.addItemSQS()` to invoke this action from your app. To perform these tasks in an asynchronous manner in an application, please see [Working with Asynchronous Tasks](./how-to-ios-asynchrounous-tasks).

## Logging

As of version 2.5.4 of this SDK, logging utilizes [CocoaLumberjack SDK](https://github.com/CocoaLumberjack/CocoaLumberjack), a flexible, fast, open source logging framework. It supports many capabilities including the ability to set logging level per output target, for instance, concise messages logged to the console and verbose messages to a log file.

CocoaLumberjack logging levels are additive such that when the level is set to verbose, all messages from the levels below verbose are logged. It is also possible to set custom logging to meet your needs. For more information, see [CocoaLumberjack Logging Levels](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/CustomLogLevels.md).

You can change the logging level to suit the phase of your development cycle by importing AWSCore and calling:

```swift
AWSDDLog.sharedInstance.logLevel = .verbose
```

The following logging level options are available:

- `.off`
- `.error`
- `.warning`
- `.info`
- `.debug`
- `.verbose`

We recommend setting the log level to  `.off` before publishing to the App Store.

CocoaLumberjack can direct logs to file or used as a framework that integrates with the Xcode console. For example:

```swift
//File Logger example
let fileLogger: AWSDDFileLogger = AWSDDFileLogger() // File Logger
fileLogger.rollingFrequency = TimeInterval(60*60*24)  // 24 hours
fileLogger.logFileManager.maximumNumberOfLogFiles = 7
AWSDDLog.add(fileLogger)


//Console example
AWSDDLog.add(AWSDDTTYLogger.sharedInstance) // TTY = Xcode console
```

## Configure using an in-memory object

As an alternative to the `awsconfiguration.json` file, since version `2.11.0` a configuration object can also be used for configuring the client. This approach can be useful for resolving configuration in runtime instead of the pre-defined JSON file:

```swift
let configuration: [String: Any] = [
    "IdentityManager": [
        "Default": [:]
    ],
    "Auth": [
        "Default": [
            "OAuth": [
                "AppClientId": "APP_CLIENT_ID",
                "AppClientSecret": "APP_CLIENT_SECRET",
                "Scopes": ["email"]
            ]
        ]
    ]
]

let mobileClient = AWSMobileClient(configuration: configuration)
mobileClient.initialize { (userState, error) in
    // initialization logic
}
```

Please note that creating multiple instances of `AWSMobileClient` <b>is not supported</b>. The configuration cannot be reset and/or re-initialized. Therefore, even though you can instantiate `AWSMobileClient` multiple times, all instances will have the same configuration reference. If you configure `AWSMobileClient` as shown above, make sure to use the initialized in memory object of mobileClient instead of the singleton object of `AWSMobileClient`.
{: .callout .callout--warning}

## DocSet for Xcode

Open the macOS terminal and go to the directory containing the expanded archive. For example:

```bash
$ cd ~/Downloads/aws-ios-sdk-2.9.0
```

**Note**: Replace 2.9.0 in the preceding example with the version number of the AWS Mobile SDK for iOS that you downloaded.

Create a directory called `~/Library/Developer/Shared/Documentation/DocSets`:

```bash
$ mkdir -p ~/Library/Developer/Shared/Documentation/DocSets
```

Copy (or move) `documentation/com.amazon.aws.ios.docset` from the SDK installation files to the directory you created in the previous step:

```bash
$ mv documentation/com.amazon.aws.ios.docset ~/Library/Developer/Shared/Documentation/DocSets/
```

If Xcode was running during this procedure, restart Xcode. To browse the documentation, go to **Help**, click **Documentation and API Reference**, and select **AWS Mobile SDK for iOS v2.7 Documentation** (where '2.7' is the appropriate version number).

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Follow these instructions if you need to build native code in your project. For example, if you are integrating React Native into an existing application, or if you "ejected" from</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Create React Native App</span>](http://facebook.github.io/react-native/docs/getting-started.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">, you'll need this section.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">The instructions are a bit different depending on your development operating system, and whether you want to start developing for iOS or Android. If you want to develop for both iOS and Android, that's fine - you just have to pick one to start with, since the setup is a bit different.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Development OS:</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">macOS</span>](javascript:void(0);) [<span style="color: white;background-color: rgb(5,165,209);font-size: 18px;">Windows</span>](javascript:void(0);) [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Linux</span>](javascript:void(0);) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Target OS:</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">iOS</span>](javascript:void(0);) [<span style="color: white;background-color: rgb(5,165,209);font-size: 18px;">Android</span>](javascript:void(0);)

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Installing dependencies</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">You will need Node, the React Native command line interface, Python2, a JDK, and Android Studio.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">While you can use any editor of your choice to develop your app, you will need to install Android Studio in order to set up the necessary tooling to build your React Native app for Android.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Node, Python2, JDK</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">We recommend installing Node and Python2 via</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Chocolatey</span>](https://chocolatey.org/)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">, a popular package manager for Windows.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">React Native also requires a recent version of the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Java SE Development Kit (JDK)</span>](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">, as well as Python 2\. Both can be installed using Chocolatey.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Open an Administrator Command Prompt (right click Command Prompt and select "Run as Administrator"), then run the following command:</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 13px;">choco install</span> <span style="color: rgb(166,127,89);background-color: rgb(245,252,255);font-size: 13px;">-</span><span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 13px;">y nodejs</span><span style="color: rgb(153,153,153);background-color: rgb(245,252,255);font-size: 13px;">.</span><span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 13px;">install python2 jdk8</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you have already installed Node on your system, make sure it is version 4 or newer. If you already have a JDK on your system, make sure it is version 8 or newer.</span>

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">You can find additional installation options on</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 14px;">Node's Downloads page</span>](https://nodejs.org/en/download/)<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">The React Native CLI</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Node comes with npm, which lets you install the React Native command line interface.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Run the following command in a Command Prompt or shell:</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">npm install</span> <span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">g react</span><span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">native</span><span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">cli</span>

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">If you get an error like</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">`Cannot find module 'npmlog'`, try installing npm directly:</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">`curl -0 -L https://npmjs.org/install.sh | sudo sh`.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Android development environment</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Setting up your development environment can be somewhat tedious if you're new to Android development. If you're already familiar with Android development, there are a few things you may need to configure. In either case, please make sure to carefully follow the next few steps.</span>

#### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 17px;font-family: inherit;">1\. Install Android Studio</span> 

[<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Download and install Android Studio</span>](https://developer.android.com/studio/index.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">. Choose a "Custom" setup when prompted to select an installation type. Make sure the boxes next to all of the following are checked:</span>

*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android SDK`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android SDK Platform`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Performance (Intel ® HAXM)`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android Virtual Device`</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Then, click "Next" to install all of these components.</span>

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">If the checkboxes are grayed out, you will have a chance to install these components later on.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Once setup has finalized and you're presented with the Welcome screen, proceed to the next step.</span>

#### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 17px;font-family: inherit;">2\. Install the Android SDK</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Android Studio installs the latest Android SDK by default. Building a React Native app with native code, however, requires the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android 6.0 (Marshmallow)`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">SDK in particular. Additional Android SDKs can be installed through the SDK Manager in Android Studio.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">The SDK Manager can be accessed from the "Welcome to Android Studio" screen. Click on "Configure", then select "SDK Manager".</span>

![Android Studio Welcome](http://facebook.github.io/react-native/img/AndroidStudioWelcomeWindows.png)

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">The SDK Manager can also be found within the Android Studio "Preferences" dialog, under</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">**Appearance & Behavior**</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">→</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">**System Settings**</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">→</span> <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">**Android SDK**.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Select the "SDK Platforms" tab from within the SDK Manager, then check the box next to "Show Package Details" in the bottom right corner. Look for and expand the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android 6.0 (Marshmallow)`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">entry, then make sure the following items are all checked:</span>

*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Google APIs`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Android SDK Platform 23`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Intel x86 Atom_64 System Image`</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Google APIs Intel x86 Atom_64 System Image`</span>

![Android SDK Manager](http://facebook.github.io/react-native/img/AndroidSDKManagerWindows.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Next, select the "SDK Tools" tab and check the box next to "Show Package Details" here as well. Look for and expand the "Android SDK Build-Tools" entry, then make sure that</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`23.0.1`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">is selected.</span>

![Android SDK Manager - 23.0.1 Build Tools](http://facebook.github.io/react-native/img/AndroidSDKManagerSDKToolsWindows.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Finally, click "Apply" to download and install the Android SDK and related build tools.</span>

![Android SDK Manager - Installs](http://facebook.github.io/react-native/img/AndroidSDKManagerInstallsWindows.png)

#### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 17px;font-family: inherit;">3\. Configure the ANDROID_HOME environment variable</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">The React Native tools require some environment variables to be set up in order to build apps with native code.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Open the System pane under</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**System and Security**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">in the Control Panel, then click on</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Change settings...**. Open the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Advanced**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">tab and click on</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Environment Variables...**. Click on</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**New...**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">to create a new</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`ANDROID_HOME`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">user variable that points to the path to your Android SDK:</span>

![ANDROID_HOME Environment Variable](http://facebook.github.io/react-native/img/AndroidEnvironmentVariableANDROID_HOME.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">The SDK is installed, by default, at the following location:</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 13px;">c:\Users\YOUR_USERNAME\AppData\Local\Android\Sdk</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">You can find the actual location of the SDK in the Android Studio "Preferences" dialog, under</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Appearance & Behavior**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">→</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**System Settings**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">→</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Android SDK**.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Open a new Command Prompt window to ensure the new environment variable is loaded before proceeding to the next step.</span>

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Creating a new application</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Use the React Native command line interface to generate a new React Native project called "AwesomeProject":</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">react</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">native init AwesomeProject</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">This is not necessary if you are integrating React Native into an existing application, if you "ejected" from Create React Native App, or if you're adding Android support to an existing React Native project (see</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Platform Specific Code</span>](http://facebook.github.io/react-native/docs/platform-specific-code.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">).</span>

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Preparing the Android device</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">You will need an Android device to run your React Native Android app. This can be either a physical Android device, or more commonly, you can use an Android Virtual Device which allows you to emulate an Android device on your computer.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Either way, you will need to prepare the device to run Android apps for development.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Using a physical device</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you have a physical Android device, you can use it for development in place of an AVD by plugging it in to your computer using a USB cable and following the instructions</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">here</span>](http://facebook.github.io/react-native/docs/running-on-device.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Using a virtual device</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">You can see the list of available Android Virtual Devices (AVDs) by opening the "AVD Manager" from within Android Studio. Look for an icon that looks like this:</span>

![Android Studio AVD Manager](http://facebook.github.io/react-native/img/react-native-tools-avd.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you have just installed Android Studio, you will likely need to</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">create a new AVD</span>](https://developer.android.com/studio/run/managing-avds.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">. Select "Create Virtual Device...", then pick any Phone from the list and click "Next".</span>

![Android Studio AVD Manager](http://facebook.github.io/react-native/img/CreateAVDWindows.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Select the "x86 Images" tab, then look for the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">**Marshmallow**</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">API Level 23, x86_64 ABI image with a Android 6.0 (Google APIs) target.</span>

![Install HAXM](http://facebook.github.io/react-native/img/CreateAVDx86Windows.png)

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">If you don't have HAXM installed, click on "Install HAXM" or follow</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 14px;">these instructions</span>](https://software.intel.com/en-us/android/articles/installation-instructions-for-intel-hardware-accelerated-execution-manager-windows) <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">to set it up, then go back to the AVD Manager.</span>

![AVD List](http://facebook.github.io/react-native/img/AVDManagerWindows.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Click "Next" then "Finish" to create your AVD. At this point you should be able to click on the green triangle button next to your AVD to launch it, then proceed to the next step.</span>

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Running your React Native application</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Run</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`react-native run-android`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">inside your React Native project folder:</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">cd AwesomeProject</span>  
<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">react</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">native run</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">android</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If everything is set up correctly, you should see your new app running in your Android emulator shortly.</span>

![AwesomeProject on Android](http://facebook.github.io/react-native/img/AndroidSuccessWindows.png)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`react-native run-android`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">is just one way to run your app - you can also run it directly from within Android Studio or</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Nuclide</span>](https://nuclide.io/)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">.</span>

<span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">If you can't get this to work, see the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 14px;">Troubleshooting</span>](http://facebook.github.io/react-native/docs/troubleshooting.html#content) <span style="color: rgb(72,72,72);background-color: rgba(248,245,236,0.1);font-size: 14px;">page.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Modifying your app</span> 

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Now that you have successfully run the app, let's modify it.</span>

*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Open</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`index.js`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">in your text editor of choice and edit some lines.</span>
*   <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Press the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`R`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">key twice or select</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`Reload`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">from the Developer Menu (`Ctrl + M`) to see your changes!</span>

### <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">That's it!</span> [<span style="color: rgb(72,72,72);background-color: transparent;font-size: 18px;">#</span>](http://facebook.github.io/react-native/docs/getting-started.html#that-s-it)

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Congratulations! You've successfully run and modified your first React Native app.</span>
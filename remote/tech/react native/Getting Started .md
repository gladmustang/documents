# <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 40px;">Getting Started</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">This page will help you install and build your first React Native app. If you already have React Native installed, you can skip ahead to the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Tutorial</span>](http://facebook.github.io/react-native/docs/tutorial.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">.</span>

[<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Create React Native App</span>](https://github.com/react-community/create-react-native-app) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">is the easiest way to start building a new React Native application. It allows you to start a project without installing or configuring any tools to build native code - no Xcode or Android Studio installation required (see</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Caveats</span>](http://facebook.github.io/react-native/docs/getting-started.html#caveats)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">).</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Assuming that you have</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Node</span>](https://nodejs.org/en/download/) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">installed, you can use npm to install the</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`create-react-native-app`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">command line utility:</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">npm install</span> <span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">g create</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">react</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">native</span><span style="color: rgb(166,127,89);background-color: rgba(5,165,209,0.05);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">app</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Then run the following commands to create a new React Native project called “AwesomeProject”:</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">create</span><span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">react</span><span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">native</span><span style="color: rgb(166,127,89);background-color: rgba(255,255,255,0.498);font-size: 18px;">-</span><span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">app AwesomeProject</span>

<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">cd AwesomeProject</span>  
<span style="color: rgb(72,72,72);background-color: rgba(5,165,209,0.05);font-size: 18px;">npm start</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">This will start a development server for you, and print a QR code in your terminal.</span>

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Running your React Native application</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Install the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Expo</span>](https://expo.io/) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">client app on your iOS or Android phone and connect to the same wireless network as your computer. Using the Expo app, scan the QR code from your terminal to open your project.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Modifying your app</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Now that you have successfully run the app, let’s modify it. Open</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`App.js`</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">in your text editor of choice and edit some lines. The application should reload automatically once you save your changes.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">That’s it!</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Congratulations! You’ve successfully run and modified your first React Native app.</span>

![](http://facebook.github.io/react-native/img/react-native-congratulations.png)

## <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 31px;font-family: inherit;">Now what?</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Create React Native App also has a</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">user guide</span>](https://github.com/react-community/create-react-native-app/blob/master/react-native-scripts/template/README.md) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">you can reference if you have questions specific to the tool.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you can’t get this to work, see the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Troubleshooting</span>](https://github.com/react-community/create-react-native-app/blob/master/react-native-scripts/template/README.md#troubleshooting) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">section in the README for Create React Native App.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you’re curious to learn more about React Native, continue on to the</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">Tutorial</span>](http://facebook.github.io/react-native/docs/tutorial.html)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">.</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Running your app on a simulator or virtual device</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Create React Native App makes it really easy to run your React Native app on a physical device without setting up a development environment. If you want to run your app on the iOS Simulator or an Android Virtual Device, please refer to the instructions for building projects with native code to learn how to install Xcode and set up your Android development environment.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Once you’ve set these up, you can launch your app on an Android Virtual Device by running</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`npm run android`, or on the iOS Simulator by running</span> <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">`npm run ios`(macOS only).</span>

### <span style="color: rgb(2,82,104);background-color: rgb(245,252,255);font-size: 23px;font-family: inherit;">Caveats</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Because you don’t build any native code when using Create React Native App to create a project, it’s not possible to include custom native modules beyond the React Native APIs and components that are available in the Expo client app.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you know that you’ll eventually need to include your own native code, Create React Native App is still a good way to get started. In that case you’ll just need to “</span>[<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">eject</span>](https://github.com/react-community/create-react-native-app/blob/master/react-native-scripts/template/README.md#ejecting-from-create-react-native-app)<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">” eventually to create your own native builds. If you do eject, the “Building Projects with Native Code” instructions will be required to continue working on your project.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Create React Native App configures your project to use the most recent React Native version that is supported by the Expo client app. The Expo client app usually gains support for a given React Native version about a week after the React Native version is released as stable. You can check</span> [<span style="color: rgb(5,165,209);background-color: transparent;font-size: 18px;">this document</span>](https://github.com/react-community/create-react-native-app/blob/master/VERSIONS.md) <span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">to find out what versions are supported.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">If you’re integrating React Native into an existing project, you’ll want to skip Create React Native App and go directly to setting up the native build environment. Select “Building Projects with Native Code” above for instructions on configuring a native build environment for React Native.</span>

<span style="color: rgb(72,72,72);background-color: rgb(245,252,255);font-size: 18px;">Projects with Native Code" above for instructions on configuring a native build environment for React Native.</span>
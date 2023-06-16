<!--- README.md --->
# React Native Environment Setup - macOS -> Target Android App
## Installing dependencies
You will need Node, Watchman, the React Native command line interface, a JDK, and Android Studio.
While you can use any editor of your choice to develop your app, you will need to install Android Studio 
in order to set up the necessary tooling to build your React Native app for Android.
This script provides step-by-step instructions to set up your macOS environment for React Native development.

## Node & Watchman
```shell
brew install node
brew install watchman
```
If you have already installed Node on your system, make sure it is Node 14 or newer.
Check the node version of your machine
```shell
node --version
```
Watchman is a tool by Facebook for watching changes in the filesystem. It is highly recommended you install 
it for better performance.

## Java Development Kit
```shell
brew tap homebrew/cask-versions
brew install --cask zulu11
# Get path to where cask was installed to double-click installer
brew info --cask zulu11
```
After you install the JDK, update your JAVA_HOME environment variable. If you used above steps, JDK will likely be at 
/Library/Java/JavaVirtualMachines/zulu-11.jdk/Contents/Home
The Zulu OpenJDK distribution offers JDKs for both Intel and M1 Macs. This will make sure your builds are faster on 
M1 Macs compared to using an Intel-based JDK.
If you have already installed JDK on your system, official documentation recommends JDK 11. You may encounter problems 
using higher JDK versions.

## Android development environment
Setting up your development environment can be somewhat tedious if you're new to Android development. If you're already
familiar with Android development, there are a few things you may need to configure. In either case, please make sure
to carefully follow the next few steps.
### 1. Install Android Studio
   
Download and install [Android Studio.](https://developer.android.com/studio?gclid=Cj0KCQjw7aqkBhDPARIsAKGa0oKFC15O8HbRTOyB3NgSvpJoA7sICbazlKFS-iEcx6mt1xT7_BzVnOUaAjraEALw_wcB&gclsrc=aw.ds) While on Android Studio installation wizard, make sure the boxes next to
all of the following items are checked:
   a. Android SDK
   b. Android SDK Platform
   c. Android Virtual Device
   
Then, click "Next" to install all of these components.

### 2. Install Android SDK
Android Studio installs the latest Android SDK by default. Building a React Native app with native code, however, requires the 
Android 13 (Tiramisu) SDK in particular. Additional Android SDKs can be installed through the SDK Manager in Android Studio.

To do that, open Android Studio, click on "More Actions" button and select "SDK Manager".

Select the "SDK Platforms" tab from within the SDK Manager, then check the box next to "Show Package Details" in the bottom 
right corner. Look for and expand the Android 13 (Tiramisu) entry, then make sure the following items are checked:

  a. Android SDK Platform 33
  
  b. Intel x86 Atom_64 System Image or Google APIs Intel x86 Atom System Image or (for Apple M1 Silicon) 
    Google APIs ARM 64 v8a System Image
    
Next, select the "SDK Tools" tab and check the box next to "Show Package Details" here as well. Look for and expand the "Android 
SDK Build-Tools" entry, then make sure that 33.0.0 is selected.

Finally, click "Apply" to download and install the Android SDK and related build tools.

### 3. Configure the ANDROID_HOME environment variable
The React Native tools require some environment variables to be set up in order to build apps with native code.

Add the following lines to your ~/.zprofile or ~/.zshrc (if you are using bash, then ~/.bash_profile or ~/.bashrc) config file:
```shell
export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
```
Run source ~/.zprofile (or source ~/.bash_profile for bash) to load the config into your current shell. Verify that ANDROID_HOME 
has been set by running echo $ANDROID_HOME and the appropriate directories have been added to your path by running echo $PATH.

## Creating a new application
If you previously installed a global react-native-cli package, please remove it as it may cause unexpected issues:
```shell
npm uninstall -g react-native-cli @react-native-community/cli
```
React Native has a built-in command line interface, which you can use to generate a new project. You can access it without 
installing anything globally using npx, which ships with Node.js. Let's create a new React Native project called "AwesomeProject":
```
npx react-native@latest init <your-project-name>
```

## Preparing the Android device
You will need an Android device to run your React Native Android app. This can be either a physical Android device, or more commonly, 
you can use an Android Virtual Device which allows you to emulate an Android device on your computer.

Either way, you will need to prepare the device to run Android apps for development.

### Using a physical device
If you have a physical Android device, you can use it for development in place of an AVD by plugging it in to your computer using a 
USB cable and following the instructions [here](https://reactnative.dev/docs/running-on-device)

### Using a virtual device
If you use Android Studio to open ./AwesomeProject/android, you can see the list of available Android Virtual Devices (AVDs) by opening
the "AVD Manager" from within Android Studio. Look for an icon that looks like this:

If you have recently installed Android Studio, you will likely need to create a new AVD. Select "Create Virtual Device...", then pick 
any Phone from the list and click "Next", then select the Tiramisu API Level 33 image.

Click "Next" then "Finish" to create your AVD. At this point you should be able to click on the green triangle button next to your AVD 
to launch it, then proceed to the next step.

## Running React Native application
### Step 1: Start Metro
```shell
npx react-native start
```
### Step 2: Start your application
```shell
npx react-native run-android
```




# React Native Environment CLI Setup - macOS -> Target IOS App

## Installing dependencies
You will need Node, Watchman, the React Native command line interface, a Ruby version manager, Xcode and CocoaPods.

While you can use any editor of your choice to develop your app, you will need to install Xcode in order to set up 
the necessary tooling to build your React Native app for iOS.

## Node & Watchman
```shell
brew install node
brew install watchman
```

## Ruby
React Native uses a .ruby-version file to make sure that your version of Ruby is aligned with what is needed. Currently, macOS 13.2 is shipped with Ruby 2.6.10, which is not what is required by this version of React Native (2.7.6). Our suggestion is to install a Ruby version manager and to install the proper version of Ruby in your system.

Some common Ruby version manager are:
[rbenv](https://github.com/rbenv/rbenv)
[RVM](https://rvm.io/)
[chruby](https://github.com/postmodern/chruby)
[asdf-vm](https://github.com/asdf-vm) with the [asdf-ruby](https://github.com/asdf-vm/asdf-ruby) plugin

To check what is your current version of Ruby, you can run this command:
```shell
ruby --version
```
React Native [uses](https://github.com/facebook/react-native/blob/v0.71.3/.ruby-version) this version of Ruby. You can also find which version your specific project needs in the .ruby-version file at root of your RN project.

## Xcode
The easiest way to install Xcode is via the [Mac App Store.](https://apps.apple.com/us/app/xcode/id497799835?mt=12) Installing Xcode will also install the iOS Simulator and all the necessary tools to build your iOS app.

If you have already installed Xcode on your system, make sure it is version 10 or newer.

## Command Line Tools
You will also need to install the Xcode Command Line Tools. Open Xcode, then choose "Preferences..." from the Xcode menu. Go to the Locations panel and install the tools by selecting the most recent version in the Command Line Tools dropdown.

## Installing an iOS Simulator in Xcode
To install a simulator, open Xcode > Preferences... and select the Components tab. Select a simulator with the corresponding version of iOS you wish to use.

## CocoaPods
[CocoaPods](https://cocoapods.org/) is one of the dependency management system available for iOS. It is built with Ruby and you can install it using the version of Ruby you configured with in the previous steps.

## Creating a new application
If you previously installed a global react-native-cli package, please remove it as it may cause unexpected issues:
```shell
npm uninstall -g react-native-cli @react-native-community/cli
```
You can use React Native's built-in command line interface to generate a new project. 
```shell
npx react-native@latest init <your-project-name>
```
## Running your React Native application
### Step 1: Start Metro
To start Metro, run npx react-native start inside your React Native project folder:
```shell
npx react-native start
```
Step 2: Start your application
```shell
npx react-native run-ios
```












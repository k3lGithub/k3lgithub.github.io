## Setup Appium on Mac
This will be a step by step for those who are looking to use `Appium` with `Mac`, `Java`, `Maven` and `SDK command line tool`.
A simple Caclulator test will be carried out at the end of the instructions.

### Prerequisites
- homebrew
- xcode
- NodeJS
- JAVA JDK 7 or higher

We will also be installing the following

- Android SDK and command line tool
- IntelliJ IDE
- Maven

### Homebew
Starting with installing homebrew, open `Terminal` and type below to install
```markdown
> ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- Other useful command lines

```markdown
> brew doctor
> brew search
> brew update
```

### Xcode and command line tool
Check if you have Xcode installed. If not install Xcode from App Store.
You may need to upgrade macOS accordingly in order to be able to install latest Xcode
```markdown
xcode-select --install (Xocde command line tool)
```

### Install node.js and npm
Check if node and npm are installed
```markdown
> node --version
> npm -- version
> npm update -g
> brew install node
> npm install -g npm
```
### Java JDK
Firstly, you can check if you have Java already installed by running below in the terminal
```markdown
> java -version (Should be v7 or higher)
```
Download and install java JDK

`ADD IMAGE`

If you are not sure where it is installed, try the below to find it’s `path`.
```markdown
> which java
```
 **NOTE:** This will be useful when we set the enviorment variables later on.
### Maven
```markdown
> brew install maven
> mvn -version
```
To check if Maven is installed and it’s `path`

### Android SDK
The version I have installed was `tools_r25.2.3-macosx.zip` or you can download `Android Studio` and use it's sdkmanager.
`Add image of the folders`
Save the folders under the desired `path`

### Add Enviorment variables
Update enviroment variables for Java JDK, Android SDK and maven paths

Open .profile and add the below variables 
Replace the paths from above and set the environment variables. Ensure to add correct paths /bin and /tools etc accordingly.

```markdown
> nano ~/.bash_profile

export ANDROID_HOME=/Users/user/Library/Android/androidSDK
export PATH=$ANDROID_HOME/tools:$PATH
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-10.0.1.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
export PATH=“/usr/local/Cellar/maven/3.5.3/libexec/bin”:$PATH
```
**NOTE:** If your sdk has “platform-tools” folder, also add below to the file
```markdown
export PATH=$ANDROID_HOME/platform-tools:$PATH
```
`Add image after changing the variable`

save and exit (or) you can exit and choose Y to save

Source the .profile after making the changes
```markdown
> source ~/.bash_profile
> echo $JAVA_HOME  (or) > echo $ANDROID_HOME  etc. and it should return the values
> android
```
It should launch Android `SDK Manager` and this will confirm sdk is installed successfully

### Installing SDK and build tools using SDK Manager
Choose packages you want to install. Recent `SDK tools`, `Platform Tools` and `Build Tools` necessary.
From the `Extra` folder, also choose `Intel x86 Emulator Accelerator`

`Add image`

Accept licence and install

`Add image`

This will take a while to download...

### Install Appium
```markdown
> npm install -g appium
```
**NOTE:** If you come across the following error, try downgrading the node as node v10 might not be compatible with appium@1.8.0. “Error trying to install Chromedriver binary. Waiting and trying again. frame.getFileName is not a function”
In that case, `downgrade node` to desired version
```markdown
> node —version  (to see the current version)
> brew install node@8 (node v8 or any desired version)
> brew search node (to see what is currently available)
> brew unlink node (if current version is node)
> brew link node@8 (if you can’t use this try the below force link)
> brew link --overwrite node@8 --force
```
Confirm the current version and try `installing Appium again`

### Verify `Appium Dependencies` are installed
```markdown
> npm install -g appium-doctor
> appium-doctor
> appium-doctor --ios (checks ios setup)
> appium-doctor --android (checks android setup)
```
**NOTE:** If getting `access or permission issues`, try
```markdown
(eg. path)
> sudo mkdir /usr/local/frameworks 
> sudo chown $(whoami):admin /usr/local/frameworks
```
To set the root permission (or) Go To path > Info > permission > Click on lock and add your write access

`Add Image`

### Install Other and missing Dependencies if necessary
```markdown
> brew install libimobiledevice --HEAD
> brew install carthage
> brew link carthage
> npm install device console
> brew install ios-deploy
> gem install xcpretty
> npm install authorize-ios
> authorize-ios
```

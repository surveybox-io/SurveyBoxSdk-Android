# SurveyBoxSdk-Android
The Surveybox Mobile SDK allows you to collect feedback from your mobile app users. Installed in your app, the SDK will enable you to trigger targeted surveys to better understand your users and collect their opinions about your products.

The SDK is maintained and supported by Survicate - The Customer Experience & Survey Software.

Installation The SDK can be installed in the IDE(Android Studio) using the methods described below.

**Step 1.** Download the .aar file in  computer from (https://github.com/surveybox-io/SurveyBoxSdk-Android).

**Step 2.** To create a new project in Android Studio, follow these steps:

**if you already created the project then follow the Step 3**

Launch Android Studio on your computer.

On the welcome screen, click on "Start a new Android Studio project." If you already have a project open, you can go to "File" > "New" > "New Project" instead.

In the "Create New Project" window, you'll be prompted to configure your new project. Here are the key steps in the process:

a. Application Name: Enter a name for your project. This is the name that will be displayed on the user's device.

b. Company Domain: Enter a unique identifier for your project, typically in reverse domain name notation (e.g., com.example).

c. Project Location: Choose a directory where you want to save your project files.

d. Language: Select the programming language you prefer (Java or Kotlin).

e. Minimum SDK: Choose the minimum Android version your app will support.

f. Select the desired form factors and orientation for your app.

g. Add Activity: Choose an activity template for your app's main screen. You can select "Empty Activity" to start with a blank activity.

h. Customize the activity details such as activity name, layout name, etc.

i. Click on "Finish" to create your project.

Android Studio will start building your project and setting up the necessary files and dependencies. This process may take a few moments.

Once the project is created, you'll see the project structure in the "Project" view on the left side of the IDE. The main components of your project, such as source code files, resources, and manifests, can be found here.

**Step 3.** In the Project view (usually located on the left side of the IDE), navigate to the "app" module.
Expand the "app" module by clicking on the arrow next to it.
Look for a folder named "libs" within the "app" module. 

Copy the .aar file into the "libs" folder of your Android project. If the "libs" folder doesn't exist, you can create it manually in the "app" module.

**Step 4.** Open your project's "build.gradle" file, located in the "app" module. It should be under the following path: "app/build.gradle".

In the "build.gradle" file, locate the "dependencies" block.

 Add the following line inside the "dependencies" block to include the .aar file
 
**implementation files('libs/surveybox-debug.aar')**

Sync your project by clicking on the "Sync Now" button that appears in the toolbar. This action ensures that the new dependency is recognized and properly added to your project.

After performing these steps, the .aar file will be included in your Android project, and you can use its classes, resources, and other assets in your code. Remember to rebuild your project to make sure the changes take effect.

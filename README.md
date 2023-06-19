# SurveyBoxSdk-Android
The Surveybox Mobile SDK allows you to collect feedback from your mobile app users. Installed in your app, the SDK will enable you to trigger targeted surveys to better understand your users and collect their opinions about your products.

The SDK is maintained and supported by Survicate - The Customer Experience & Survey Software.

Installation The SDK can be installed in the IDE(Android Studio) using the methods described below.

**1.** To create a new project in Android Studio, follow these steps:

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





# Requirements

Using Surveybox Mobile SDK requires an account at [Survaybox](https://surveybox.io/). Sign up for free and find your workspace key in the Access Keys tab.

**Minimum SDK:** The minimum SDK required by the SDK is set to 26 or higher.

**Compile SDK:** The SDK is compiled against SDK version 33. 

**Dependencies:** The SDK has several dependencies listed in the dependencies block. To use the SDK, the project should include the necessary dependencies in its own Gradle file. These dependencies include:

```implementation 'androidx.core:core-ktx:1.10.1'

 implementation 'androidx.appcompat:appcompat:1.6.1'

 implementation 'com.google.android.material:material:1.9.0'

implementation 'com.google.code.gson:gson:2.9.0'

implementation 'androidx.navigation:navigation-fragment-ktx:2.6.0'

implementation 'androidx.navigation:navigation-ui-ktx:2.6.0'```

Build Features: The SDK utilizes View Binding, so the project's Gradle file should have viewBinding set to true under the buildFeatures block.
![view binding](https://github.com/surveybox-io/SurveyBoxSdk-Android/assets/79449782/bcaade5e-bfeb-42c1-8f8d-76a80d496ac4)

  **buildFeatures{
        viewBinding true
    }**


**Java Version:** The SDK is set to use Java version 8. Make sure that the project is compatible with Java 8 or above.

By ensuring that the project meets the above requirements, you should be able to successfully install and use this SDK in your project.

# Installation
![projet screenshot](https://github.com/surveybox-io/SurveyBoxSdk-Android/assets/79449782/644d8bfd-284a-498a-b9dc-a8ddbb2fe014)


**Step 1.** [Download the latest Surveybox SDK for Android](https://github.com/surveybox-io/SurveyBoxSdk-Android)
 and extract the zip. This is a ~194kb file and might take some time to download.
Open your existing Android Studio Project.

**Step 2.** In the Project view (usually located on the left side of the IDE), navigate to the "app" module.
Expand the "app" module by clicking on the arrow next to it.
Look for a folder named "libs" within the "app" module. 

Copy the .aar file into the "libs" folder of your Android project. If the "libs" folder doesn't exist, you can create it manually in the "app" module.

**Step 3.** Open your project's "build.gradle" file, located in the "app" module. It should be under the following path: "app/build.gradle".

In the "build.gradle" file, locate the "dependencies" block.

 Add the following line inside the "dependencies" block to include the .aar file
 
**implementation files('libs/surveybox-debug.aar')**

Sync your project by clicking on the "Sync Now" button that appears in the toolbar. This action ensures that the new dependency is recognized and properly added to your project.

After performing these steps, the .aar file will be included in your Android project, and you can use its classes, resources, and other assets in your code. Remember to rebuild your project to make sure the changes take effect.


# Configuring Framework API Key

**Step 1.** Create a class in your project and copy the below code in that class.
```kotlin scrollbar
class MyApplication : Application() {
    lateinit var configSurvey: ConfigSurvey

    // This method is called when the application is created
    @RequiresApi(Build.VERSION_CODES.O)
    override fun onCreate() {
        super.onCreate()

        // Initialize the ConfigSurvey instance with the application context
        configSurvey = ConfigSurvey(applicationContext)
        // Configure the survey by providing the app key and email
        configSurvey.configSurvey("Your Api Key", "Email Id")
    }

    // This method is used to check and show the survey
    @RequiresApi(Build.VERSION_CODES.O)
    fun checkAndShowSurvey(activity: Activity, presentClass: String) {

        // Get the trigger class from the ConfigSurvey instance
        val triggerClass = configSurvey.getTriggerClass()

        // Check if the present class matches the trigger class
        if (presentClass == triggerClass) {
            // Show the survey
            showSurvey(activity as AppCompatActivity)
        }
    }

    // This method is used to show the survey dialog
    @RequiresApi(Build.VERSION_CODES.O)
    fun showSurvey(activity: AppCompatActivity) {
        val welcomeSurvey = WelcomeSurvey()
        welcomeSurvey.show(activity.supportFragmentManager, "WelcomeSurvey")
    }
}
```
**Step 2.** Include the below lines in Project
Trigger survey  automatically by matching the class name

Calling the survey from activity  
  Replace MainActivity with your Activity 
  ** (application as MyApplication).checkAndShowSurvey(this,"Your Activity Class name or this.javaClass.simpleName")**

Call Survey on Button click from Activity

  (application as MyApplication).showSurvey(this)
 
 **Trigger survey  automatically by matching the class name of the fragment **
  if you are calling the survey from fragment 
 Replace fragmentClassName with your Fragment class name

**(requireActivity().application as MyApplication).checkAndShowSurvey(requireActivity(), "Your Fragment class name")**

Call Survey on Button click from Fragment

 ** (requireActivity().application as MyApplication).showSurvey(requireActivity() as AppCompatActivity)**
 






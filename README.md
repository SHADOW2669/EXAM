### **PART – A**

*Answer any six of the following questions.*

**a) List any four features of android.**
Four key features of the Android operating system are:
1.  **Open Source:** The source code for Android (AOSP) is free and open, allowing manufacturers to customize it for their devices.
2.  **Large App Ecosystem:** Google Play Store provides access to millions of applications, offering a vast range of functionality to users.
3.  **Rich Connectivity:** Android natively supports various connectivity technologies, including Wi-Fi, Bluetooth, NFC, and Hotspot.
4.  **Multi-tasking:** Users can run multiple applications simultaneously and switch between them seamlessly.

---
**b) Expand AVD, DVM.**
* **AVD:** Android Virtual Device
* **DVM:** Dalvik Virtual Machine

---
**c) What do you mean by fragment?**
A **Fragment** represents a reusable, modular portion of an application's user interface. It is like a "sub-activity" that has its own lifecycle and UI layout. Multiple fragments can be combined within a single Activity to build a multi-pane UI, and a single fragment can be reused across multiple activities, promoting modularity and adaptability for different screen sizes (like phones and tablets).

---
**d) Why the android manifest file is used?**
The `AndroidManifest.xml` file is a crucial configuration file for an Android application. Its primary uses are:
* To **declare the app's components**, such as activities, services, broadcast receivers, and content providers.
* To request **permissions** the app needs to access protected parts of the system or other apps (e.g., internet, camera).
* To declare the **hardware and software features** the app requires, which is used by Google Play to filter which devices can install the app.

---
**e) What do you mean by list view?**
A **`ListView`** is a classic Android UI component (a `ViewGroup`) that displays a vertically scrollable list of items. The items in the list are not defined directly in the layout but are dynamically populated from a data source (like an array or database) using an **Adapter**. The Adapter acts as a bridge between the data and the `ListView`.

**Note:** In modern Android development, `RecyclerView` is preferred over `ListView` as it is more efficient and flexible.

---
**f) List the different types of layouts available for android applications.**
The main types of layouts (ViewGroups) in Android are:
* **`ConstraintLayout`**: The most powerful and flexible layout manager; allows creating complex UIs with a flat view hierarchy.
* **`LinearLayout`**: Arranges child views in a single direction, either vertically or horizontally.
* **`RelativeLayout`**: Arranges child views in relation to each other or to the parent layout.
* **`FrameLayout`**: The simplest layout, designed to hold a single child view or stack views on top of each other.
* **`TableLayout`**: Arranges children into rows and columns.

---
**g) What do you mean by projection?**
In the context of Android's Content Providers and databases, a **projection** is an array of strings representing the specific columns of data you want to retrieve from a query. It is analogous to the `SELECT column1, column2` clause in an SQL statement. Using a projection is an efficient practice as it ensures you only fetch the data your application actually needs.

---
**h) What is the use of DBA adapter helper class?**
This typically refers to the **`SQLiteOpenHelper`** class. It is an abstract helper class used to simplify database management in Android. Its main uses are:
* **Database Creation:** It handles the initial creation of the SQLite database file if it doesn't already exist via the `onCreate()` method.
* **Version Management:** It manages database schema upgrades. When the database version number is increased, the `onUpgrade()` method is called to handle migrations (e.g., adding new tables or columns).

***

### **PART – B**

### **Unit – I**

**2. a) Explain android architecture with a neat diagram.**

The Android architecture is a software stack organized into five main layers. Each layer provides different services to the layer directly above it.

**Diagram of Android Architecture:**
```
+------------------------------------------+
|            APPLICATIONS                  |
| (Home, Contacts, Phone, Browser, etc.)   |
+------------------------------------------+
|        APPLICATION FRAMEWORK             |
| (Activity Manager, Window Manager,       |
|  Content Providers, View System, etc.)   |
+------------------------------------------+
|       NATIVE C/C++ LIBRARIES      | ANDROID RUNTIME (ART)  |
| (OpenGL, WebKit, SQLite, etc.)    | (Core Libraries & VM)  |
+------------------------------------------+
|     HARDWARE ABSTRACTION LAYER (HAL)     |
| (Camera, Bluetooth, Wi-Fi Modules, etc.) |
+------------------------------------------+
|              LINUX KERNEL                |
| (Drivers, Power Management, Memory, etc.)|
+------------------------------------------+
```

**Explanation of Layers:**

1.  **Applications Layer:** This is the top layer where users interact. It includes all installed applications, both system apps (like Phone, Contacts, Browser) and third-party apps downloaded from the Play Store.

2.  **Application Framework:** This layer provides high-level services that applications use directly. It consists of API managers that manage the basic functions of the phone, such as:
    * **Activity Manager:** Manages the lifecycle of applications.
    * **Content Providers:** Allows applications to share data with each other.
    * **View System:** Provides a rich set of UI elements like buttons, lists, and layouts.
    * **Notification Manager:** Manages all app notifications.

3.  **Android Runtime (ART) & Native Libraries:**
    * **Android Runtime (ART):** This is the engine that runs Android apps. It replaced the older Dalvik Virtual Machine (DVM). ART uses Ahead-Of-Time (AOT) compilation to compile app bytecode into native machine code upon installation, resulting in faster app execution.
    * **Native C/C++ Libraries:** This layer includes a set of core C/C++ libraries used by various components of the Android system. Examples include SQLite (for database support), WebKit (for browser rendering), and OpenGL ES (for 3D graphics).

4.  **Hardware Abstraction Layer (HAL):** The HAL provides a standard interface that exposes device hardware capabilities to the higher-level application framework. It allows Android to be agnostic about lower-level driver implementations. It consists of library modules for specific hardware components like the camera, Bluetooth, and Wi-Fi.

5.  **Linux Kernel:** At the bottom of the stack is the Linux Kernel. Android is built on top of the Linux kernel, which is responsible for core system services like process management, memory management, power management, and device drivers.

---
**2. b) Explain different steps that is required to launch an android application.**

The process of launching an Android application starts when a user taps the app's icon and involves several system components working together.

1.  **User Tap:** The user taps the application icon on a launcher app (e.g., the home screen).

2.  **Launcher Sends an Intent:** The launcher app sends an `Intent` to the Android system. This intent is an `implicit intent` that specifies the action (`ACTION_MAIN`) and category (`CATEGORY_LAUNCHER`) to identify the app's main entry point.

3.  **Activity Manager Service (AMS) Receives Intent:** The system's central **Activity Manager Service (AMS)** receives this intent. AMS is responsible for managing the state and lifecycle of all activities.

4.  **Process Creation (Zygote Fork):** AMS checks if a process for the target application already exists.
    * If **no process exists**, AMS requests a new process from a special system process called **Zygote**.
    * Zygote is a pre-initialized process that contains core system libraries. It **forks** (creates a copy of) itself to create a new, dedicated process for the application. This forking mechanism allows apps to start up quickly.

5.  **Process Initialization:** The newly created process starts the **Android Runtime (ART)** and loads the application's code (the APK file).

6.  **Activity Instance Creation:** Once the process is ready, AMS instructs it to create an instance of the app's main (launcher) activity class.

7.  **Activity Lifecycle Callbacks:** The new activity instance then goes through its lifecycle callbacks in sequence:
    * `onCreate()`: The activity is initialized. The UI layout is inflated, and initial setup is performed here.
    * `onStart()`: The activity becomes visible to the user.
    * `onResume()`: The activity comes to the foreground and is ready for user interaction.

8.  **App is Visible:** The activity's window is drawn on the screen, and the application is now fully launched and running.

---
**3. a) Write a note on android studio IDE.**

**Android Studio** is the official Integrated Development Environment (IDE) for Android application development, built by Google on JetBrains' IntelliJ IDEA software. It provides a comprehensive suite of tools for developers to build, test, and debug high-quality Android apps.

Key features of Android Studio include:

* **Intelligent Code Editor:** Provides advanced code completion, refactoring, and static code analysis for Kotlin, Java, and C++ code. It highlights errors and offers suggestions to improve code quality.
* **Visual Layout Editor:** Allows developers to build UI layouts by dragging and dropping UI widgets. It provides a real-time preview of how the layout will look on different screen sizes and API versions.
* **Gradle-Based Build System:** Uses Gradle as its build automation system, offering great flexibility in managing dependencies, creating build variants (e.g., free vs. paid versions), and customizing the build process.
* **Fast and Feature-Rich Emulator:** Includes a powerful Android Emulator to run and test apps on a wide range of virtual devices and Android versions without needing a physical device.
* **Integrated Profiling Tools:** Provides tools to monitor app performance, including a CPU Profiler, Memory Profiler, and Network Profiler. These help identify and fix performance bottlenecks.
* **APK Analyzer:** Allows you to inspect the contents of your built APK file to understand its size composition, check resource files, and diagnose DEX file issues.
* **Built-in Version Control:** Integrates seamlessly with popular version control systems like Git, allowing developers to manage their source code directly within the IDE.

---
**3. b) Write a note on android SDK with its components.**

The **Android SDK (Software Development Kit)** is a mandatory collection of software tools, libraries, and documentation required to develop applications for the Android platform. It is managed and installed via the SDK Manager within Android Studio.

The core components of the Android SDK include:

1.  **SDK Platforms:** Each version of the Android OS (e.g., Android 12, Android 13) has its own "platform." Each platform includes the `android.jar` file, which contains all the public classes and methods of the Android framework for that specific API level. You must install at least one platform to compile your app.

2.  **SDK Build-Tools:** This package contains the tools required to build an Android application from source code into a deployable APK. Key tools include:
    * **aapt2 (Android Asset Packaging Tool):** Compiles app resources into a binary format.
    * **d8:** Compiles Java or Kotlin bytecode into DEX (Dalvik Executable) bytecode that runs on the Android Runtime (ART).
    * **zipalign:** Optimizes the final APK file for efficient memory usage.

3.  **SDK Platform-Tools:** This package contains platform-dependent tools that are updated for each new Android version. It is essential for interacting with an Android device (physical or virtual).
    * **adb (Android Debug Bridge):** A command-line tool to communicate with a device for installing apps, debugging, and accessing the device shell.
    * **fastboot:** A tool for flashing firmware onto a device.

4.  **Android Emulator:** A virtual device emulator that allows you to test your application on various screen sizes, hardware configurations, and Android versions without needing a physical device. It works with **System Images**, which are copies of the Android OS for different API levels and architectures (e.g., x86, ARM).

5.  **Documentation:** A local copy of the Android developer documentation, including API references and guides.

### **Unit – II**

**4. a) Explain various android terminologies.**

Here are some fundamental terminologies used in Android development:

1.  **Activity:** An **Activity** is a single, focused screen with which a user can interact. An application is typically composed of one or more activities that are loosely bound to each other. For example, an email app might have one activity to show a list of emails, another to compose an email, and a third for settings.

2.  **Service:** A **Service** is an application component that can perform long-running operations in the background. It does not provide a user interface. For example, a service might play music in the background while the user is in a different app.

3.  **Intent:** An **Intent** is a messaging object used to request an action from another app component. Intents can be used to start an activity, start a service, or deliver a broadcast. They are the glue that binds different components together, both within a single app and between different apps.

4.  **Content Provider:** A **Content Provider** manages access to a central repository of data, acting as an abstraction layer over a database. It allows one application to securely share its data with other applications. For example, the Android system provides a Content Provider for managing user contacts.

5.  **Broadcast Receiver:** A **Broadcast Receiver** is a component that listens for and responds to system-wide broadcast announcements (Intents). For example, it can react to events like the system booting up, the network connection changing, or a new SMS arriving.

6.  **APK (Android Package Kit):** This is the file format used by the Android operating system for the distribution and installation of mobile apps. The APK file contains all of the elements that an app needs to install correctly on a device, including its compiled code, resources, assets, and manifest file.

---
**4. b) Write a note on configuring intent filter.**

An **Intent Filter** is a declaration in an app's manifest file (`AndroidManifest.xml`) that specifies the types of intents that an application component (like an Activity, Service, or Broadcast Receiver) is capable of receiving. When another component sends an implicit intent, the Android system finds the appropriate component to respond to by comparing the intent to the intent filters declared in the manifests of all installed apps.

An intent filter is declared using the `<intent-filter>` element inside the tag of the component it applies to. It is defined by three core sub-elements:

1.  **`<action>`:**
    * Specifies the intent action that the component can handle. This is a string that represents a generic action to be performed, like `android.intent.action.VIEW` (to display data) or `android.intent.action.SEND` (to share data).
    * A filter must contain at least one `<action>` element.

2.  **`<category>`:**
    * Specifies the intent category. This provides additional information about the action. For example, `android.intent.category.LAUNCHER` means the activity should be shown as a top-level app in the system launcher. `android.intent.category.DEFAULT` is required for an activity to receive implicit intents.

3.  **`<data>`:**
    * Specifies the type of data the component can handle. It can be defined by various attributes like `android:mimeType` (e.g., `image/jpeg`), `android:scheme` (e.g., `http`), `android:host`, `android:port`, and `android:path`.
    * A filter can have multiple `<data>` specifications.

**Example Code:**
The following is an intent filter for a main activity that should appear in the app launcher.
```xml
<application ...>
    <activity android:name=".MainActivity" android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
    </activity>
</application>
```

---
**5. a) Explain life cycle of activity with neat diagram.**

The **Activity lifecycle** is the set of states an Activity can be in during its entire lifetime, from when it is first created until it is destroyed. The Android system manages this lifecycle through a series of callback methods that are invoked at different stages.

**Activity Lifecycle Diagram:**
```
                      +----------------+
                      | Activity Launch|
                      +-------+--------+
                              |
                              v
                      +----------------+
      +-------------> |  onCreate()    | <-----------------+
      |               +-------+--------+                   |
      |                       |                            | (Process killed)
      |                       v                            |
      |               +----------------+                   |
      |               |   onStart()    | <------------+    |
      |               +-------+--------+              |    |
      |                       |                       |    |
      |                       v                       |    |
      |               +----------------+              |    |
      |               |  onResume()    | (Activity in foreground)
      |               +-------+--------+              |
      |                       | (Another Activity comes into foreground)
      |                       v                       |
      |               +----------------+              |
      |               |   onPause()    | --------------+
      |               +-------+--------+
      | (User returns         | (Activity no longer visible)
      |  to Activity)          v
      |               +----------------+
+-----> |               |   onStop()     |
|     |               +-------+--------+
|     |                       | (Activity is finishing or being destroyed by system)
|     |                       v
|     +---------------+----------------+
|                     |  onDestroy()   |
|                     +----------------+
|                           |
|                           v
|                     +----------------+
|                     | Activity       |
|                     |  Shutdown      |
|                     +----------------+
|
| (From onStop(), if user navigates back to activity)
+-----------------------+ onRestart() +-----------------------
```

**Explanation of Lifecycle Callbacks:**

* **`onCreate()`**: Called once when the activity is first created. This is where you should perform all basic application startup logic, such as inflating the UI, initializing variables, and binding data.
* **`onStart()`**: Called when the activity becomes visible to the user.
* **`onResume()`**: Called when the activity is in the foreground and ready for user interaction.
* **`onPause()`**: Called when the activity is partially obscured (e.g., by a dialog) but still visible. This is the place to save any unsaved data and stop resource-intensive tasks.
* **`onStop()`**: Called when the activity is no longer visible to the user (it's in the background).
* **`onRestart()`**: Called after an activity has been stopped, just before it is started again.
* **`onDestroy()`**: Called just before the activity is destroyed. This can happen because the user is finishing the activity (e.g., by pressing back) or because the system is temporarily destroying it to save space. This is the final cleanup point.

---
**5. b) How we can register an activity with manifest file? Explain.**

Every activity in an Android application **must** be registered in the `AndroidManifest.xml` file. If an activity is not declared in the manifest, the system will not be aware of it, and any attempt to start it will cause the application to crash.

Registration is done by adding an **`<activity>`** element inside the main **`<application>`** element.

**Explanation:**
The `<activity>` tag has several attributes that define its properties and behavior.

* **`android:name`**: This is the **only required attribute**. It specifies the fully qualified class name of the activity (e.g., `com.example.myapp.MainActivity`) or a shorthand name (`.MainActivity`) if it's in the same package defined in the manifest.

* **`android:label`**: A user-readable string for the activity's title. This is often displayed in the action bar.

* **`android:icon`**: A drawable resource for the activity's icon.

* **`android:theme`**: A reference to a style resource that defines the overall theme for the activity.

* **`android:exported`**: A boolean value that indicates whether the activity can be launched by components of other applications.
    * `true`: The activity is accessible to other apps.
    * `false`: The activity can only be launched by components of the same app.

**Example Code:**
This example shows how to register two activities. `MainActivity` is the main entry point, and `DetailActivity` is a secondary screen.

```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.example.myapp">

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        <activity
            android:name=".MainActivity"
            android:label="@string/title_activity_main"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>

        <activity
            android:name=".DetailActivity"
            android:label="Details"
            android:exported="false" />

    </application>
</manifest>
```

### **Unit – III**

**6. a) List and explain common attributes used by view and view groups.**

Views and ViewGroups (layouts) share a set of common XML attributes that are used to define their size, position, and appearance.

1.  **`android:id`**:
    * **Explanation**: Provides a unique identifier for a view within the layout. This ID is used to reference the view from Java/Kotlin code (e.g., using `findViewById()`) or from other XML attributes.
    * **Example**: `android:id="@+id/my_button"`

2.  **`android:layout_width`** and **`android:layout_height`**:
    * **Explanation**: Specify the width and height of the view.
    * **Common Values**:
        * **`match_parent`**: The view should be as big as its parent.
        * **`wrap_content`**: The view should be just big enough to enclose its content.
        * **Specific Dimension**: A fixed size in density-independent pixels (e.g., `100dp`).

3.  **`android:padding`**:
    * **Explanation**: Sets the padding (internal spacing) on all four sides of the view. It defines the space between the view's content and its border. You can also specify padding for individual sides (`android:paddingLeft`, `android:paddingTop`, etc.).
    * **Example**: `android:padding="16dp"`

4.  **`android:layout_margin`**:
    * **Explanation**: Sets the margin (external spacing) on all four sides of the view. It defines the space outside the view, between it and adjacent views or the parent. You can also specify margins for individual sides (`android:layout_marginLeft`, etc.).
    * **Example**: `android:layout_margin="8dp"`

5.  **`android:background`**:
    * **Explanation**: Sets the background for the view. The value can be a color or a reference to a drawable resource (like an image or a shape).
    * **Example**: `android:background="#FFFFFF"` or `android:background="@drawable/my_background"`

6.  **`android:visibility`**:
    * **Explanation**: Controls the visibility of the view.
    * **Values**:
        * **`visible`**: The view is visible (default).
        * **`invisible`**: The view is hidden, but it still takes up space in the layout.
        * **`gone`**: The view is hidden, and it does not take up any space in the layout.

---
**6. b) Explain progress bar view with its working and example.**

A **`ProgressBar`** is a UI widget that indicates the progress of an operation. It provides visual feedback to the user that a task is running, which improves the user experience.

There are two main styles of progress bars:

1.  **Indeterminate ProgressBar:**
    * This style is used when the duration or progress of the task is unknown. It shows a continuous, cyclical animation (like a spinning wheel).
    * You use this for tasks like waiting for a network response where you can't predict how long it will take.

2.  **Determinate ProgressBar:**
    * This style is used when the progress of the task can be measured (e.g., downloading a file, processing data). It is typically displayed as a horizontal bar that fills up from 0% to 100%.
    * Its progress is updated programmatically.

**Working:**
You add the `<ProgressBar>` element to your XML layout file. To update a determinate progress bar, you get a reference to it in your Java/Kotlin code and call the `setProgress(int)` method periodically to reflect the current state of the task.

**Example Code:**

**XML Layout (`activity_main.xml`):**
```xml
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Loading... (Indeterminate)"/>
    <ProgressBar
        android:id="@+id/indeterminateBar"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="32dp"
        android:text="Downloading... (Determinate)"/>
    <ProgressBar
        android:id="@+id/determinateBar"
        style="?android:attr/progressBarStyleHorizontal"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:max="100" />
</LinearLayout>
```

**Kotlin Code (`MainActivity.kt`):**
```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import android.widget.ProgressBar

class MainActivity : AppCompatActivity() {
    private var progressStatus = 0
    private val handler = Handler(Looper.getMainLooper())

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val determinateBar = findViewById<ProgressBar>(R.id.determinateBar)

        // Simulate updating the determinate progress bar
        Thread {
            while (progressStatus < 100) {
                progressStatus += 1
                handler.post {
                    determinateBar.progress = progressStatus
                }
                try {
                    Thread.sleep(50)
                } catch (e: InterruptedException) {
                    e.printStackTrace()
                }
            }
        }.start()
    }
}
```

---
**7. a) What is table layout? Explain with a suitable code.**

**`TableLayout`** is a `ViewGroup` that arranges its child elements into a grid of rows and columns, similar to an HTML `<table>`.

**Explanation:**
* A `TableLayout` container does not display borders or lines for its rows, columns, or cells. The structure is defined by the arrangement of its children.
* The direct children of a `TableLayout` must be **`<TableRow>`** elements. Each `<TableRow>` object defines a single row in the table.
* Each `<TableRow>` then contains one or more `View` objects (like `TextView`, `Button`, `EditText`), where each View represents a cell in that row.
* The width of each column is determined by the widest cell in that column.
* A cell can be made to span multiple columns by using the `android:layout_span` attribute on the View inside a `TableRow`.
* A column can be made to stretch to fill any remaining empty space using the `android:stretchColumns` attribute on the `TableLayout` itself.

**Suitable Code Example:**
This XML code creates a simple 2x2 table to display user information.

```xml
<TableLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:padding="16dp"
    android:stretchColumns="1">
    <TableRow>
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Username:"
            android:textStyle="bold"
            android:padding="8dp"/>

        <EditText
            android:layout_width="0dp" android:layout_height="wrap_content"
            android:hint="Enter username"
            android:padding="8dp"/>
    </TableRow>

    <TableRow>
        <TextView
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="Password:"
            android:textStyle="bold"
            android:padding="8dp"/>

        <EditText
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:inputType="textPassword"
            android:hint="Enter password"
            android:padding="8dp"/>
    </TableRow>

    <TableRow>
        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Login"
            android:layout_span="2"
            android:layout_marginTop="16dp"/>
    </TableRow>

</TableLayout>
```

---
**7. b) Write a note on date and time picker view.**

**`DatePicker`** and **`TimePicker`** are UI controls that provide a standardized way for users to select a date (year, month, day) and a time (hour, minute), respectively. Using these standard controls ensures a consistent and intuitive user experience across all Android apps.

There are two primary ways to implement them:

1.  **As Views in a Layout:** You can embed `<DatePicker>` and `<TimePicker>` directly into your activity's XML layout file. This is less common as it can take up significant screen space.

2.  **As Dialogs:** The more common and recommended approach is to show them inside a dialog box. Android provides the **`DatePickerDialog`** and **`TimePickerDialog`** helper classes for this purpose. Displaying them as dialogs saves screen space and provides a clean, focused interface for selection.

**Working with Dialogs:**
The typical workflow is:
1.  The user clicks a button (e.g., "Select Date").
2.  In the button's `onClick` listener, you create an instance of `DatePickerDialog` or `TimePickerDialog`.
3.  You need to provide a listener (`OnDateSetListener` or `OnTimeSetListener`) to the dialog's constructor.
4.  The dialog is shown to the user.
5.  When the user selects a date/time and clicks "OK," the listener's callback method (`onDateSet` or `onTimeSet`) is invoked, providing you with the selected values.

**Example Code (using `DatePickerDialog` in Kotlin):**
This code shows how to display a `DatePickerDialog` when a button is clicked.

```kotlin
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.Button
import android.widget.Toast
import java.util.Calendar
import android.app.DatePickerDialog

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val selectDateButton = findViewById<Button>(R.id.selectDateBtn)

        selectDateButton.setOnClickListener {
            showDatePickerDialog()
        }
    }

    private fun showDatePickerDialog() {
        // Get current date to pre-fill the dialog
        val calendar = Calendar.getInstance()
        val year = calendar.get(Calendar.YEAR)
        val month = calendar.get(Calendar.MONTH)
        val day = calendar.get(Calendar.DAY_OF_MONTH)

        // Create the DatePickerDialog
        val datePickerDialog = DatePickerDialog(
            this,
            // Listener that gets called when a date is set
            DatePickerDialog.OnDateSetListener { view, selectedYear, selectedMonth, selectedDay ->
                val selectedDate = "$selectedDay/${selectedMonth + 1}/$selectedYear"
                Toast.makeText(this, "Selected Date: $selectedDate", Toast.LENGTH_LONG).show()
            },
            year,
            month,
            day
        )
        // Show the dialog
        datePickerDialog.show()
    }
}
```

### **Unit – IV**

**8. a) Explain how we can store the file to external storage or SD card.**

Storing files on external storage allows you to save data that should be accessible to other apps or the user, or that is too large for internal storage. The process involves checking for availability, getting the correct file path, and handling permissions.

**Note:** With modern Android (Android 10+), **Scoped Storage** has changed how apps access external storage. For app-specific files, the process below is still largely correct. For shared media, using `MediaStore` is the preferred approach.

Here are the traditional steps:

**Step 1: Declare Permissions in `AndroidManifest.xml`**
For older Android versions, you need to request permission to write to external storage.
```xml
<manifest ...>
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
</manifest>
```
*For Android 6.0 (API 23) and higher, you must also request these permissions from the user at runtime.*

**Step 2: Check if External Storage is Available**
Before trying to write, you must check if the storage is mounted and writable.
```kotlin
fun isExternalStorageWritable(): Boolean {
    return Environment.getExternalStorageState() == Environment.MEDIA_MOUNTED
}
```

**Step 3: Get the Correct Directory Path**
There are two types of directories on external storage:

* **App-Specific Storage:** This is the **recommended** location. Files stored here are private to your app and are automatically deleted when the user uninstalls your app. You do not need storage permissions to access this directory on Android 4.4+.
    * `Context.getExternalFilesDir(null)`: Gets the root directory for your app's private files on external storage.

* **Public Shared Storage:** For files that should be publicly available to other apps and the user (e.g., photos, documents).
    * `Environment.getExternalStoragePublicDirectory(Environment.DIRECTORY_PICTURES)`: Gets the public Pictures directory. This method is now deprecated in favor of Scoped Storage APIs.

**Step 4: Write the File**
Use standard Java I/O classes to write your data to a file.

**Example Code (Writing to App-Specific External Storage):**
```kotlin
import android.os.Bundle
import android.os.Environment
import androidx.appcompat.app.AppCompatActivity
import java.io.File
import java.io.FileOutputStream

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // ...

        if (isExternalStorageWritable()) {
            val file = File(getExternalFilesDir(null), "MyTestFile.txt")
            try {
                val fos = FileOutputStream(file)
                fos.write("This is a test.".toByteArray())
                fos.close()
                // File written successfully
            } catch (e: Exception) {
                e.printStackTrace()
            }
        }
    }

    private fun isExternalStorageWritable(): Boolean {
        return Environment.getExternalStorageState() == Environment.MEDIA_MOUNTED
    }
}
```

---
**8. b) How we can use database programmatically?**

Android provides built-in support for SQLite databases, which can be used programmatically to store structured, private data within an application. The primary tool for this is the `SQLiteOpenHelper` class.

**Step 1: Create a `SQLiteOpenHelper` Subclass**
This helper class will manage the creation and versioning of your database. You must override two methods: `onCreate()` and `onUpgrade()`.

```kotlin
import android.content.Context
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper

class DatabaseHelper(context: Context) :
    SQLiteOpenHelper(context, DATABASE_NAME, null, DATABASE_VERSION) {

    companion object {
        private const val DATABASE_NAME = "MyCompany.db"
        private const val DATABASE_VERSION = 1
        const val TABLE_EMPLOYEES = "employees"
        const val COLUMN_ID = "_id"
        const val COLUMN_NAME = "name"
        const val COLUMN_DEPT = "department"
    }

    // Called when the database is created for the first time.
    override fun onCreate(db: SQLiteDatabase?) {
        val createTableQuery = """
            CREATE TABLE $TABLE_EMPLOYEES (
                $COLUMN_ID INTEGER PRIMARY KEY AUTOINCREMENT,
                $COLUMN_NAME TEXT,
                $COLUMN_DEPT TEXT
            )
        """.trimIndent()
        db?.execSQL(createTableQuery)
    }

    // Called when the database needs to be upgraded.
    override fun onUpgrade(db: SQLiteDatabase?, oldVersion: Int, newVersion: Int) {
        db?.execSQL("DROP TABLE IF EXISTS $TABLE_EMPLOYEES")
        onCreate(db)
    }
}
```

**Step 2: Get a Database Instance**
In your Activity or Repository, instantiate your `DatabaseHelper` class and get a writable or readable database instance.
* `getWritableDatabase()`: Gets a database for both reading and writing.
* `getReadableDatabase()`: Gets a database for reading only.

**Step 3: Perform CRUD Operations**
Use the methods of the `SQLiteDatabase` object to perform Create, Read, Update, and Delete operations.

* **Insert (Create):** Use the `insert()` method with a `ContentValues` object.
* **Query (Read):** Use the `query()` method. The result is returned in a `Cursor` object.
* **Update:** Use the `update()` method.
* **Delete:** Use the `delete()` method.

**Example Code (Inserting a record in an Activity):**
```kotlin
import android.content.ContentValues
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {
    private lateinit var dbHelper: DatabaseHelper

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // ...

        dbHelper = DatabaseHelper(this)
        addEmployee("John Doe", "Engineering")
    }

    private fun addEmployee(name: String, department: String) {
        // Get the database in write mode
        val db = dbHelper.writableDatabase

        // Create a new map of values, where column names are the keys
        val values = ContentValues().apply {
            put(DatabaseHelper.COLUMN_NAME, name)
            put(DatabaseHelper.COLUMN_DEPT, department)
        }

        // Insert the new row, returning the primary key value of the new row
        val newRowId = db.insert(DatabaseHelper.TABLE_EMPLOYEES, null, values)

        // You can close the db connection when you're done with it
        // db.close()
    }

    override fun onDestroy() {
        dbHelper.close() // Close the database connection
        super.onDestroy()
    }
}
```
---
**9. a) How can we use content providers? Write its relevant code.**

You don't access a `ContentProvider` directly. Instead, you use a **`ContentResolver`** object to communicate with the provider as a client. The `ContentResolver` acts as an intermediary, handling the communication and security.

The process to use a Content Provider involves these steps:

1.  **Get `ContentResolver`:** Obtain an instance of `ContentResolver` from your app's `Context`.
2.  **Define a `Content URI`:** Each Content Provider exposes a public `URI` (Uniform Resource Identifier) that uniquely identifies its dataset. For example, the built-in contacts provider uses URIs defined in the `ContactsContract` class.
3.  **Request Permissions:** Your app must request the necessary read/write permissions in `AndroidManifest.xml` to access the provider's data (e.g., `READ_CONTACTS`).
4.  **Perform Query:** Use the `ContentResolver.query()` method to retrieve data. This method returns a `Cursor` object.
5.  **Process the `Cursor`:** Iterate through the `Cursor` to read the data from each row.

**Relevant Code (Reading Contact Names):**

**1. Add Permission in `AndroidManifest.xml`:**
```xml
<manifest ...>
    <uses-permission android:name="android.permission.READ_CONTACTS" />
</manifest>
```
*Note: For Android 6.0+, you must also request this permission at runtime.*

**2. Kotlin Code to Query Contacts:**
```kotlin
import android.os.Bundle
import android.provider.ContactsContract
import android.util.Log
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // ...
        readContacts()
    }

    private fun readContacts() {
        // 1. Get ContentResolver
        val contentResolver = contentResolver

        // 2. Define the Content URI for contacts
        val uri = ContactsContract.CommonDataKinds.Phone.CONTENT_URI

        // 3. Define the projection (which columns to fetch)
        val projection = arrayOf(
            ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME,
            ContactsContract.CommonDataKinds.Phone.NUMBER
        )

        // 4. Perform the query
        val cursor = contentResolver.query(uri, projection, null, null, null)

        // 5. Process the Cursor
        cursor?.use { // 'use' will automatically close the cursor
            val nameIndex = it.getColumnIndex(ContactsContract.CommonDataKinds.Phone.DISPLAY_NAME)
            val numberIndex = it.getColumnIndex(ContactsContract.CommonDataKinds.Phone.NUMBER)

            while (it.moveToNext()) {
                val name = it.getString(nameIndex)
                val number = it.getString(numberIndex)
                Log.d("Contacts", "Name: $name, Number: $number")
            }
        }
    }
}
```

---
**9. b) Explain how we can create and use databases in android.**

Creating and using a local SQLite database in Android is a fundamental skill for storing structured data. The process can be broken down into three main parts: defining the database schema, creating a helper class to manage the database, and then using that helper to perform data operations.

**Step 1: Define the Database Schema with a Contract Class**
A best practice is to create a "Contract" class. This class acts as a container for constants that define the names of your tables, columns, and other database-related strings. This makes your code cleaner, less error-prone, and easier to modify.

```kotlin
// A Contract class defines constants for the DB schema
object FeedReaderContract {
    // Inner class that defines the table contents
    object FeedEntry : BaseColumns {
        const val TABLE_NAME = "entry"
        const val COLUMN_NAME_TITLE = "title"
        const val COLUMN_NAME_SUBTITLE = "subtitle"
    }
}
```

**Step 2: Create a Database Helper (`SQLiteOpenHelper`)**
This class is the core of your database implementation. It handles the creation of the database file and its tables, as well as managing version upgrades.

```kotlin
import android.content.Context
import android.database.sqlite.SQLiteDatabase
import android.database.sqlite.SQLiteOpenHelper
import android.provider.BaseColumns

class FeedReaderDbHelper(context: Context) :
    SQLiteOpenHelper(context, DATABASE_NAME, null, DATABASE_VERSION) {

    override fun onCreate(db: SQLiteDatabase) {
        // SQL statement to create the table, using constants from the Contract class
        val SQL_CREATE_ENTRIES =
            "CREATE TABLE ${FeedReaderContract.FeedEntry.TABLE_NAME} (" +
            "${BaseColumns._ID} INTEGER PRIMARY KEY," +
            "${FeedReaderContract.FeedEntry.COLUMN_NAME_TITLE} TEXT," +
            "${FeedReaderContract.FeedEntry.COLUMN_NAME_SUBTITLE} TEXT)"
        db.execSQL(SQL_CREATE_ENTRIES)
    }

    override fun onUpgrade(db: SQLiteDatabase, oldVersion: Int, newVersion: Int) {
        // This database is only a cache for online data, so its upgrade policy is
        // to simply to discard the data and start over
        val SQL_DELETE_ENTRIES = "DROP TABLE IF EXISTS ${FeedReaderContract.FeedEntry.TABLE_NAME}"
        db.execSQL(SQL_DELETE_ENTRIES)
        onCreate(db)
    }

    companion object {
        const val DATABASE_VERSION = 1
        const val DATABASE_NAME = "FeedReader.db"
    }
}
```

**Step 3: Use the Database in your Application**
In your Activity or another class, you can now instantiate the helper and use it to insert, read, update, or delete data.

**Example: Inserting and Reading Data**
```kotlin
import android.content.ContentValues
import android.os.Bundle
import androidx.appcompat.app.AppCompatActivity

class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        // ...

        // Instantiate the database helper
        val dbHelper = FeedReaderDbHelper(this)

        // --- INSERT DATA ---
        val db = dbHelper.writableDatabase // Get DB in write mode

        val values = ContentValues().apply {
            put(FeedReaderContract.FeedEntry.COLUMN_NAME_TITLE, "My First Title")
            put(FeedReaderContract.FeedEntry.COLUMN_NAME_SUBTITLE, "My First Subtitle")
        }
        db?.insert(FeedReaderContract.FeedEntry.TABLE_NAME, null, values)


        // --- READ DATA ---
        val readableDb = dbHelper.readableDatabase
        val cursor = readableDb.query(
            FeedReaderContract.FeedEntry.TABLE_NAME, // The table to query
            null, // The columns to return (null for all)
            null, // The columns for the WHERE clause
            null, // The values for the WHERE clause
            null, // don't group the rows
            null, // don't filter by row groups
            null  // The sort order
        )
        // Process the cursor...

        // Close the helper when your activity is destroyed to free up resources
        // dbHelper.close()
    }
}
```


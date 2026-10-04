Task 1: Flutter & Dart Environment Setup

C:\Users\admin\Desktop>flutter doctor
Doctor summary (to see all details, run flutter doctor -v):
[√] Flutter (Channel stable, 3.47.6, on Microsoft Windows [Version 10.0.26200.9457], locale en-US)
[√] Windows Version (Windows 11 or higher, 25H2, 2009)
[X] Android toolchain - develop for Android devices
    X Unable to locate Android SDK.
      Install Android Studio from: https://developer.android.com/studio/index.html
      On first launch it will assist you in installing the Android SDK components.
      (or visit https://flutter.dev/to/windows-android-setup for detailed instructions).
      If the Android SDK has been installed to a custom location, please use
      `flutter config --android-sdk` to update to that location.

[√] Chrome - develop for the web
[X] Visual Studio - develop Windows apps
    X Visual Studio not installed; this is necessary to develop Windows apps.
      Download at https://visualstudio.microsoft.com/downloads/.
      Please install the "Desktop development with C++" workload, including all of its default components
[√] Connected device (3 available)
[√] Network resources

! Doctor found issues in 2 categories.


In Flutter, Hot Reload and Hot Restart both let you see code changes quickly, but they preserve different amounts of your app's state.


🔥 Hot Reload
🔄 Hot Restart
What happens
Injects updated Dart code into the running app
Restarts the Dart app from scratch
App state
Preserved
Lost
Speed
Very fast
Slower
main() runs again?
No
Yes
Useful for
UI/layout changes
Changes involving app initialization or global state

Hot Reload
Hot Reload updates the running application without losing its current state.
For example, suppose you're editing:
Text(
  'Hello',
  style: TextStyle(fontSize: 20),
)
You change the font size to 30 and perform a hot reload. Flutter updates the widget tree while keeping things like the current navigation position, form inputs, and other state.
Use Hot Reload when:
Changing widget layouts or styling
Adjusting colors, padding, fonts, etc.
Modifying widget build methods
Iterating quickly on UI
Fixing many ordinary Dart-code bugs
It's usually your first choice during development.
Hot Restart
Hot Restart completely restarts the Flutter application's Dart execution.
That means things such as:
void main() {
  // initialization
  runApp(MyApp());
}
are executed again, and the application's in-memory state is reset.
For example, if you have:
int counter = 0;
and you've incremented it to 10, a hot restart will reset that state.
Use Hot Restart when:
Hot Reload doesn't reflect your changes correctly
You've changed initialization code in main()
You've changed global/static state
You've changed code that needs to run again from application startup
You want to reproduce the app's initial state
You've made changes involving certain stateful resources that hot reload can't safely update
Simple rule
Hot Reload = "Update my code, keep my app where it is."
Hot Restart = "Start my Flutter app over, using the new code."
For normal UI development, try Hot Reload first. If the change isn't taking effect because the relevant initialization/state wasn't recreated, use Hot Restart.
 Task 2: MySQL Database Management
mysql> CREATE DATABASE school;
Query OK, 1 row affected (0.02 sec)

mysql> USE school;
Database changed
mysql> CREATE TABLE students (
    ->     id INT AUTO_INCREMENT PRIMARY KEY,
    ->     name VARCHAR(100),
    ->     email VARCHAR(150) UNIQUE,
    ->     enrolled_on DATE
    -> );
Query OK, 0 rows affected (0.08 sec)


  
Query OK, 2 rows affected (0.01 sec)
Records: 2  Duplicates: 0  Warnings: 0

mysql>
mysql> -- Retrieve Records
mysql> SELECT * FROM students;
+----+---------------+-------------------+-------------+
| id | name          | email             | enrolled_on |
+----+---------------+-------------------+-------------+
|  1 | Alice Johnson | alice@example.com | 2026-01-15  |
|  2 | Bob Smith     | bob@example.com   | 2026-02-01  |
+----+---------------+-------------------+-------------+
2 rows in set (0.00 sec)

mysql>


Task 3: Python Environment & Dependency Isolation
# Python environment setup commands


Run these commands from the project folder in PowerShell. Each command below is followed by its purpose.


| Command | What it is used for |
| --- | --- |
| `py -m venv venv` | Creates an isolated Python virtual environment named `venv` in this folder. |
| `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` | Temporarily allows PowerShell scripts to run in the current PowerShell process so the environment can be activated. It does not change the machine-wide execution policy. |
| `.\venv\Scripts\Activate.ps1` | Activates the `venv` environment in PowerShell, so `python` and `pip` refer to the environment. |
| `python -m pip install requests` | Installs the `requests` library into the active virtual environment. |
| `python -m pip list` | Lists packages installed in the active environment; use it to verify that `requests` appears. |
| `python -m pip freeze > requirements.txt` | Exports the installed packages and exact versions to `requirements.txt`. |
| `.\venv\Scripts\python.exe -c "import requests, sys; print('Python:', sys.executable); print('requests:', requests.__version__)"` | Verifies directly that the environment's Python interpreter can import `requests`, and prints the interpreter path and installed version. |
| `.\venv\Scripts\python.exe -m pip list` | Lists the packages in `venv` explicitly, without relying on activation. |


## Commands in execution order


```powershell
py -m venv venv
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\venv\Scripts\Activate.ps1
python -m pip install requests
python -m pip list
python -m pip freeze > requirements.txt
.\venv\Scripts\python.exe -c "import requests, sys; print('Python:', sys.executable); print('requests:', requests.__version__)"
.\venv\Scripts\python.exe -m pip list
```


The first activation attempt, before setting the process-scoped execution policy, was blocked by PowerShell. After applying the temporary policy command, activation succeeded. The verified `requests` version was `2.34.2`.

Task 4: VS Code Workspace Configuration


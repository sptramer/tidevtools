tidevtools from Bill Dawson
============================

Includes a script to make a Titanium mobile project, and a script to "eclipsify" a project.

Suggested Steps To Use It
--------------------------

- Clone this repository.
- Copy tidevtools_settings.py.sample -> tidevtools_settings.py.
- Open tidevtools_settings.py and change the values -- I think they're self-explanatory.
- chmod +x *.py
- Make life easy on yourself and make some aliases.  I do this...

     alias mp="/Users/bill/projects/tidevtools/ti_makeproj.py"

     alias ec="/Users/bill/projects/tidevtools/ti_eclipsify.py"

     alias an="/Users/bill/projects/tidevtools/ti_android_device.py"

Usage Instructions
-------------------

### ti_builder.py

If you're sitting in the root directory of a Titanium project -- the directory containing tiapp.xml -- and you run this, it will build the Android apk for you.  If you pass `simulator` as an argument, it'll also install the app on a running emulator.  If you instead pass `install`, it will install on to an attached Android device.  If you don't pass anything as an argument, it just builds the project, producing the .apk file down in build/android/bin.

### ti_makeproj.py
Makes a Titanium mobile project, including making its entry in the Titanium Developer Sqlite DB (so you see it next time you open Developer).

set ANDROID_SDK environment variable!

Usage:

`ti_makeproj.py [Project name]`

Example:

`ti_makeproj.py MyProject`

That will create a MyProject folder in the folder you specify in the PROJECT_FOLDER variable in your tidevtools_settings.py.

### ti_eclipsify.py

**DEPRECATED** -- will not function correctly if you're Titanium SDK source in Eclipse is from 1.8.0 or higher.  Replaced by ti_eclipsify2.py.

Does what you expect.  Run it while you are sitting in the root of a project (where the tiapp.xml is.)

### ti_eclipsify2.py

**DEPRECATED** Does what you expect.  Run it while you are sitting in the root of a project (where the tiapp.xml is.)

### ti_eclipsify3.py

Does what you expect.  Run it while you are sitting in the root of a project (where the tiapp.xml is.)

### ti_android_device.py

If you're sitting in a Titanium project folder (a folder with tiapp.xml) and run this with no options, it checks to see if the project you're sitting in is installed on any connected Android devices.  If it is, it gives you options to uninstall from those devices.  Also, if it sees that build/android/bin/app.apk is there (i.e., you've built the project at leat once), it gives you options to install the APK on any of the connected devices.

Alternatively, you can run this script from anywhere with the "-u [package_filter]" option, such as:

`ti_android_device.py -u com.billdawson`

It will then check all your connected Android devices to see if they have any packages whose names begin with the filter you've provided.  If it finds any, it gives you the option to uninstall those matching packages from the device(s).  You can select one-by-one the ones you want to uninstall (and from which device.)

Alternatively, you can run this script from a Titanium project folder with the -i (--immediate) option, in which case no UI will be displayed and instead the app from your current directory will be uninstalled from all attached Android devices or emulators on which it is installed.

### ti_pull_request.sh

Automatically opens the URL for sending a pull request on github from the current branch. Makes some assumptions (see the script for more details)

Plumble
=======

Plumble is a robust GPLv3 Mumble client for Android that uses the [Jumble](https://github.com/Morlunk/Jumble) protocol implementation.


Use for Silent Classroom
------------------------

This code will modified due to the learning process needed to understand it. A higher level of usage on top of the original Plumble application will be build.



Building on GNU/Linux
---------------------

    1. Get Android studios archive
	
	--> https://developer.android.com/studio/?gclid=Cj0KCQjwpsLkBRDpARIsAKoYI8yed-jly_3d_67jJc5ZfWnmp2dkxOfweEgRz4rK2OutzwuMbzPDMawaArXiEALw_wcB

	2. extract to /usr/local
	
	3. cd android-studios/bin

	--> ./studio.sh

	4. Install all default parameters

	5. Go to tools --> SDK Manager

	--> install SDK platform lollipop (21)

	6. [NOT IN ANDROID STUDIOS] open terminal --> sudo apt install lib32stdc++6

	7. [NOT IN ANDROID STUDIOS] open terminal:

	--> mkdir project
	--> git init
	--> git remote add origin https://github.com/Soultoe/Plumble.git
	--> git pull origin master
	--> git submodule update --init --recursive

	8. in project folder open project/libraries/Jumble/build.gradle

	--> comment the function that begins by // Trigger NDK build on java compilation task.
	--> replace with: task ndkBuild(type: Exec) {
        commandLine '/home/[USERNAME]/Android/Sdk/ndk-bundle/ndk-build', '-C', file('src/main/jni/').absolutePath
    }
    externalNativeBuild {
        ndkBuild {
            path file('src/main/jni/Android.mk')
        }
    }

	9. Download NDK build 15c

	--> https://developer.android.com/ndk/downloads/older_releases.html

	10. Extract to /home/[username]/Android/Sdk/ndk-bundle
	
	--> You might have to mkdir ndk-bundle first
	--> Make sure the files are at the root of the folder, no intermediary folders

	11.  Go to file --> project structure --> NDK location : /home/[USERNAME]/Android/Sdk/ndk-bundle

	12. Go back to project root:
	--> ./gradlew assembleDebug

	13. The project should build successfully now!

	14. To run the emulator you may have to do the following
	chmod 777 /dev/kvm

Inter-process communication
---------------------------

Documentation on integrating your app with Plumble's IPC features [here](https://github.com/Morlunk/Plumble/wiki/Inter-process-communication).

Contributing
============

Coding
------

Standard FOSS project procedure applies; fork and submit a PR!

Please use Transifex for translations, not pull requests.

Testing
-------

[Help test the latest Plumble nightly builds here.](https://www.morlunk.com/jenkins/) File issue reports with Nightly version number.

Translation
-----------

Contribute translations to Plumble using [Transifex](https://www.transifex.com/projects/p/plumble/)!

Donate
------

Plumble is a lot of work to develop! All donations are appreciated, via the paid version on Google Play or here.

[Paypal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=ALTS7G56K2CGS)

[Bitcoin](bitcoin:1ySD4UzFDtPLq9agRg9eiFtWmz6DJ7bBf?label=Plumble%20Donations) (1ySD4UzFDtPLq9agRg9eiFtWmz6DJ7bBf)

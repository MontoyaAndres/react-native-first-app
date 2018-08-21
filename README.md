https://www.youtube.com/watch?v=mhoiwfShSnE&list=PLN3n1USn4xlmt7mOqxc3nl3RajpFxkDH8&index=3

# How to install React-Native (Ubuntu 18.*)

```
# First to all

sudo apt install openjdk-VERSION-jdk openjdk-VERSION-jre

sudo apt update

sudo apt install libtool m4 automake pkg-config libssl-dev adb python python3 python-dev python3-dev
```

Then, install android studio -> https://developer.android.com/studio/install#linux **(ONLY INSTALL THE IDE!)**

Then, install watchman:

```
git clone https://github.com/facebook/watchman.git
cd watchman
git checkout v4.9.0  # the latest stable release
./autogen.sh
./configure
make
sudo make install
```

Then, follow this tutorial:

https://facebook.github.io/react-native/docs/getting-started.html

Configure build path in your .bash_profile or .zshrc

### Emulate

Then, open your react-native project: https://www.youtube.com/watch?v=OZ5nCNOzflM

And create your first avd: https://facebook.github.io/react-native/docs/getting-started.html#preparing-the-android-device

To check is that exists, use:

```
# List your avds
emulator -list-avds

# Use the avd
emulator -avd NAME_AVD
```

More info (You couldn't emulate):

https://www.stkent.com/2017/08/10/update-your-path-for-the-new-android-emulator-location.html

### Slow

If your android-studio is slow, watch this video:

https://www.youtube.com/watch?v=4H0zI5Dga8U

And that's it!

If you already created a project, open it and run:

```
react-native run-android
```

If you're using a physic dispositive, you need to enable the reload option:

https://facebook.github.io/react-native/docs/debugging#accessing-the-in-app-developer-menu

Or you can enter:

```
adb shell input keyevent 82
```

And activate it!

# Possible errors

When you use your physic device, and it's running `react-native run-android` and it's very slow, so this is the solution:

First, you need to restart the adb config -> https://stackoverflow.com/a/47768793

And then, run again the new adb config:

```
adb reconnect

adb reverse tcp:8081 tcp:8081

killall node

# Check what ID you're using, in my case is "12d1".
lsusb

echo 'SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", MODE="0666", GROUP="plugdev"' | sudo tee /etc/udev/rules.d/51-android-usb.rules

#It'll show the adb-id of your device, in my case is "NSXDU17210009568"
adb devices

adb -s NSXDU17210009568 reverse tcp:8081 tcp:8081

#And all will run correctly
sudo react-native run-android
```


Possible variables errors: 

solution: http://www.techomoro.com/how-to-install-and-setup-react-native-on-ubuntu-17-10/

---

Metro Bundler can't listen on port 8081

solution: https://stackoverflow.com/a/49042658

---

your system lacks libtoolize

solution: https://github.com/facebook/watchman/issues/486

---
       
libtoolize:   error: One of these is required:
libtoolize:                 gm4 gnum4 m4
libtoolize:   error: Please install GNU M4, or 'export M4=/path/to/gnu/m4'.

solution: sudo apt install m4

---

./autogen.sh: line 16: aclocal: command not found

solution: sudo apt-get install automake

---

please install the pkg-config package for your system.

solution: sudo apt install pkg-config

---

fatal error: openssl/sha.h: No such file or directory

solution: sudo apt install libssl-dev

---

watchman-ContentHash.o: In function watchman::ContentHashCache::computeHashImmediate(char const*)

solution: After installing libssl-dev I did ./autogen ./configure again. make is now working without error.

---

fatal error: Python.h: No such file or directory

solution: sudo apt-get install python-dev python3-dev

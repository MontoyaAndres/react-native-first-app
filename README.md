https://www.youtube.com/watch?v=mhoiwfShSnE&list=PLN3n1USn4xlmt7mOqxc3nl3RajpFxkDH8&index=3

# How to install React-Native (Ubuntu 18.*)

sudo apt install openjdk-VERSION-jdk openjdk-VERSION-jre

sudo apt update

sudo apt install libtool m4 automake pkg-config libssl-dev adb python python3 python-dev python3-dev

Then, install android studio -> https://developer.android.com/studio/install#linux

Then, install watchman:

`
git clone https://github.com/facebook/watchman.git
cd watchman
git checkout v4.9.0  # the latest stable release
./autogen.sh
./configure
make
sudo make install
`

Then, follow this tutorial:

https://facebook.github.io/react-native/docs/getting-started.html

Configure build path in your .bash_profile or .zshrc

If your android-studio is slow, watch this video:

https://www.youtube.com/watch?v=4H0zI5Dga8U

### Emulate

To emulate, you need first to create a avd.

To compravate is that exists, use:

`
# List your avds
emulator -list-avds

# Use the avd
emulator -avd NAME_AVD
`

More info (You couldn't emulate):

https://www.stkent.com/2017/08/10/update-your-path-for-the-new-android-emulator-location.html

# Possible errors

Possible variables errors: 

http://www.techomoro.com/how-to-install-and-setup-react-native-on-ubuntu-17-10/

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

sudo apt-get install python-dev python3-dev

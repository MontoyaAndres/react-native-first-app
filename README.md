https://www.youtube.com/watch?v=mhoiwfShSnE&list=PLN3n1USn4xlmt7mOqxc3nl3RajpFxkDH8&index=3

# How to install React-Native (Ubuntu 18.*)

First to all install: sudo apt install libtool m4 automake pkg-config libssl-dev python python-dev python3-dev

**First:** https://www.youtube.com/watch?v=VvMYTQ_q-6o

**SECOND:** https://facebook.github.io/react-native/docs/getting-started.html

**THIRD (VARIABLES):** http://www.techomoro.com/how-to-install-and-setup-react-native-on-ubuntu-17-10/

Configure build path in your .bash_profile or .zshrc

# Possible errors

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

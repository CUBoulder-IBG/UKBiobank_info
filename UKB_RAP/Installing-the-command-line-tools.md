### Installing the command line tools on Mac OS X

In order to install the DNANexus command-line tools, you must have Python3 installed (this might already be installed by default).

Once you have Python3 installed, open a Terminal window and run the command `pip3 install dxpy`

The installer is likely to show you several warnings like "WARNING: The scripts dx, dx-app-wizard, dx-build-app and dx-build-applet are installed in '/Users/yourusername/Library/Python/3.9/bin' which is not on PATH." These warnings mean that in order to run these commands, you would need to type the full path, eg. to run dx you would type `/Users/yourusername/Library/Python/3.9/bin/dx`. This is annoying - to fix it, you need to add the directory to your PATH setting.

To add this directory to your path:
1. Check which shell you are using by running `env | grep SHELL`
2. If the result of step 1 says "/bin/zsh":
  * Edit (or create) the file ~/.zshrc, and add the following line to the bottom of the file:
        `export PATH="$PATH:/Users/yourusername/Library/Python/3.9/bin/"`
        (replace "yourusername" with your Mac OS username)
  * Run the command `source ~/.zshrc` to activate the change you made
3. If the result of step 1 says "/bin/bash", follow the instructions in step 2, but instead of using the file ~/.zshrc use either ~/.bash_profile (if you use MacOS's default Terminal.app), or ~/.bashrc (if you use almost any other terminal besides Terminal.app).

You may also get this warning message whenever you run a "dx" command:
> /Users/yourusername/Library/Python/3.9/lib/python/site-packages/urllib3/\__init__.py:34: NotOpenSSLWarning: urllib3 v2 only supports OpenSSL 1.1.1+, currently the 'ssl' module is compiled with 'LibreSSL 2.8.3'.

This message appears to be harmless (everything still works), but since it's annoying you can get rid of it by running `pip3 uninstall urllib3` and then `pip3 install urllib3==1.26.7`

### Installing the command line tools on Linux

FIXME: Add this

### Installing the command line tools on Windows

FIXME: Add this

Instructions for installing the command line tools are at the bottom of this document, after the instructions for using them.

### Useful documentation for the command line tools

Quickstart guide: https://documentation.dnanexus.com/getting-started/cli-quickstart<br/>
Full command reference: https://documentation.dnanexus.com/user/helpstrings-of-sdk-command-line-utilities<br/>
Type `dx help all` to see one-line summaries of all available dx commands, or `dx help commandname` to see more detailed documentation for a specific command.

### Signing in using the command line tools

To sign in, run the command `dx login`, and enter the same username and password you first created when registering your RAP/DNANexus account. You will not see any change in your command prompt (the way you would when you ssh to something) because you have not established a persistent connection to a remote system. The only thing that happens when you log in is that you have authenticated yourself, so now when you run other "dx" commands (from your local system) they will have permission to establish as-needed connections to RAP/DNANexus in order to carry out your commands.

When you log in, you will be shown a list of projects you have access to (if there are any), and it may automatically set one of them as your current project.

If you want to sign out when you are finished, you can run the command `dx logout`. If you are the only person who uses your computer, you can choose to stay authenticated for up to 30 days instead of logging out.

### Viewing and selecting projects with the command line tools

To see a list of projects you have "contribute" or higher access to, use the command `dx find projects`. To make one of those projects your current active project for other dx commands, use the command `dx select projectname` (where projectname is the name of your project). You can also use the command `dx select` with no other options to see a list of projects you have access to and be prompted to select one. If you only have access to one project, `dx select` will set that as your active project automatically.

You can also use the command `dx select --level VIEW` to see projects you have read-only access to, or `dx select --public` to see projects that are publicly available (such as reference datasets).

### Using the command line tools to manage data

Once you have selected a project as your current project, you can use "dx" with basic Linux commands (`dx ls` `dx cd` `dx mv` etc.) to manage files within your project.

To copy data between two projects you have access to, you can include the name of the non-active project in the path given to the `dx cp` command, adding a `:` before the `/` to indicate that you are referring to another project (and not a directory with that name within your project).<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;For example: `dx cp "Apollo Reference Data - AWS UKB RAP (London):/gnomAD Annotation Data/" gnomad`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;would copy gnomAD annotation data from the public project "Apollo Reference Data - AWS UKB RAP (London)"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;to a directory called "gnomad" in your current active project.<br/>
**Note:** You can only do this between two projects in the same AWS region. For UKB RAP, this means you can only copy data to/from other projects with region (London). All UKB RAP projects have region (London), even though they do not say (London) in their name.

To copy a small amount of data from your local system to your current active project, you can use the `dx upload` command. To copy a larger amount of data, you will need to install and use the Upload Agent. (Details for the Upload Agent: https://documentation.dnanexus.com/user/objects/uploading-and-downloading-files/batch/upload-agent )

To copy data from your current active project to your local system, you can use the `dx download` command. **Please do not attempt to download individual-level data about UKB participants, this is not allowed.**

### Using the command line tools to manage projects
FIXME: Add this

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
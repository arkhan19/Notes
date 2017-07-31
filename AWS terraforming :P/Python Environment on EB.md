##### To start with AWS and Web Development using Python you need Elastic Beanstalk on AWS.

Install the Elastic Beanstalk Command Line Interface (EB CLI)

The Elastic Beanstalk Command Line Interface (EB CLI) is a command line client that you can use to create, configure, and manage Elastic Beanstalk environments. The EB CLI is developed in Python and requires Python version 2.7, version 3.4, or newer.

Note
Amazon Linux comes with Python 2.7 and pip starting with version 2015.03.
The primary distribution method for the EB CLI on Linux, Windows, and macOS is pip, a package manager for Python that provides an easy way to install, upgrade, and remove Python packages and their dependencies. For macOS, you can also get the latest version of the EB CLI with Homebrew.

If you already have pip and a supported version of Python, you can install the EB CLI with the following command:

```
$ pip install --upgrade --user awsebcli
```

The --upgrade option tells pip to upgrade any requirements that are already installed. The --user option tells pip to install the program to a subdirectory of your user directory to avoid modifying libraries used by your operating sytem.

Note
If you encounter issues when you attempt to install the EB CLI with pip, you can install the EB CLI in a virtual environment to isolate the tool and its dependencies, or use a different version of Python than you normally do.
After you install the EB CLI, add the path to the executable file to your PATH variable:

```
Linux – ~/.local/bin
```

```
macOS – ~/Library/Python/3.4/bin
```


To modify your PATH variable (Linux, macOS, or Unix)

1. Find your shell's profile script in your user folder. If you are not sure which shell you have, run echo $SHELL.

```
$ ls -a ~
.  ..  .bash_logout  .bash_profile  .bashrc  Desktop  Documents  Downloads
```

 Bash – .bash_profile, .profile, or .bash_login.
 Zsh – .zshrc
 Tcsh – .tcshrc, .cshrc or .login.

2. Add an export command to your profile script. The following example adds the path represented by LOCAL_PATH to the current PATH variable.
```
export PATH=LOCAL_PATH:$PATH
```

3. Load the profile script described in the first step into your current session. The following example loads the profile script represented by PROFILE_SCRIPT into your current session.

```
$ source ~/PROFILE_SCRIPT
```


```
$ eb --version
```

EB CLI 3.7.8 (Python 3.4.3)
The EB CLI is updated regularly to add functionality that supports the latest Elastic Beanstalk features. To update to the latest version of the EB CLI, run the installation command again.

```
$ pip install --upgrade --user awsebcli
```

If you need to uninstall the EB CLI, use pip uninstall.

```
$ pip uninstall awsebcli
```



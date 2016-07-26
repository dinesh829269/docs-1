## Package Managers

> A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner.
-- [Wikipedia](https://en.wikipedia.org/wiki/Package_manager)

Package managers are extremely useful tools for installing software. They often come with major software packages (think Python, Ruby, JavaScript, an operating system).

Package managers make modularity possible on a large scale. Developers share their open source code by publishing it as a package. Other developers (like we do, at MiddCourses) download that code through the relevant package manager and include it in our own code.

Package managers mean time spent rewriting existing, tested code and more modularity (a major :key: in good software development).

## [Homebrew](http://brew.sh/)

Homebrew bills itself as "The missing package manager for OS X". OS X doesn't come with a package manager, so many developers use Homebrew to install useful packages.

Install Homebrew using the command on their website. You can then use Homebrew to install some of the bigger pieces of software, like Python.

Follow the [Python Guide](http://docs.python-guide.org/en/latest/starting/installation/) to install Python.

> But I already have Python on my Mac?

Yes, there is a version of Python in `/usr/bin/python`. However, it might be outdated depending on your operating system, and it will become outdated when a new version of Python is released. With Homebrew you can install both Python 2 and Python 3 side by side (`brew install python` and `brew install python3`, respectively) and easily update them to stay up to date with the current version of Python.

### Changing `PATH` to use Homebrew by default

*The following is some knowledge that will help you set up Homebrew (in the context of Python).*

There are a lot of packages that come with OS X that you'll want to install with Homebrew. Anytime you need a specific version this is the way to go.

Once you install with Homebrew, you almost always want to use the Homebrew version over the version that comes with OS X (that's why you installed it, right?). To make sure this happens, you need to change your `PATH`, a special variable in your terminal that tells the terminal where to find programs to run. You can see your `PATH` by running `echo $PATH` from the command line. Programs are run based on the first location in the `PATH` that contains the program with the matching name. So if there are two Pythons (OS X and Homebrew), the first location in the `PATH` that contains a Python will match, and that Python will be run.

**Protip**: Run `which python` to see the location of the Python that will match and run when you run `python`. You can replace "python" here with the name of any program.

Try running `which python` before changing anything `PATH`-related. You'll likely see `/usr/bin/python` if you haven't already changed anything. This is a problem. Homebrew executables (the things you run) are in `/usr/local/bin`. We need the Homebrew location to match first. We need to change the `PATH` variable.

There are two ways to change your path. Both are detailed in the answers to this [StackOverflow question](http://stackoverflow.com/questions/10343834).

 - [Change `/etc/paths`](http://stackoverflow.com/a/10343891/2044612)
 - [Change `PATH` in `.bashrc`](http://stackoverflow.com/a/11076829/2044612)

You need to restart your terminal (just open a new window or tab) for changes in the environment (like changing `PATH`) to take effect.

### I still don't get the right Python...

Run `brew doctor` to get a list of issues that might exist with your Homebrew setup. This is always a good idea when you have issues with Homebrew. It probably has the fix.
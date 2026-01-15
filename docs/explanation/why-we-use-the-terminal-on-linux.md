(why-we-use-the-terminal-on-linux)=
# Why we use the terminal on Linux

The history of the Linux command line dates back to the 1970s. We still use this interface today in a much updated form.

During the formative years of the computer industry, one of the early operating systems was called Unix. It was designed to run as a multi-user system on mainframe computers, with users connecting to it remotely via individual **terminals**. These terminals were pretty basic by modern standards: just a keyboard and screen, with no power to run programs locally. Instead they would just send keystrokes to the server and display any data they received on the screen. There was no mouse, no fancy graphics, not even any choice of color. Everything was sent as text, and received as text. Obviously, therefore, any programs that ran on the mainframe had to produce text as an output and accept text as an input.

Compared with graphics, text is very light on resources. Even on machines from the 1970s, running hundreds of terminals across glacially slow network connections (by today's standards), users were still able to interact with programs quickly and efficiently. The commands were also kept very terse to reduce the number of keystrokes needed, speeding up people's use of the terminal even more. This speed and efficiency is one reason why this text interface is still widely used today.

When logged into a Unix mainframe via a terminal users still had to manage the sort of file management tasks that you might now perform with a mouse and a couple of windows. Whether creating files, renaming them, putting them into subdirectories or moving them around on disk, users in the 70s could do everything entirely with a textual interface.

Each of these tasks required its own program or command: one to change directories (`cd`), another to list their contents (`ls`), a third to rename or move files (`mv`), and so on. In order to coordinate the execution of each of these programs, the user would connect to one single master program that could then be used to launch any of the others. By wrapping the user's commands this "shell" program, as it was known, could provide common capabilities to any of them, such as the ability to pass data from one command straight into another, or to use special wildcard characters to work with lots of similarly named files at once.

Users could even write simple code (called "shell scripts") which could be used to automate long series of shell commands in order to make complex tasks easier. Shell scripts are still widely used today, and they even form the basis of modern tools like continuous integration and continuous delivery (CI/CD) in the cloud.

The original Unix shell program was just called `sh`, but it has been extended and superseded over the years, so on a modern Linux system you're most likely to be using a shell called `bash`.

Linux is a sort-of-descendant of Unix. The core part of Linux is designed to behave similarly to a Unix system, such that most of the old shells and other text-based programs run on it quite happily. In theory you could even hook up one of those old 1970s terminals to a modern Linux box, and access the shell through that. But these days it's far more common to use a software terminal: that same old Unix-style text interface, but running in a window alongside your graphical programs.

When you open the terminal, you get access to running commands on your own machine. But just as easily, you could instruct the shell to connect to a remote system on another continent, to a virtual machine or a container, and run the same familiar commands there. Thanks to this speed and flexibility, the terminal interface is still useful many decades after its invention.

To learn how to use the terminal, go to {ref}`the-linux-command-line-for-beginners`.

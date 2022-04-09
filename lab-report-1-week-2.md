# Week 2 Lab Report
This report covers how to log into a course-specific account on `ieng6`.

Step 1: Install Visual Studio Code
---
Visual Studio Code is an Integrated Development Environment (IDE) that is used to maximize programmer efficiency thanks to featureslike syntax highlighting, autocomplete, support for multiple languages, debugging, and more.

First go to https://code.visualstudio.com/download and download VSCode for your operating system. You should see the page below. Because I am on MacOS, the rest of the steps in this guide will pertain to the MacOS operating system.

![screenshot 1](lab1-screenshots/lab1-screenshot1.png)

Once you have it downloaded, open VSCode. It should look like the screenshot below.

![screenshot 2](lab1-screenshots/lab1-screenshot2.png)

Step 2: Remotely Connecting
---
In order to connect to a remote computer over the internet, you must first open a terminal by clicking 'Ctrl + \`' (or by clicking 'Terminal' > 'New Terminal' in the menu bar). Next, use the following ssh command to connect to the remote computer: 

`ssh cs15lsp22zz@ieng6.ucsd.edu` 

IMPORTANT: replace zz with the letters associated with your account. SSH stands for Secure Socket Shell and is a protocol which allows you to connect securely to a remote computer or server. After running the command, you should see the following: 

![screenshot 3](lab1-screenshots/lab1-screenshot3.png)

Step 3: Try out some commands
---
Below are some examples of commands you can try.

![screenshot 4](lab1-screenshots/lab1-screenshot4.png)
In the example above I created a new directory called test_directory using the `mkdir` command. Then I navigated to the directory using the `cd` command. Then I navigated back to the parent directory using the `cd ..` command. Next I deleted the directory using the `rmdir` command.

![screenshot 5](lab1-screenshots/lab1-screenshot5.png)
In this example, I used the command `ls` to list the files in my current directory. Then I used the `rm` command to remove the files.

![screenshot 6](lab1-screenshots/lab1-screenshot6.png)
In this example I created a text file called hello.txt using the `cat` command, and I appended some text to it. Then I ran the command `cat hello.txt` to print the contents of the file.

![screenshot 7](lab1-screenshots/lab1-screenshot7.png)
In the example above, I created three new text files using the `touch` command. Then I once again used the `ls` command to see the files in my current directory, which displayed the new files I created. Then I used the `rm` command followed by the names of the three files to delete them all in one line.

Step 4: Moving files with `SCP`
---
An important part of working through a remote computer is being able to securely copy files back and forth between your local computer and the remote host. You can do this using the `scp` command, which stands for secure copy. To securely copy a file from the client (your local computer) to the remote computer, use the following command:

`scp fileName.java cs15lsp22zz@ieng6.ucsd.edu:~/`

Below is an example of creating a file called WhereAmI.java on my local computer, securely copying it to the remote computer, and then running it on the remote computer. As expected, running the file gives a different output depending on where it is being ran from.
![screenshot 8](lab1-screenshots/lab1-screenshot8.png)

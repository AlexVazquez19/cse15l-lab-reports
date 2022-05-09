# Lab Report 3
This report outlines the three additional group choice tasks from Lab 5.

Streamlining `ssh` Configuration
---
When logging into the remote server, I normally have to type `ssh cs15lsp22atv@ieng6.ucsd.edu`. This is a lot to type and can use up a lot of time if I need to frequently reconnect to the server. This is where streamlining the `ssh` configurations comes in handy to save time and make it so you don't have to memorize as much.

The first step is to navigate to the .ssh directory and create a config file. I navigated to the .ssh directory using the `cd .ssh` command and created a config file using the `touch config` command.

![screenshot 1](LR3-screenshots/LR3-screenshot1.1.png)

After creating the file, I opened it using the `open config` command. This opened the file in a new window for me to edit, as seen below. I edited the file to include the host name and my user ID.

![screenshot 2](LR3-screenshots/LR3-screenshot2.png)

After saving the file, I then connected to the remote server by typing `ssh ieng6`. This is much shorter than what I previosuly had to type. If I wanted to, I could go back to the config file and change `ieng6` to whatever name I want, as it's basically just a nickname for the host and user given below it.

![screenshot 3](LR3-screenshots/LR3-screenshot3.1.png)

Setting up GitHub access from `ieng6`
---
To enable pushing to origin from the command line in a cloned repository on my local computer, we need to add an SSH key to GitHub. Below is a screenshot of the public key that I added to my GitHub account.

![screenshot 4](LR3-screenshots/LR3-screenshot4.png)

Here is a screenshot of the private key on my local computer (stores in my .ssh directory). If I run the command `open id_rsa`, it opens the file as a text file and allows me to see the private key.

![screenshot 5](LR3-screenshots/LR3-screenshot5.png)

After adding the public key to my GitHub account, I went back to VScode and made a small edit to my local copy of MarkdownParse.java. Then I added it to the staging area using the command `git add MarkdownParse.java`, committed it using the command `git commit -m "adding a line"`, and finally pushed it to origin using the command `git push origin main`.

![screenshot 6](LR3-screenshots/LR3-screenshot6.png)

As seen by the [commit linked here](https://github.com/AlexVazquez19/markdown-parser/commit/8485a19950bc4e5b8119113940038765712f1c5f) (same as in the screenshot below), the commit worked properly and was pushed to the main repository on my GitHub account.

![screenshot 7](LR3-screenshots/LR3-screenshot7.png)

Copying Whole Directories with `scp -r`
---
In order to save time copying an entire directory to a remote server, we can use the `scp -r` command to copy all files within a directory (including any sub-directories). The `r` indicates that it will recursively copy files into the indicated server until there are no more left to copy from within the directory. This prevents us from having to copy over every file individually using just `scp`, which would be very inefficient.

Below is a screenshot of me running the command `scp -r . cs15lsp22atv@ieng6.ucsd.edu:~/markdown-parse` to copy my directory markdown-parse into the remote server.

![screenshot 8](LR3-screenshots/LR3-screenshot8.png)

To verify that it was copied successfully, I logged into the remote server using the command `ssh ieng6`. Then I used `ls` to see the files/folders in my current directory, and markdown-parser was there as expected (circled in red in the screenshot below). Then I compiled and ran MarkdownParse.java.

![screenshot 9](LR3-screenshots/LR3-screenshot9.png)

Lastly, using the command below I was able to copy the directory, login to the remote server, and compile and run MarkdownParse.java all in one line.

`scp -r . ieng6:~/markdown-parse; ssh ieng6 "cd markdown-parse; javac MarkdownParse.java; java MarkdownParse test-file.md"`

To break down this command:
* `scp -r . ieng6:~/markdown-parse;` copies the directory to the remote server
* `ssh ieng6` connects me to the remote server
* `"cd markdown-parse; javac MarkdownParse.java; java MarkdownParse test-file.md"` runs the three commands within the quotation marks on the remote server

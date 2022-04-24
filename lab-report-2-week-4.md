# Lab Report 1
This report covers three code changes from lab 3 that fixed bugs in the original code.

Change 1
---
The first bug that I encountered was that MarkdownParse.java would incorrectly return image links in the output list. Below is the test file that contains an image, which leads to the incorrect output. [Here is the link to the failure inducing input file.](https://github.com/AlexVazquez19/markdown-parser/blob/main/test-file.md)

![screenshot 1](LR2-screenshots/LR2-screenshot1.png)

Because the original code only identifies URLs by finding a set of brackets and parenthesis, it will also capture image links since images also use brackets and parenthesis. The resulting output is shown below. As you can see, the list includes the link to the image 'this_is_an_image.png'.

![screenshot 2](LR2-screenshots/LR2-screenshot2.png)

In order to fix this bug, I made it so that the code would check if there was an exclamation mark before the first bracket before the link was added to the returned list. As you can see in the diff screenshot below, I added a new integer variable called 'exclamationPoint' to get the index of the first exclamation point from currentIndex. Then I added an if statement that checks if the exclamation point index is right before the index for the first bracket. If it is, the link is for an image and is therefore not added to the final list to be returned.

![screenshot 3](LR2-screenshots/LR2-screenshot3.png)

**Relationship between bug, symptom, and failure inducing input**

In this case, the bug was that the code would incorrectly capture image links and return them in the final output. The symptom was that the image links would be returned in the list and could be visibly seen by the user. The failure inducing input was any markdown file that conatained an image.


Change 2
---

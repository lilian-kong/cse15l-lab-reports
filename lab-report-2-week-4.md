# Week 4 Lab Report
## Code Change 1
![image1](https://cdn.discordapp.com/attachments/808427673960972298/967996973670105098/Screen_Shot_2022-04-24_at_8.54.19_PM.png)
These are the changes I made to the code.

The test file that prompted me to make this change is [new-test](https://github.com/lilian-kong/markdown-parser/blob/main/new-test.md).

The symptom of the failure-inducing input was the error message ![image2](https://cdn.discordapp.com/attachments/808427673960972298/967988155552792656/Screen_Shot_2022-04-24_at_8.19.12_PM.png)
The correct output should be just the list of the 2 original, valid links (without an error message). 

The bug in the original codes is that it didn't have a mechanism that would exit the loop if there weren't anymore brackets or paratheses (so when it would index into the string using the indexes obtained it would result in an index out of bounds error). 
Because the input had an unpaired bracket, after assigning openBracket to the index of the open bracket, it would assign closeBracket to -1 (because there are no more in the string), same to openParen and closeParen. 
Because there was no mechanism to catch the situation (missing brackets or parantheses) -- bug, the file provided would cause the resultant error. 

## Code Change 2
![image1](https://cdn.discordapp.com/attachments/808427673960972298/967970243785932871/Screen_Shot_2022-04-24_at_7.08.07_PM.png)
These are the changes I made to the code.

The test file that prompted me to make this change is [test-file6](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-file6.md)

The symptom of the failure-inducing input was the output 
`[page.com]`
The correct output should have been an empty list, because images are not the same thing as links.

The bug in the original code is that there isn't a mechanism to detect the difference between a link and an image. As a result, the input file with an image was registered as a link by the code (because an image has the same format as a link but there is an exclamation point infront). 
The symptom in this case would be the addition of the image to the output list when it shouldn't be there.

## Code Change 3
![image1](https://cdn.discordapp.com/attachments/808427673960972298/967961564177129472/Screen_Shot_2022-04-24_at_6.33.37_PM.png)
These are the changes I made to the code.

The test file that prompted me to make this change is [test-file8](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-file8.md).

The symptom of the failure-inducing input was the output
`[a link on the first line]`
Based on the original Markdown file, the input given should not have resulted in a valid link, and therefore the output should have been an empty list.

The bug in the previous version of the code is that it didn't require anything in the brackets when checking the "template" for a valid link. As a result, test-file8 being run through the program resulted in the symptom of something being counted as a link when it really wasn't. 
Because the input `[](a link on the first line) [` originally passed the requirements (as there wasn't a statement screening whether or not there was actually valid text within the brackets or the parantheses -- bug), as a result when the code was run, it included "a link on the first line" as a valid link in the output -- symptom.

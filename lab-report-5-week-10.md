# Lab Report 5 Week 10
I found the tests with different results when using vimdiff on the results of running a bash for loop.

## Test 342
[This is the link to the test file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/342.md?plain=1)

With the lab 9 implementation of the markdownparser, this is the output: 

![image](https://cdn.discordapp.com/attachments/808427673960972298/982996549112041502/Screen_Shot_2022-06-05_at_5.36.09_AM.png)

With my implementation of the markdownparser, this is the output: 

![image](https://cdn.discordapp.com/attachments/808427673960972298/982996692238467113/Screen_Shot_2022-06-05_at_6.17.47_AM.png)

The correct one based on the CommonMark demo site is mine

![image](https://cdn.discordapp.com/attachments/808427673960972298/983001397077352458/Screen_Shot_2022-06-05_at_6.36.30_AM.png)
The expected output based on this should be `[]`

The issue with the lab 9 is that they don't have any sort of catch for if there's an inline comment within the formatting for a link. Something they could do is add another index counter for the most recent "\`" character. 
It could maybe be placed in this part of the code
![image](https://cdn.discordapp.com/attachments/808427673960972298/983011287539785758/Screen_Shot_2022-06-05_at_7.15.46_AM.png)

though it would also need two counters. There should be one for the first character and one for the second. If any part of the text (including the start parantheses or the end bracket) is included within the text contained in the inline code formatting, then that "chunk" should be skipped. That instance wouldn't be a valid link and the code should continue in the whileloop after updating currentIndex to the second "\`" character.

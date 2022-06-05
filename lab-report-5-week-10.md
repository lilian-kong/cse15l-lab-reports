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

though it would also need two counters. There should be one for the first character and one for the second. If any part of the text (including the start parantheses or the end bracket) is included within the text contained in the inline code formatting, then that "chunk" should be skipped. That instance wouldn't be a valid link and the code should continue in the whileloop after updating currentIndex to the second "\`" character. The issue is that this implementation doesn't currently have a catch for this kind of situation.

## Test 500
[This is the link to the test file](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/500.md)

With the lab 9 implementation of the markdownparser, this is the output: 

![image](https://cdn.discordapp.com/attachments/808427673960972298/983055783531008070/Screen_Shot_2022-06-05_at_10.12.39_AM.png)

My implementation doesn't have anything that checks for special characters or anything of the sort. It might be something with how the substring is extracted but my implementation doesn't look different from the one from lab 9 either so I'm still not sure.

With my implementation of the markdownparser, this is the output: 

![image](https://cdn.discordapp.com/attachments/808427673960972298/983055862727856208/Screen_Shot_2022-06-05_at_10.12.54_AM.png)

The correct one based on the CommonMark demo site is the implementation from lab 9

![image](https://cdn.discordapp.com/attachments/808427673960972298/983055712630505512/Screen_Shot_2022-06-05_at_10.12.19_AM.png)
The expected output based on this should be `[#fragment, http://example.com#fragment, http://example.com?foo=3#frag]`

I'm honestly not exactly sure what the problem is. Based on this test as well as others I looked at, my implementation of the markdownparser breaks when there is some sort of special character, whether its `#` in this case or `<` in others, that starts the potential link. This doesn't really make sense to me because based on my code there isn't anything that should stop that from being added as a valid link.
![image](https://cdn.discordapp.com/attachments/808427673960972298/983053710018117693/Screen_Shot_2022-06-05_at_10.04.19_AM.png)

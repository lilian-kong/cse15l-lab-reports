# Lab Report 4 Week 8
[My markdownparser repository](https://github.com/lilian-kong/markdown-parser)

[Week 7 repository]()
## Snippet 1
![image](https://cdn.discordapp.com/attachments/808427673960972298/977369153180696587/unknown.png)

Based on the output from the CommonMark demo site, the output should be 
```
["another link`"]
```
![image](https://cdn.discordapp.com/attachments/808427673960972298/977370932286988338/unknown.png)


This is the JUnit test I wrote (for both implementations) to test for Snippet 1. 
- for my implementation, the test failed ![image](https://cdn.discordapp.com/attachments/808427673960972298/977372878301442078/unknown.png)
- for their implementation, the test failed ![image](https://cdn.discordapp.com/attachments/808427673960972298/977373624270983188/unknown.png)

To fix this bug, I would have to add code that would check for a set of backticks (two variables for the indexes of backticks -- one for the first, and one for the second). Given that there are two backticks found, if the second backtick is not before the opening bracket or the first backtick after the closing parenthesis (in other words if some amount of the link formatting is within the inline text format), the link won't be valid, and as a result the code should update currentIndex to after the second backtick and continue. Otherwise, if there is only a first backtick or none at all, the code should run normally and count it as a valid link (if everything else checks out). There should also be some sort of catch for finding paired backticks (as theroretically there could be more than one pair of backticks detected before the potential link, so the code should have some sort of way of finding the most recent "open" backtick, maybe implemented in a similar way to how the week 8 implementation finds the close parentheses.
## Snippet 2
![image](https://cdn.discordapp.com/attachments/808427673960972298/977379509105991720/unknown.png)

Based on the output from the CommonMark demo site, the output should be
```
["nested link", "a nested parenthesized url", "some escaped [ brackets ]"]
```
![image](https://cdn.discordapp.com/attachments/808427673960972298/977381651350966312/unknown.png)

This is the JUnit test I wrote (for both implementations) to test for Snippet 1. 
- for my implementation, the test failed ![image](https://cdn.discordapp.com/attachments/808427673960972298/977381977634254869/unknown.png)
- for their implementation, the test failed ![image](https://cdn.discordapp.com/attachments/808427673960972298/977382198598574090/unknown.png)

To fix this bug, I would have to add code that kept track of how many paired brackets and parentheses have been counted, and only return what is in the final paired set. The implementation from week 8 would be helpful to look at and apply to each individual case. For nest brackets, the potential link would start at the first paired set of brackets, and if that one isn't valid, move back to a previous one. This might be able to be done with an ArrayList of potential opening brackets and a loop that iterates starting from the end that breaks when it finds a valid one. The nested parentheses is solved with the implementation given in the week 8 lab. Escaped brackets can be caught with something that checks if the character immediately preceding the open or closed bracket is a backslash, and if so invalidate it as a potential open bracket (put an in statement that only allows the index of openBracket or closeBracket to be changed if the previous character is not backslash).
## Snippet 3

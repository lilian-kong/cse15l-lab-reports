# Week 2 Lab Report
## Installing VSCode
First step is to download [VSCode](https://code.visualstudio.com/). When you launch it should look something like ![vscode open](https://cdn.discordapp.com/attachments/808427673960972298/962682780230254623/Screen_Shot_2022-03-31_at_4.19.19_PM.png)

## Remotely Connecting
The next step is actually accessing the remote server. First, open a terminal in VSCode (Ctrl + `), then type your course specific account. For example, mine would be
```
$ ssh cs15lsp22ate@ieng6.ucsd.edu
```
If it is your first time connecting to the server, it will ask you whether or not you want to continue connecting. Select yes, and then input your password when prompted. Note that the password will not show up in the terminal while you are typing, but if typed correctly, after hitting enter, it should greet you with something like ![remote connect](https://cdn.discordapp.com/attachments/808427673960972298/962682975030505522/Screen_Shot_2022-04-10_at_4.49.59_AM.png)

## Trying Some Commands
Some useful commands to try out (both on your your computer and the remote server) are:
- `cd ~`
- `cd`
- `ls -lat`
- `ls -a`
- `mkdir`
- `pwd`
- `cp`

![commands](https://cdn.discordapp.com/attachments/808427673960972298/962683137429749800/Screen_Shot_2022-03-31_at_4.51.32_PM.png)
You can use Ctrl D or the command `exit` to log out of the remote server in your terminal.

## Moving Files with `scp`
One way to copy files from your computer to a remote coputer is by using the `scp` command. This command is always run from the client (your computer, not the server). The file `WhereAmI.java` helps us check that `scp` is working properly and copying the files.
```
class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
    }
}
```
Then run the command `scp WhereAmI.java cs15lsp22ate@ieng6.ucsd.edu` but with your specific username.
![scp](https://cdn.discordapp.com/attachments/808427673960972298/962698214644011118/Screen_Shot_2022-03-31_at_5.05.59_PM.png)
you will be prompted to give a password like when logging in. 

After logging into your remote server using `ssh`, use the `ls` command, you should see the copied file in the directory. You can then run the file on the server computer using `javac` and `java`
![scp run](https://cdn.discordapp.com/attachments/808427673960972298/962698254397636638/Screen_Shot_2022-03-31_at_5.35.04_PM.png)

## Setting an SSH Key
Because typing the password each time you want to access the remote server with `ssh` and `scp` is annoying and time consuming, we are going to use `ssh-keygen` to speed it up. Enter the following command on your client (local).
```
$ ssh-keygen

Generating public/private rsa key pair.

Enter file in which to save the key
(/Users/<user-name>/.ssh/id_rsa): /Users/<user-name>/.ssh/id_rsa

Enter passphrase (empty for no passphrase):

Enter same passphrase again:
```
It should then save your identification (`id_rsa`) and publ~ic key (`id_rsa.pub`) in the `.ssh` directory of your computer. We then need to copy the public key into the `.ssh` directory of the remote server.

First you need to go to the remote server and create a `.ssh` directory. 
```
$ ssh cs15lsp22ate@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ exit
```
Then, now that we are back on the client, we copy the key into the remote server:
```
$ scp /Users/<liliankong>/.ssh/id_rsa.pub
cs15lsp22ate@ieng6.ucsd.edu:~/.ssh/authorized_keys
```
using your own respective username and file path.

Then you should be able to access the remote server without having to enter your password each time.
![ssh key](https://cdn.discordapp.com/attachments/808427673960972298/962882573086908436/Screen_Shot_2022-04-10_at_6.11.31_PM.png)
note that there is no longer a prompt to enter a password 

## Optimizing Remote Running
To make accessing and leaving the remote servers more efficient, there are some tricks you can use.
- after a `ssh` command, you can write another command in quotes to run it on the remote server before exiting
- you can also run multiple commands in a single line by separating them with semicolons
![tricks](https://cdn.discordapp.com/attachments/808427673960972298/962886657546276864/Screen_Shot_2022-04-10_at_6.27.43_PM.png)
By combining these two tips, you can copy a local file into the remote server and compile/run it there in only one line rather in four
![efficient](https://cdn.discordapp.com/attachments/808427673960972298/962889522708906014/Screen_Shot_2022-04-10_at_6.38.56_PM.png)
# Lab Report 1

## Installing VScode
- First, I went to the [VSCode](https://code.visualstudio.com/) website
- As shown in the image, I clicked the "Download for Windows" button (the dropdown menu shows more options for other operating systems)

![VS Code Website](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/download-vscode.png?raw=true)
- I then followed the on-screen instructions to complete the installation.

## Remotely Connecting
- First, I had to find my course specific account name [here](https://sdacs.ucsd.edu/~icc/index.php)
- Then I clicked on "change your password" and followed the on-screen instructions. If you don't want to change your MyTritonLink password, you can, but I changed everything
- We also have to install [OpenSSH](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse), which I already have installed

![PowerShell OpenSSH](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/download-openssh.png?raw=true)
- Now we are ready to remotely connect using VSCode
- Open a terminal in VSCode and type `ssh cs15lwi22ahx@ieng6.ucsd.edu`, replacing the `ahx` with your own account information
- Type your new password, and the following screen should appear

![Remote Connection](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/remote-connection.png?raw=true)
- I have already set a key, so I did not have to type a password in

## Trying Some Commands

![Commands](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/commands.png?raw=true)
- Let's run through the commands seen above
- `cd ~` and `cd` both bring me to the home directory, in this case I was already in the home directory
- `ls -lat` lists all files and directories in the current directory, in this case it was the home directory. `ls -l` provides a long listing with various information on the files, `ls -a` shows all files, including hidden ones, and `ls -t` sorts the listing based on the time each file or directory was touched
- `ls /home/linux/ieng6/cs15lwi22/cs15lwi22ahx` lists everything in my own directory, we cannot access other directories due to permissions
- Both `cp /home/linux/ieng6/cs15lwi22/public/hello.txt ~/` and `cat /home/linux/ieng6/cs15lwi22/public/hello.txt` do not work due to permission issues as well

## Moving Files with `scp`
- First I used a simple code given in lab which tells us what machine we are currently in
```java
class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getProperty("os.name"));
        System.out.println(System.getProperty("user.name"));
        System.out.println(System.getProperty("user.home"));
        System.out.println(System.getProperty("user.dir"));
    }
}
```
- I first ran it on my local machine, used `scp WhereAmI.java cs15lwi22ahx@ieng6.ucsd.edu:~/` to copy the file into the ieng6 computer, and ran it on the remote machine to get the following

![scp](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/whereami.png?raw=true)
- The run on the local machine showed the information of the local machine while the remote run showed the the information of the remote machine

## Setting an SSH Key
- First, I used the `ssh-keygen` command and left all the prompts empty as not having a passphrase decreses the time it requires to connect to the ieng6 server
- Using the `scp` command, I copied the public key generated from the client to the server
- Now I can `ssh` and `scp` into the remote server without entering my password everytime as seen below

![no-password](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/no-password.png?raw=true)

## Optimizing Remote Running
- After copying the `WhereAmI.java` file into the remote server using `scp`, I am able to `ssh` into the server, compile and run `WhereAmI.java` all in one line as seen below

![image](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/no-password-one-line.png?raw=true)
- Through the lack of a passphrase and combining multiple commands into one line through the use of quotes and semicolons, remote run times can be reduced significantly
- Now, in our command history, we have the following two commands
    - `scp WhereAmI.java cs15lwi22ahx@ieng6.ucsd.edu:~/`
    - `ssh cs15lwi22ahx@ieng6.ucsd.edu "javac WhereAmI.java; java WhereAmI"`
- To minimize the number of keystrokes to remotely run `WhereAmI.java`, we have a few options, but I believe the following are sufficient.
    - Assuming that these two commands were the last two done in the terminal, we can simply press `UP_ARROW`, `UP_ARROW`, `ENTER` twice. This works because the two `UP_ARROW` key hits bring us to the `scp` command. After running this, the `ssh` is now two commands back in the history, so we have to click `UP_ARROW` twice again. This gives a total of 6 keystrokes.
    - With a single click and drag, we can copy any command using `Ctrl + C` and paste it with `Ctrl + V`. After that, we can click `ENTER` to run that command. This is a total of 6 keystrokes and we must do it twice in this case, for a total of 12 keystrokes. However, this is likely the solution that will be mostly used due to the fact that we cannot always guarentee that the command we would like to run is very recent in the command history like we assume in the previous option.

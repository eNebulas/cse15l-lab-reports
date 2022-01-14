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

## Setting an SSH Key

## Optimizing Remote Running

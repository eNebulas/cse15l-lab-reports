# Lab Report 3: Streamlining `ssh` Configuration

## Creating the `.ssh/config` file
- First, we navigate to our `.ssh` folder in our home directory. We can see the `.ssh` folder in the following image where we use `ls` in the home directory.

![ls_in_home_dir](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-ls-main-dir.png?raw=true)
- Now, we change our directory to the `.ssh` folder using `cd` and create our `config` file with `code`. This also opens the file in VSCode.

![cd_to_.ssh_folder_and_make_config](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-cd-ssh-create-config.png?raw=true)
- From here, we fill out the necessary information, namely the host name and our username. There is no need to do anything with our password as we have already made a public and private key so we no longer have to type in our password when we `ssh` into the `ieng6` remote server.

![show_config_file](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-config.png?raw=true)
- As we can see in the following image, we have sucessfully created our `.ssh/config` file

![ls_in_.ssh_to_show_config](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-ls-ssh-dir.png?raw=true)

## Using the `ssh` command
- Using `cd ..` we navigate back to the home directory, although as we will see later we can use `ssh` anywhere on my computer. For now, we call the `ssh ieng6` command in the following image as we have called our config `ieng6`.

![ssh_using_ieng6](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-ssh-command.png?raw=true)

## Using the `scp` command
- In order to copy a file, we must first navigate to the directory where the file is located. I have a `CSE15L` folder on my desktop, so we can use the `cd` command to navigate to that directory. In this directory, as seen by the `ls` command, I have already created a file called `hello_world.txt`. We can go ahead and use `code hello_world.txt` to open this file in VSCode.

![go_to_dir_with_file](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-cd-check-file.png?raw=true)
- Here is what is contained in the file as seen in VSCode, a one line text file that says `Hello, World!`.

![show_file](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-code-hello-world.png?raw=true)
- Now, we can copy our file in one line using the `scp` command. This command is shortened due to the setup of the `config` file. `scp [File Name] ieng6:[Directory]` is what we would use to copy any file over. In this case, we copy `hello_world.txt` into the home directory in the `ieng6` remote server. After copying the file, we can `ssh` into the remote server to check if the file is there. Note that we can use `ssh ieng6` regardless of what directory we are in my local machine. Using `ls` in the remote server shows that the file has indeed been copied over. As we are Linux, we can use `vim` to check if the contents of the file are also accurate.

![scp_and_show_file_in_ssh](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-scp-hello-world.png?raw=true)
- As we can see below, the file's contents have been copied over as well. We can go ahead and exit vim using `:wq` where the `w` is saving and the `q` is quitting.

![file_in_ieng6](https://github.com/eNebulas/cse15l-lab-reports/blob/main/images/lab-report-3/lab-report-3-vim-hello-world.png?raw=true)
- Now we have succesfully streamlined our `ssh` configuration!

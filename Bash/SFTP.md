
# [Using SFTP for Remote File Transfer from the Command Line](https://cat.pdx.edu/platforms/linux/remote-access/using-sftp-for-remote-file-transfer-from-command-line/)


The **S**SH **F**`ile` **T**`ransfer` **P**`rotocol` allows you to transfer files from the command line via SSH between a local computer and a specified remote computer. Like SSH, SFTP can be run natively from the shell. This is true of macOS and Linux machines, and is also true of any up-to-date Windows 10 PC (SSH support was added in the Win10 April 2018 update) via PowerShell.

## **Instantiating an SFTP Connection with a Remote Host**

When you are at the command line, the command used to start an SFTP connection with a remote host is:

> `sftp username@hostname` 

For example, a user with the username _user_ connecting to the remote host _Ada_ would use the following command: 

> `sftp user@ada.cs.pdx.edu` 

SFTP will then ask for the password to the account you’re trying to log into. After inputting it, the SFTP connection will be instantiated. An SFTP prompt will appear, looking like the following:

> sftp> 

From here, you can use a few basic linux-like commands to navigate both your directory of your local computer and the remote directory you’re connected to. To end your SFTP session, use the _exit_ command. For a full list of SFTP commands, including those outside the scope of this guide, use the _help_ command. 

## **Remote Directory** **Navigation**

The _pwd_ command will print your current remote directory path.

The _ls_ command will print the contents of current directory. It can be used with the _-l_ flag to display directory content as a list, or with the _-a_ flag to display hidden files and directories. These flags may be used in conjunction to display all files in a list.

The _cd_ command can be used to change to a different directory. For example, _cd Documents_ would move your working directory to Documents, assuming it existed as a sub-directory within the directory from which you ran the command.

> Use _cd .._ in order to move to the parent directory, e.g. from /home/Documents/ to /home/.



## **Local Directory** **Navigation**

The aforementioned commands are within the context of the **remote** **directory**. In order to navigate your **local directory**, preface any of the above commands (_ls_, _cd_, _pwd_) with the letter _l_, like so: 

> `lls`,  `lpwd`,  `lcd` 

This indicates the command is to take place in the local directory.

## **Transferring Files**

In order to copy a file from the remote directory to the local directory, use the command _get_. Get expects at least one argument, which specifies the name of the file. This can either be just the filename if it’s in your current working directory, or an absolute file path. If a destination path isn’t specified as a second argument, the get command will default to your local working directory.  

To send files to the remote directory, use the _put_ command. This works basically the same as the get command. You must specify the file to be sent to the remote directory, either by name (only if within the current working directory) or absolute file path. If a destination path isn’t specified as a second argument, the _put_ command will default to the remote working directory. 

> Copying a directory via SFTP is slightly more complicated. This is because most command line implementations of SFTP cannot directly copy a directory, instead you can only copy the _contents_ of a directory. In practice, this means the outermost layer (i.e., the directory itself) will not be copied. You will usually have to make it yourself.
> 
> To copy a directory, follow these steps:
> 
> 1. Create a local directory of your choice using the command _`lmkdir directoryname`_.
> 2. Use _`lcd directory name`_ to navigate your working directory into the empty directory you’ve just created.
> 3. Move inside the remote directory you want to copy.
> 4. From within the remote directory, copy all the files using the command _get -r *_.
> 
> This will copy all files and sub-directories contained within the directory. This process works same way for transferring a directory to the remote host, but uses the _put_ command.
> 
> Another option is to simply compress the directory you’re trying to move, at which point the compressed folder can be transferred like any other file.

## **Using SFTP to Transfer Files to/from Stashes**

From within your SFTP session, type _cd /stash/yourstashname_. Please be aware that your stash will not show up in the stash directory if you look for it using _ls –_ it can only be accessed directly.


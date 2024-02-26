# Linux-HandNotes

### Linux Commands and Options 

There are 300+ flavors of Linux :
```
Kali Linux :  Majority ethical hacking ppl will use this Flavor
Corporate : RedHat , CentOS ,  Ubuntu , Fedora , IBM AIX , HP_Unix , Cisco Unix ,OEL.
```

What do we use in lab is CentOS 7 

## Linux Command Standard Syntax:

Command-name {options} {inputs} 
```
Options:
    - <Single-Character>
    -- <Single-Word>

Standard Option to all the commands is --help
    Ex: uname --help 
```


```Command line Syntaxes.```

```
$ command -options  
```

## Commands

In terminal, the first argument we give to execute is a command.

For example:

``` 
uname 
```
uname is a command and that is the first word of a command line syntax.


## Options

Certain commands are going to have options, Options in Linux Command line will be a second argument over the command line, Usually those options will be seen in three formats..
```
    <command>    -<single character> (Ex: -h , -v )
    <command>    --<single word> (Ex: --help , --version)
    <command>    -<single word> (Ex: -version, -help) 

 ```

For Ex :
``` 
uname -a   
uname --all 
```

# Inputs

Certain commands require inputs, Inputs are given with options in some commands and without options for some commands.

For Example:
 ``` 
ls stands for list
    $ ls /boot
    $ ls -d /boot
```

In above example, ls is a command -d is an option and /boot is an input. 
Given the command with and without option changes the behavior of the command execution.


### Hardware and Operating system Information

In general, when we purchase a new hardware like Laptops or Desktops we generally look into the configuration of the machine. So let us try to do the same for the server as well and this is minimum knowledge required while you are working on any machine either that is Desktop or Server.

So we need to login to the server to run the following commands to see the system details.
In Linux, everything is a file. So, it's all about reading respective files to know the properties


### To check the vendor of the operating system.

```
$ cat /etc/*release
```

### To check the CPU information

```
$ cat /proc/cpuinfo
```

### To check the memory information 
```
$ cat /proc/meminfo
```

###  To check the disk information
```
$ fdisk -l   or    lsblk
``` 

### To check the architecture whether it is 32bit or 64bit

```
$ uname -i

32 bit ->  i386/i586/i686 
64 bit ->  x86_64

PS Note: Starting CentOS 7, We don't have operating systems coming in 32 bit any more. Hence, we always see 64 bit.
With this information in hand you will have an idea of what you are dealing with and the specifications of that Linux machine. 

```



## Listing Files and Directories

# List Files

In windows OS, you generally see the list of files when you open a particular folder, But Linux is mostly command line and hence you may not see the files by default. Hence, you need to execute a command to check the list of files.

ls is a Linux shell command that lists directory contents of files and directories. Some practical examples of ls command are shown below.

```
Syntax: ls <Options> <Path>
```

Note that ls command works without an input i.e both the options and path are optional. It works with or without them.
```
$ ls -ld /opt
```

Get list of files and directories but it may not show hidden files.
```
$ ls
```

Get list of hidden files and directories.
```
$ ls -A
```

Get list of files with long format, usually shows properties of a file
```
$ ls -l
```

We can combine multiple options as well.
```
$ ls -Al
```
## NOTE: 
Giving multiple options depends on the command. ls accepts multiple options but it isn't applicable for all.


### Creating files

We can create files in multiple ways/commands in Linux. We will use `touch` command to create the file.
```
Syntax: $ touch <filename>
```
touch command by default creates an empty file.

```
$ touch file.txt
```

To check the file created.
```
$ ls -l
```
In the above ls command output you can see the file is an empty size file by referring the fifth colum.

touch command can create multiple files at a single go as shown.

touch sample notes.txt lambda.py

To check the file created.
```
$ ls -l
```
### Important Takeaways:

In Linux OS, there is no file-extensions. Extensions are given only for user understanding.
Also, linux commands and files are case sensitive.

```
training.txt and Training.txt are 2 different files as per the linux ( as it's case sensitive )
```


### Removing Files


In Linux to remove files we have `rm` command, We can also use unlink command which does the same thing yet rm is widely preferred and used command.

        Syntax: rm <filename>
```
$ rm fileName.txt
```

Now again when you list the files using ls command the sample file should be gone as you have removed it.
```
$ ls
$ rm -i fileName.txt
```

It may ask you for a prompt (yes/no) [Not all the times] to remove the files. You can suppress the prompt by adding -f option in the command.
```
$ rm -f fileName.txt
$ ls
```

Note: Be careful while removing a file as it deletes all the contents of the file and retrieving the lost data is not possible in most of the cases.
Thing you can explore.

How to remove multiple files ?
```
$ rm file1 file2
```

###  Copying Files

In Linux to copy a file we have cp command. Alternatively we have rsync but mostly we prefer to use cp command in general.
```

    Syntax: cp <source-file> <destination-file>

            $ cp notes.txt pages.txt
```

You can check whether the file has been copied or not by referring ls command output.

            $ `ls`

NOTE: If destination exists it will overwrite the file and in some cases it will ask you for a prompt (yes/no) to overwrite the file or not.


## Rename Files

### Renaming/Moving a File

In Linux, in order to change the name of a file we use mv command.

        Syntax: mv <source-file> <destination-file>

                $ mv notes.txt note.txt

You can check whether the file has been renamed or not by referring ls command output.

                $ ls

NOTE: Unlike Windows, Linux filesystem are Case-Sensitive ones, Meaning the file note.txt & NOTE.txt can be referred as two different files. But windows FAT & NTFS filesystem are Case-Insensitive, Meaning the file note.txt & NOTE.txt are same files and you cannot create multiple files with same name.

                $ mv note.txt NOTE.txt

You can check whether the file has been renamed or not by referring ls command output.

                $ ls

## NOTE: 
    If destination exists then it will overwrite the file and in some cases it will ask you for a prompt (yes/no) to overwrite the file or not.
    mv command intention is to move the file from one location to another yet we use mainly to rename the files as well.


# Creating Directories

### Linux Directory Structure :

Unlike any operating system Linux also has its own directory structure and here in linux it starts with /
```
Ref: https://qph.cf2.quoracdn.net/main-qimg-849caf34b204bb41bcb94b20335cab6f
```

### Directories:

* / -> Root Directory
```
Types of files:
    d - Directory   
    - - Regular file 
    l - Link
    b - block devices
    c - character files 
    S - socket files 
    p - Named pipe file 
```
### pwd: present working directory
```
To check in which directory you are in 
    $ pwd
```

### general Directory Switch Commands

```
Change from one directory to another
    $ cd <directory>

    $ cd -> This will take you to home directory 
    $ cd - -> This will take you to previous dir 
    $ cd .. -> Takes you to parent directory 
```

### Directory sandbox 
```
 -> Create Directory 
 
    $ mkdir demo 

 -> Remove a directory 
    rm / rmdir (Empty Dir)
    $ rm -r dirname

*  Copy a directory 
    $ cp -r dir1 dir2

* *Renaming / Moving a directory
    $ mv source destination

    * If destination does not exists: Rename the directory
    * If destination exists:
         -> Destination is a file:
                Invalid operation
         -> Destination is a Directory:
                File/Directory will move inside that directory
```


### Basic Connection

In windows, we use ```\``` (backslash) to give the path of a file or a directory but in Unix & Linux we use ```/``` (forward slash).

In Linux, we have a ```ROOT DIRECTORY``` where the path of any directory ends here. A simple forward slash ```(/)``` is called as a ROOT DIRECTORY.

Additionally, to the list of directories provided in the above diagram we have more and each and every default directory are under```/``` have some purpose in the operating system.
Unlike Windows, Linux is Command line based OS, So if you want to move from one directory to another directory we would be using commands to get it done.



# Navigate Directories

## Present Working Directory

To check where you are currently in the system we use pwd command.

    $ pwd


##Navigate to Directories

To change the working directory from one location to another we use cdcommand

    Syntax: cd <directory>
    $ cd /bin

you will switch to /bin directory

    $ pwd

you can check your current working directory using pwd command

    $ cd

simple cd command will take you to the home directory of the user

    $ pwd

observe the output

    $ cd - This command will take you the previous directory that you were using.

Double dot (..)
```
$ cd /etc/yum

$ cd ..

$ pwd

$ cd ..

$ pwd

.. means parent directory and it takes you to the parent directory of the current directory

### Single dot (.)
```

Dot in linux indicates present working directory, you can use it in the commands which we have used so far

```
$ ls observe the names of the files

We will try cp command with the . option

$ cp /etc/passwd .

$ ls

```

Now if you compare the output from the previous ls you will be able to see the file with name sample in the present directory.

### User Management
```
Create a user account named userName
  
  $ sudo useradd userName  
  $ cat /etc/group   

Create a group account names groupName
  
  $ sudo groupadd groupname

Adding User to the Group
  
  $ sudo usermod -a -G groupName userName  

Changing the user password
  
  $ sudo passwd userName   

Deleting the user  `userName` from the group `groupName`
  
  $ sudo gpasswd -d userName groupName

```   

## Common Filtering Pattenrs with awk and cut

``` 
awk and cut are very powerful file filtering tools on linux
```
* cat is to read the file from top to bottom 
* tac is to read the file from bottom to top 
* tail is to read the lines from bottom to top based the number of mentioned lines ( By default, it prints the last 10 lines of a file )
* head is to read the lines from top to bottom based the number of mentioned lines ( By default, it prints the top 10 lines of a file )

### Here are common examples of head, tail cat , tac, sed and cut

```
# cat /etc/passwd               //To read a file
# cat -n /etc/passwd            //reads and will place a serial number at the starting of every line
# tac /etc/passwd               //To read the file from bottom to top


# head passwd                   //reads the top 10 times
# head -n 5 passwd              //Reads the first 5 lines

# tail passwd                  //Reads the last 10 lines
# tail -5 passwd               //Reads the last 5 lines
```

### To print the lines from specific line to line like print the lines in between 10 to 15
```
# sed -n -e '10,14 p' passwd         //Prints the lines from 10 to 14
# sed -n -e '1 p' -e '10 p' passwd   //prints 1st and 10th line in the passwd file 
# sed -n -e '9 p' /etc/passwd        //To print a specific line

# cat /etc/passwd | grep login       //To find the word login
```

###To see the first field in every line of the file which has a common delimiter
```
# cut -d : -f1 /etc/passwd        //Will display the first field in each and every line
If you want first and 4th field

# cut -d : f1,4 /etc/passwd
# cut -d : -f1-4  /etc/passwd     //Prints the fields from 1 to 4

```
![image](https://github.com/b54-clouddevops/Linux-Notes/assets/57979895/a3474b34-730f-4212-983a-36710a0208c1)


# Create Directories


Creating Directory is same as creating a Folder in your windows machine. You can create a directory using mkdir command.

    $ mkdir demo

This will create a new directory with the name demo. you can check using ls command.

    $ ls

Now you can see demo directory listed.
But to determine demo is a directory, better always use ls -l command output. Directories start with d character of ls -l output.

    $ mkdir -p demo/new/item1

-p option is used to create the directory recursively even if the parent directory is missing

    $ mkdir demo1 demo2 demo3 demo4

You can also create multiple directories.

    $ ls


### Ownerships 

`chown` is the command to change the ownership of the files and directions.

    Syntax: chown userName:groupName  fileName.txt 
```
    # chmod centos:devops  fileName.txt   [ Changes the owner & group of the file to centos & devops ]
    # chmod -r centos:devops dirName/     [ Changes the owner & group of the directroy to centos & devops ]
    # chmod -rf centos:devops dirName/    [ Recursively changes the owner & group of the directroy to centos & devops along with the files in the directory ]
```


### Permissions  

In linux, permissions are classifed to Read [ `r` and the value of it is 4 ] ,Write [ `w` and the value of it is 2 ] ,execute [ `x` and the value of it is 1 ] ,

    Syntax: chmod 761 fileName   [first 7 is user , second 6 is group and third 1 is others permission]
```
  U:  4+2+1 = 7     [ Owner can read, write and execute the file ]
  G:  4+2   = 6     [ Owner can read, write the file ]
  O:  1     = 1     [ Other can just run the file ]
```


### Additional things to learn.


    There are total seven type of files in Linux. Explore each of them. Directory and regular file is two of them.
    Types: Directory, Regular File, Block Special File, Character Special File, Named pipe file, Link file, Socket file.

# Create Directories

Copying directories can be done with the same command cp that is used to copy the files but while copying the directories we need mention -r option.

    Syntax: cp -r dir1 dir2

It copies all the contents of dir1 into dir2.

Note: If dir2 already exists dir1 will be copied inside dir2

    $ cp -r demo1 demo2

Copy always changes the behavior based on Target Directory.

    $ cp SOURCE TARGET
```
-> if TARGET exists and if it is a file then it is invalid operation.
-> if TARGET exists and if it is a dir then it copies the file inside the directory.
-> if TARGET doesnt exist then it will copy the directory
```


# Moving / Renaming Directories

# Moving Directories

Moving directories or renaming directories can be done using mv command.

    Syntax: mv source destination

    If destination doesn't exist it renames the directory
    If destination exists the source will be moved into the directory

    $ mv demo4 DEMO4

This will rename the demo4 as renaming
    $ ls


## Removing Directories

To remove a directory we use rmdir command in linux. Removing directories also deletes all the files that the directory holds inside it.

     Syntax: rmdir <directory>

    $ mkdir demo1
    $ ls
    $ rmdir demo1
    $ ls

### Check the output to see if the directory is deleted or not.

It deletes the directory with the name demo1 but in the following example you will see an error saying the directory is not empty. That is because we have already created sub-directories named new and test inside demo.

    $ mkdir -p demo1/{new,test} 
    $ rmdir demo1

To delete them recursively we use -r option.

    $ rm -r demo1 
    $ ls

Some times you might be propted for (yes/no) to delete the files and if we want to make it forceful delete without prompting then we use -f option.

Note: Once the files are removed there is no way of retrieving it back them.


# Concatenate Files

### Concatenate File Content

cat(concatenate) command is very frequently used in Linux. It reads data from the file and gives their content as output. It helps us to create, view, concatenate files. So let us see some frequently used cat commands.

    Syntax: cat <filename>

    cat /etc/passwd

It shows the content of the file

    cat -n /etc/passwd

It shows the content of the file along with the line numbers

    tac /etc/passwd

It displays the content of the file in reverse order. 
Additional things to Learn.

    -A option in cat command.


### Filter Commands

In many situations you might want to have only a certain number of lines from a file. You can use filter commands or a combination of them to get your work done.

Usually the filters are based on

    Line Numbers
    Row Filters
    Column Filters

#### Head Command

To filter the output based on line numbers and that to be from starting of the file then we use head command.

    Syntax: head <filename>

By default head command gives you top 10 lines of the file but you can change it according to your needs.

    head /etc/passwd
    head -n 5 /etc/passwd

It gives the first 5 lines of the file

#### Tail Command

head command gives you the top lines of the file however if you want to print the last lines you can use tail command

    Syntax: tail <filename>

tail command will print last 10 lines and however you can change them using -n option.

    tail /etc/passwd

    tail -n 5 /etc/passwd

It gives the last 5 lines of the file

#### Grep command

The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression (grep stands for globally search for regular expression and print out).

    Syntax: grep <word> <filename>
    grep root /etc/passwd

It fetches all the lines which have the word root in them.

### Awk Command

In some cases the content needs to be filtered based on the columns in that case we use awk command.

    Syntax: awk -F 'delimiter' '{print $column-number}' <filename>

    awk -F : '{print $1}' /etc/passwd

It will print the first column of the file

    awk -F : '{print $1,$2}' /etc/passwd

It will print the first and second column of the file
Additional things to learn.

### cut command 

Cut is a command which helps us in extracting the sections of the lines based on the delimiters.

   $ cut -d : f1 /etc/passwd [assuming the delimiter as `:` prints the 4th field in each and every line of the file]
   $ cut -d : f1-4 /etc/passwd [assuming the delimiter as `:` prints the fields from 1-4 in each and every line of the file]


### Process Management 

Most useful commands to see the list of running process and their utliisations are :
    $ ps 
    $ top 

    Examples on their usage
 
```
    $ ps -ef                 [ Shows every process on the system using standard syntax]
    $ ps -aux                [ Shows every process on the system using BSD syntax ]
    $ top                    [ Top shows you dynamic result and refresh the result for 3 seconds ]
    $ ps -U root -u root u   [ every process running as root (real & effective ID) ]
    
```

### kill   

Kill is a command which has the capability to kill any process and the parent process of your choice. Also kill has lot of signals to kill :

```
    Syntax: 
        $ kill pID 
        $ kill -9 pID  [ To delete a process forcefully ]
```


### Regular Expressions.

    https://www.grymoire.com/Unix/Regular.html#uh-6

#### SED & AWK

    https://github.com/chiranjibKonwar/Documentation/blob/master/Sed%20%26%20awk%20101Hacks%20%20.pdf


# VI Editor

### Linux Editors.

There are so many editors which are part of different Linux Operating Systems. Editors like vi, vim, nano, gedit, emacs and more are mostly known editors. Among these 90% of the operating systems comes with vi editor as default editor.

```vi   ```is very powerful editor and it comes with much enhanced options in vim. Hence, we choose to go with vim in our sessions.
### VIM Editor.

vim editor has three modes and each and every mode has its own purpose and allows you to perform certain actions.

    ESC Mode
    COLON Mode
    INSERT Mode

VI MODES

Following are the operations done by each and every mode.

`ESC Mode` is used to perform the following operations.

    Line Operations.

    -> Copy Lines

    Ex: Copy a Single Line

     1. Ensure you are in ESC Mode, by pressing ESC.
     2. Take the cursor to that line.
     3. Press yy to copy the line

  -> Paste Lines

  Ex: Paste a Single Line.

      1. Take the cursor to the line where you want to paste then press p after performing copy using yy.


  -> Delete/Cut Lines

  Ex: Cut / Delete a Single line

      1. Ensure you are in ESC Mode, by pressing ESC.
      2. Take the cursor to that line.
      3. Press dd to cut/delete the line

    Word Operations

    -> Copy Words

    yw

    -> Paste Words

    p

    -> Delete Words.

    dw

    n , Number can combined with any option of above. For ex to copy 10 lines 10yy, and if we want to delete 5 lines then 5dd

    Undo Operations.

    u is available to undo the operations like (CTRL + Z ) in windows.

COLON Mode

COLON is used to perform the following options.

   #### Search Operation.

    Ex: Search a word.
        Ensure you are in ESC mode and press : to go to COLON Mode.
        :/WORD , GIve WORD which you want to search.

  ####  Search & Replace

    Ex: Search a Word and Replace
        Ensure you are in ESC mode and press : to go to COLON Mode.
        :%s/WORD1/WORD2/ -> This will replace WORD1 with WORD2
        Flags : g, i :%s/WORD1/WORD2/g -> global means all possibilities on the line will be changed. :%s/WORD1/WORD2/i -> case-sensitive replace.

  ####  File Operations
        Save File :w
        Quit Editor :q :q! -> Quit with out saving
        Save and Quit :wq

### INSERT Mode

    INSERT mode is used to add your own content, whereas above two modes are dealing with existing content on the file.

    NOTE: There are lot many operations are available, But we are talking which is needed for DevOps prospective.

# Find Files

### FInding Files

Most of the times when you login you have no idea where the files are located at. Since Linux doesn't have an UI it would be a tedious job to traverse through all the directories to find a single file but linux provides find command to search for a file with the name.

    Syntax: find <location-to-find> <search-criteria>

    find / -name passwd

This command searches through all the directories as we have given the location as /. You will find many files, but you can narrow down the search nby providing /etc directory.

    find /etc -name passwd

This command only searches /etc directory for the passwd file. You can observe that the results are less in number.
Additional things to learn.

    https://alvinalexander.com/unix/edu/examples/find.shtml


# Internet Utilities

### Command line browser

Most of the times you need to browse urls to and fetch that content to command line. Some times we need partial information of the URL or the full information. curl command is available to browse the content over command line.

    Syntax: curl <url>

    curl www.google.com

Using curl command we can download the files.

    curl https://archive.apache.org/dist/tomcat/tomcat-8/v8.0.0-RC1/bin/apache-tomcat-8.0.0-RC1-deployer.tar.gz -o apache-tomcat-8.0.0-RC1-deployer.tar.gz

Above command will download the file to the given filename. But with out giving the filename also we can download it to the default file name.

    curl -O https://archive.apache.org/dist/tomcat/tomcat-8/v8.0.0-RC1/bin/apache-tomcat-8.0.0-RC1-deployer.tar.gz

# Download Files

Most of the times we need to download softwares or tools from internet to work on them. We can use wget command to download the files from internet.

    Syntax: wget <url>

In this example I will be downloading tomcat from the internet.

    wget https://archive.apache.org/dist/tomcat/tomcat-8/v8.0.0-RC1/bin/apache-tomcat-8.0.0-RC1-deployer.tar.gz

    ls

NOTE: wget command will not come by default with OS. We need to exclusively install that, So better use curl command all the time.
Extracting the files from tar

Many times in Linux world all the softwares are packaged either in .zip or .tar format. To extract the files from .tar extension we can use tar command.

    Syntax: tar -xf <filename>.tar.gz

    tar -xf apache-tomcat-8.0.0-RC1-deployer.tar.gz

To extract archives we use -x option and -f means file.


# Pipes

### Pipes

Pipes are used to send the output of one command to another command without storing the content anywhere physically on disk.

    Syntax :  com1 | com2

    Ex: cat /etc/passwd | grep root

Note: All the commands will not accept inputs over pipes. In case if we need to take the input then we take the help of xargs command.

    touch sample.txt

    ls

    echo sample.txt | rm -f

    ls

Now you can use the xargs command.

    echo sample.txt | xargs rm -f
    ls



### sudo 

`sudo` is a command in linux to give the temporary privileged access to the user

Below commands shows how to switch between the users

```
$ sudo su -   [will be switched to the root user]
# whoami      [shows you the output as root]

```

### How can we enroll the users to gain sudo permission ?

By default, in centos apart from root and the centos user, none of the users will be having root access.
Here is the file where we can add / enroll the users to gain sudo access

```
$ cat /etc/sudoers   [ You can see the list of users with sudo access in the system ] 

```

### Package Management  

In centos linux, packages can be installed in any of the below ways :

    1) YUM  [YUM is the package manager in Centos Linux : YUM handles all the pre-req and co-req packages of the actual package]
    2) RPM  [RPM Package Manager : Download the package and install it manually. We are responsible for pre-req and co-req packages of the actual package]
    3) Source Code Based Installation [ Ref: https://www.makeuseof.com/compile-install-software-from-source-linux/ ]

Examples of `yum` usage :

    # yum install packageName -y     [ Installs package ]
    # yum remove packageName         [ Deletes package ]
    # yum update packageName         [ Updates package ]
    # yum list installed             [ Shows the list of installed packages ]
    # yum update -y                  [ Updates all the installed packages on the server ]

Examples of `rpm` usage : 
    # rpm -i packageName.rpm        [ Installs package ]
    # rpm -U packageName.rpm        [ Upgrades package ]
    # rpm -e packageName.rpm        [ Deletes package ]
    # rpm -q packageName.rpm        [ Queries package ] 

### Service Management  

Systemctl is the command to start,stop, restart , enable the service in centos 7.

Examples of `systemctl` usage :

```
    # systemctl start serviceName
    # systemctl stop service
    # systemctl restart service
    # systemctl enable service
```

### Network Management  

```
    # curl ifconfig.co   [ shows you the public ip address of the server ]
    # ip -a              [ shows you the private ip address of the server ] 
    # netstat            [ shows the network statistics ]
    # netstat -ln        [ shows the actual core information]
    # netstat -tulpn     [ shows you the list of listening ports and the associated process running on it]

```
### Filters:
See the complete content inside the file 

```
   $ cp /etc/passwd .
   $ cat passwd
   $ cat -n passwd 
   $ tac passwd 

`head`  : This prints the top 10 lines by default of the file
`tail`  : This prints the last/bottom 10 lines by default of the file

    --> Print from ending of the file 
        $ tail passwd 
            It prints last 10 lines

        $ tail -3 passwd 
            It prints last 3 lines 
```

# cut sed awk : Advanced Filtering Tools on linux
```
    -> Search a word and print those lines 
        Syntax: grep word file 
        $ grep ec2-user passwd 

    -> Column based filter 
        Syntax: cut -d delimeter -f number file 
        $ cut -d : -f 1 passwd 
        $ cut -d : -f 1,5 passwd
        $ cut -d : -f 1-5 passwd
```

### EDITORS: 

There are a lot of fancy editors in Linux --> vi ,vim , nano are few famours editors to edit the file.
They are just notepad,

```
    vim editor is not available by default in centos 7 and we need to install it, To install vim editor type the following command.
      sudo yum install vim -y
      
      Example Usage: $ vim filename.txt
      
```

Editor vi/vim works in 3 modes :

```
 1) ESC Mode 
 2) COLON Mode 
 3) INSERT Mode 
 
 * vim filename  --> To enter smething, yiu've to be in INSERT Mode --> pres i 

 After entering the data , if you want to save :
 
First clock ESC --> COLON --> wq!

wq! stands for Write and Quit which means SAVE

w --> Write
q --> Quit
! --> End of the Expression.

Using the forward slash / we can search the content.


```
### VIM Search and replace examples

```
%s/word1/word2/ : % s is going to search for the first occurrence in each and every line and replaces word1 with word2.
%s/word1/word2/g : % s is going to search for the all occurrence in each and every line and replaces word1 with word2.
s/word1/word2/ searches the word1 's first occurrence on the line where your cussor is placed 
s/word1/word2/g searches the word1 's first occurrence on the line where your cussor is placed 

```

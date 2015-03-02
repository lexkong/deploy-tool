# What is deploy-tool

deploy-tool tool is used to authorise logins on multiple remote machines at the same time and generate a login command for you to login these machines. It can also deploy your personal bash environment or vim, emacs profiles to your test machines at the same time.

# Features

+ Configure ssh login without password on multiple remote machines at the same time.

+ Configure your .bashrc, .vimrc and .emacs file and copy them to the remote machines to build your bash environment and edit environment.

+ Copy your own script files or executable files or other files to the remote machines to allow you use them directly.

+ deploy-tool can generate a new command for you, thus you can login the machines very convenient.

+ With undeploy option, you can restore the machine to its previous status in case you want to login a machine which is owned by others


# How to use deploy-tool

deploy-tool only have three main features, so it is very easy to use.

1. Run command `deplop-tool -e` to set static ip and dynamic ip of the remote machines. Also the password of the remote machines.
```bash
# deploy-stastll -e
```

staticip: If you have two machines that owned by you, you can put their ip address here

ip: the ip address of the remote testing machines which will be frequently restore and reserve.

password: password of the remote machines

configured: this option is used to make sure that you have checked your .bashrc file and make sure the file have no destructive settings to the remote machines.

2. Configure ssh login without password and copy .bashrc, .vimrc and .emacs file to remote machines.

```bash
# deploy-stastll -d
```

3. Undeploy remote machines, this will revert .bashrc, .vimrc and .emacs file on the remote machines

```bash
# deploy-stastll -u
```

4. Login the remote machines with `tsh` command

```bash
# tsh -a
```

Note:

You can issue `tsh -h` to get the option and ip address map

When you login the remote machine, you will see something like:

`[host-b(lkong)]$`: host-a indicate that you login this machine with `tsh -a` command, lkong indicate that the tester name is lkong

5. Configure more machines with ip address specified on the command line

```bash
# deploy-stastll -D $ip1 $ip2
```

6. Undeploy remote machines with ip address specified on the command line

```bash
# deploy-stastll -U $ip1 $ip2
```

7. Print help messages

```bash
# deploy-stastll -h
```

8. If you want to upload your own scripts, executable files or other files, you can copy them to ~/.deploy-tool./bin or ~/.deploy-tool/testfiles

9. If you want to change something in file bashrc, vimrc or emacs, you can find them at ~/.deploy-tool/conf/

10. When you login the remote machine `cd $tester`, you are enter into your workspace.

11. In the remote machine, you can run a useful command `cg`:
```bash
[host-a(lkong)]$cg -h
cg [chad] branch
branch: which branch you want to swith, like git
    -h print this help message
    -c show current branch
    -a show all the branch
    -d delete a branch
[host-a(lkong)]$cg -a
branch1
master
[host-a(lkong)]$cg branch2
You are now on branch branch2
[host-a(lkong)]$cg -c
branch2
[host-a(lkong)]$cg -d branch1
[host-a(lkong)]$cg -a
branch2
master
[host-a(lkong)]$
```

Through this way you can do different test in different directory.

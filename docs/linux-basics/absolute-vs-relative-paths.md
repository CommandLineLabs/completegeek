# Absolute vs Relative Paths

A path is simply a string (a series of characters, of letters and symbols and numbers) that spells out a particular location for files on the computer.

In the last chapter, we used paths when we created directories, changed to them, and removed them. We looked at paths when we used the `pwd` command to display the current directory, or when we looked at the command prompt to see what directory we were in.

There are two different ways of specifying paths. Those two ways are **absolute** and **relative.**

I see even fairly experienced programmers messing up absolute vs relative. This is an absolutely foundational piece of knowledge you'll need throughout your career. So we're going to do a bunch of examples to help you nail down the concept.

Absolute paths have zero ambiguity. They start from the root of the file system, and specify the path exactly. Each absolute path refers to one and only one directory (or file). Let's look at a path we've already dealt with in the last chapter as an example:

`/home/ubuntu`

The first part of that absolute path is the root directory, `/`. That's not a separator between two directories, that's an actual directory itself. The "root" of the tree, if you will. (Yes, I know actual trees with leaves have multiple roots. Bear with me. Paths don't.)

Then you have the `home` directory, then `/` which in this case is a separator between two directories, and then the second directory name, `ubuntu`. Only the first `/` is the root directory; every other slash is a separator between two directories.

Relative paths, by contrast, are **relative** to the directory you're in now. When you're in one directory, that relative path will go to one and only one directory or file. If you were in a different directory, though, that relative path could go to a different directory or file, or to nothing (an error).

Let's make this a little more real with some examples. Open a terminal and make sure you're in your home directory, and then make the following series of directories.

```bash
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$ mkdir relative1
ubuntu@completegeek:~$ mkdir relative2
ubuntu@completegeek:~$ mkdir relative3
ubuntu@completegeek:~$ mkdir relative1/apple
ubuntu@completegeek:~$ mkdir relative2/apple
ubuntu@completegeek:~$ mkdir relative3/apple
ubuntu@completegeek:~$ mkdir /home/ubuntu/absolute1
ubuntu@completegeek:~$ mkdir /home/ubuntu/absolute1/apple
ubuntu@completegeek:~$ mkdir /home/ubuntu/absolute1/peach
ubuntu@completegeek:~$ mkdir /home/ubuntu/absolute1/pear
ubuntu@completegeek:~$
```

What did we do there?

First we made sure what directory we were in -- vital if you're going to use relative paths.

Then we made the directories relative1, relative2, and relative3 in your `/home/ubuntu` folder, without specifying the `/home/ubuntu` part. We were able to do that because we used relative paths. Then we created `apple` directories inside `relative1`, `relative2`, and `relative3.`

Next we used **absolute** paths to create `absolute1` and `apple,` `peach,` and `pear` inside it.

Now let's change directories in some of the directories we just created.

```bash
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$ cd relative1
ubuntu@completegeek:~/relative1$ cd apple
ubuntu@completegeek:~/relative1/apple$ pwd
/home/ubuntu/relative1/apple
ubuntu@completegeek:~/relative1/apple$ cd ..
ubuntu@completegeek:~/relative1$ cd ..
ubuntu@completegeek:~$ cd relative2/
ubuntu@completegeek:~/relative2$ cd apple/
ubuntu@completegeek:~/relative2/apple$
```

Note that we used the **exact** same command, `cd apple`, to change into two entirely different directories.

When we were in the `/home/ubuntu/relative1` directory, `cd apple` took us into `/home/ubuntu/relative1/apple`. But when we were in the `/home/ubuntu/relative2` directory, `cd apple` took us into `/home/ubuntu/relative2/apple`. Not the same place, because we used relative paths.

We could also have used absolute paths.

```bash
ubuntu@completegeek:~/relative2$ pwd
/home/ubuntu/relative2
ubuntu@completegeek:~/relative2$ cd /home/ubuntu/relative3/apple/
ubuntu@completegeek:~/relative3/apple$ pwd
/home/ubuntu/relative3/apple
ubuntu@completegeek:~/relative3/apple$
```

Note that because we specified the exact, absolute path, we didn't have to change directories beforehand. Absolute paths don't care what directory you are in. So from `/home/ubuntu/relative2/apple`, we were able to change directly to `/home/ubuntu/relative3/apple`.

Now let's look around the file system on your VM a little further. Let's cd to the root directory:

```bash
ubuntu@completegeek:~/relative3/apple$
ubuntu@completegeek:~/relative3/apple$ cd /
ubuntu@completegeek:/$ pwd
/
ubuntu@completegeek:/$ ls
bin  boot  dev  etc  home  lib  lost+found  media  mnt  opt  proc  root  run  sbin  snap  srv  sys  tmp  usr  var
ubuntu@completegeek:/$
```

We used the cd command to change to the root directory, the top level of the file system. Everything else is below the root directory. Including the `home` directory.

There's a lot of other directories in the root directory. Every one of them is there for a reason, and I promise, we'll go over that later. For now, let's cd to the `home` directory and then to our `ubuntu` directory using relative commands.

```bash
ubuntu@completegeek:/$ cd home
ubuntu@completegeek:/home$ cd ubuntu
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$
```

Now let's try that again using absolute paths:

```bash
ubuntu@completegeek:~$ cd /
ubuntu@completegeek:/$ pwd
/
ubuntu@completegeek:/$ cd /home/ubuntu
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$
```

Much less work!

Also we've got a little ambiguity I'd like to call out. There is a directory called "home" that is under the root directory: `/home`. And then there is **your** home directory, located in the `home` directory, called `/home/ubuntu`. You can almost always tell which one is meant from context, but be aware of the difference.

Now let's look at a practical example. Linux keeps logs, or lists of things that have happened on the system. (We're going to go into a lot of detail about this later. It's vital for troubleshooting.)

We're going to cd to the logs directory and look at one of the logs using the `less` utility. Less is a program used to look at the contents of files. (There's a program called `more` that is used to display a screen of text at a time. When someone came up with a more advanced version of `more`, of course they called it `less`. There's a long and painful tradition of bad jokes in Unix/Linux.)

```bash
ubuntu@completegeek:~$
ubuntu@completegeek:~$ cd /
ubuntu@completegeek:/$ cd var
ubuntu@completegeek:/var$ cd log
ubuntu@completegeek:/var/log$ ls
alternatives.log  auth.log.2.gz          dist-upgrade  journal        landscape  syslog.1              wtmp
apt               btmp                   dmesg         kern.log       lastlog    syslog.2.gz
auth.log          cloud-init-output.log  dmesg.0       kern.log.1     private    ubuntu-advantage.log
auth.log.1        cloud-init.log         dpkg.log      kern.log.2.gz  syslog     unattended-upgrades
ubuntu@completegeek:/var/log$ less syslog
ubuntu@completegeek:/var/log$
```

When you run the `less syslog` command you'll be looking at the contents of the syslog file. You can hit the spacebar to see the next screen, up arrow or down arrow to scroll backward or forward, or `q` to quit. Once you hit `q` you should be back at your command prompt.

OK, that's the bad way of doing it. How do you open that file quickly and easily without all the fuss?

```bash
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$ less /var/log/syslog
ubuntu@completegeek:~$
```

Follow the same instructions for the `less` program, the most important of which is `q` to quit.

You don't have to change directories to open files in a different directory, because absolute paths exist! (Yes, seeing people do this the slow way does frustrate the heck out of me.)

Now let's add a tiny bit more complexity.

Remember the shortcut from last chapter, `..`? (Refers to the parent directory of the current directory.) You can use that in relative paths as well!

And finally remember the shortcut to your home directory, `~`? That shortcut refers to **your** home directory. It's a relative path for a different reason.

For **you**, `~` will always refer to `/home/ubuntu`. So it's kind of an absolute path. No ambiguity.

However, if you were logged in as the `johndoe` user, then `~` would refer to `/home/johndoe`, not `/home/ubuntu`. Just something to keep in mind for later.

If anything here is unclear, go through the chapter again, and actually do the commands I show you -- don't just read them.

## CHECKPOINT: Absolute vs Relative Paths

1. Change to the relative4 directory using an absolute paths.
2. Change to the peach directory using a relative path.
3. Change to the relative3 directory using an absolute path.
4. Change to the peach directory inside relative3 using relative paths.
5. That didn't work. Why not? Do you understand the error message you got?
6. Without changing directories, open the "auth.log" file in "/var/log" using less.
7. From the relative1, directory, change to the relative2 directory using relative paths and the `..` shortcut.
8. From your home directory, change directories to the root directory, in one step, using relative paths. Hint: use `..`. Maybe more than once.
9. Change to the /var/log directory, and then, using `~`, change back to your home directory.

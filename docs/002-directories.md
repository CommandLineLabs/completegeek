# Chapter 2 - Directories

From using a Mac or Windows computer you should already be familiar with the concept of directories (also known as folders). But to summarize, directories are places where you can store files or other directories, on your computer's hard drive (or SSD). Directories don't give you more space on the hard drive, they just give you tools to organize your files.

There are lots of files and folders already on your VM, which are part of the operating system. We'll talk more about operating systems in the next chapter.

For this entire chapter, we'll be working in your **home directory.** Your home directory is **your place** to store files on your VM. "Duh," you think. "This is my VM. All of the directories are places to store my files."

Yes, but. Unix was designed as multi-user operating systems, which means that they would have multiple people using them. Each person using the system has their own home directory, which is private to them.

You're the only person using this VM, but another advantage of keeping files in your home directory is that you can't mess up the VM itself, like you could if you change things in other directories.

The command prompt at the bottom of the screen shows you what directory you're in. If you're using vagrant, the command prompt will be "`vagrant@ubuntu-jammy:~$`". If you're using Multipass, your command prompt will be "`ubuntu@completegeek:~$`". In both cases, the tilde ("~") in the prompt means you're in your home directory. The tilde is a shortcut (short name or alias) to your home directory that works in *most* contexts. (We'll discuss the few where it doesn't work later in this course.) When you change directories, the directory in your command prompt will change as well.

We're going to go over a few commands related to directories in this chapter:

* ls: **L**i**s**t the files and folders in the current directory
* cd: **C**hange **d**irectories (switch to a different directory)
* pwd: Show the **p**resent **w**orking **d**irectory -- the directory that you are currently in
* mkdir: **M**a**k**e a **dir**ectory. Create a directory.
* rmdir: **R**e**m**ove a **dir**ectory. Deletes a directory. The directory must be empty first.

We'll also talk about the "`..`" shortcut.

First, let's see what directory we're in using `pwd`.

```bash
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$
```

We're in the ubuntu user's home directory, which is at /home/ubuntu. (The directory called "ubuntu," which is inside the directory called "home.")

If you're using Vagrant instead of Multipass, your output will look like this:

```bash
vagrant@ubuntu-jammy:~$ pwd
/home/vagrant
vagrant@ubuntu-jammy:~$
```

This is because we are in the vagrant user's home directory, which is at /home/vagrant. (The directory called "vagrant," which is inside the directory called "home.")

Now let's make a directory. (From here on most of the examples will be Multipass, because that's what I primarily use.)

```bash
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$ mkdir directory_one
ubuntu@completegeek:~$ cd directory_one
ubuntu@completegeek:~/directory_one$ pwd
/home/ubuntu/directory_one
ubuntu@completegeek:~/directory_one$
```

So we made a directory called "directory_one." Why the underscore? Well, let's talk about some rules and guidelines for choosing file and directory names in Linux. And in fact, from now on we're going to just say "file names" for simplicity. But you should know that in Unix **everything is a file**, and under the hood, directories are just files that are special. All the rules and guidelines below apply equally to files and directories.

**Rules**:

* File names are **case sensitive.** This is **very different** from what you're probably used to on Mac or Windows. This means that "Apple.txt" is a **different** file from "apple.txt". We'll explore this later
* File names can **not** include the following characters:
    * / (forward slash)
    * \> (greater-than)
    * < (less-than)
    * | (pipe symbol, on the same key as the backslash)
    * : (colon)
    * & (ampersand)

**Guidelines**:

* Despite the vast number of characters, emoji, and other symbols that are, technically, allowed in Unix filenames, we recommend that you use only capital A-Z, lowercase a-z, numbers 0-9, the underscore (_) and the dash (-). You'll eliminate a lot of problems for yourself if you stick to that.
* Especially no spaces. Spaces in filenames are allowed, but they cause all kinds of complications. We'll teach you how to handle those complications later, but it's still a good idea to leave out spaces. You can use underscores, dashes, or CamelCase instead of spaces. (CamelCase is capitalizing the first letter of each word instead of having spaces. SupposedlyTheCapitalsInCamelCaseLookLikeTheHumpsOfACamel.)

Now that we've had a long digression about file naming, let's have some more directory practice. We've changed directories and we've created them. And if you're following along, you should now be in "`~/directory_one`". (The directory called "directory_one" inside your home directory.)

We're going to use the "ls" tool to list the contents of the directories that we create. Let's make some more directories! First let's prove to ourselves that directories are case sensitive.

```bash
ubuntu@completegeek:~/directory_one$ mkdir Apples
ubuntu@completegeek:~/directory_one$ mkdir apples
ubuntu@completegeek:~/directory_one$ ls
Apples  apples
ubuntu@completegeek:~/directory_one$ cd Apples
ubuntu@completegeek:~/directory_one/Apples$ pwd
/home/ubuntu/directory_one/Apples
ubuntu@completegeek:~/directory_one/Apples$ cd ..
ubuntu@completegeek:~/directory_one$ cd apples
ubuntu@completegeek:~/directory_one/apples$ pwd
/home/ubuntu/directory_one/apples
ubuntu@completegeek:~/directory_one/apples$
```

Did you catch the new thing I threw in there? Yep, it's the "`..`" shortcut! ".." refers to the **parent directory** of the current directory. So typing "`cd ..`" will get you to a **different place** depending on where you are in the directory structure when you type it.

If you're in the "`/home/ubuntu/directory_one/Apples`" directory, typing "`cd ..`" will take you to the "`/home/ubuntu/directory_one`" directory. If you're in "`/home/ubuntu/directory_one`", typing "`cd ..`" will take you to your home directory.

Now let's clean up some of what we've created. Change to your home directory (either "`/home/ubuntu`" or "`/home/vagrant`") and type "`rmdir directory_one`". It didn't work! Why?

```bash
ubuntu@completegeek:~$ rmdir directory_one
rmdir: failed to remove 'directory_one': Directory not empty
ubuntu@completegeek:~$ ls
directory_one
ubuntu@completegeek:~$ cd directory_one/
ubuntu@completegeek:~/directory_one$ ls
Apples  apples
ubuntu@completegeek:~/directory_one$
```

That's right! As a safety measure, rmdir will refuse to remove any directory that isn't empty. So before you can remove "`directory_one`", you'll need to remove "`Apples`" and "`apples`".

```bash
ubuntu@completegeek:~$ ls
directory_one
ubuntu@completegeek:~$ cd directory_one/
ubuntu@completegeek:~/directory_one$ ls
Apples  apples
ubuntu@completegeek:~/directory_one$ rmdir Apples
ubuntu@completegeek:~/directory_one$ ls
apples
ubuntu@completegeek:~/directory_one$ rmdir apples
ubuntu@completegeek:~/directory_one$ ls
ubuntu@completegeek:~/directory_one$ cd ..
ubuntu@completegeek:~$ rmdir directory_one
ubuntu@completegeek:~$ ls
ubuntu@completegeek:~$
```

This is a good opportunity to talk about a part of the Unix/Linux philosophy -- the value of being terse.

When you try to rmdir a directory that has contents (or a directory that does not exist), rmdir will print out an error telling you to the best of its ability what went wrong. (Error messages in every operating system and programming language can often be vague and infuriating, but that's a separate topic.)

But when rmdir successfully removes a directory, it doesn't say anything. Same for cd and ls. When you change to a directory, cd doesn't say "Successfully changed to directory foo." It just does it.

This is because Unix tools are designed to be chained together -- to have the output of one command fed into the input of another command. For instance, (we'll cover this in detail later) you can pipe the output of "ls" to an application that sorts that output, and then to another application that counts the number of lines and outputs that. This is an incredibly powerful tool that you can use to do amazing things -- but it can seem deliberately obtuse and annoying at first.

If your commands and programs had to filter out all the "success" and "ok" messages, it would get complicated pretty quickly. Instead you get "just the facts" and only have to deal with errors.

To recap, when things go well, Unix tools don't tell you anything. (With exceptions like ls, where telling you something is part of their job.) Unix tools only get verbose when things go wrong.

## CHECKPOINT 2: Creating, listing, changing, and removing directories

All the following operations will be done in your home directory.

1. Create a directory called "plants" in your home directory.
1. Create a directory called "trees" inside the "plants" directory.
1. Create a directory called "vegetables" inside the "plants" directory.
1. Create a directory called "potatoes" in the "vegetables" directory.
1. Create a directory called "carrots" in the "vegetables" directory.
1. Change to the "vegetables" directory and use "ls" to see what is in there.
1. Create a directory called "douglas_fir" in the "trees" directory.
1. Create a directory called "Douglas_Fir" in the "trees" directory.
1. Create a directory called "oak" in the "trees" directory.
1. Use "ls" to see what is in the "trees" directory.
1. Attempt to remove the "trees" directory. This should fail. Why does it fail?
1. Take the steps necessary to successfully remove the "trees" directory.
1. Change to the "carrots" directory. What are the two actions you could take to verify what directory you are in? Do them.
1. Take the steps necessary to remove the "plants" directory from your home directory.
1. Why do Unix commands not output success messages?

We do not include answers to the checkpoint questions, but every bit of information you need to successfully complete them is in this chapter. Reread it if you're unable to complete any.

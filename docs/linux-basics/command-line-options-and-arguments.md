# Command-Line Options and Arguments

Almost every Linux command-line program is controlled by command-line options and arguments. How? By putting those arguments and options on the command-line after the name of the program, and hitting ENTER.

The other way programs are configured is by configuration files -- plain-text files, written in a format that the program understands, that it reads to see what it's supposed to do. We'll deal with configuration files in a later chapter.

Some of this can get kind of complex, so don't worry if you don't remember everything. (You should be taking notes, though!) The very next chapter is all about getting help when you forget to do something.

Let's start out by looking at some options to the `ls` program we've been using to look at the contents of directories.

If you just type `ls` with no options, and hit enter, `ls` will list the contents of the current directory.

```bash
ubuntu@completegeek:~$ ls
absolute1 relative1  relative2  relative3
ubuntu@completegeek:~$
```

NOTE: I still have some directories in my home folder from the previous chapter. It's a good idea to clear that stuff out at the beginning of each new chapter. Go ahead and do that before you proceed.

With command-line options you can change how `ls` behaves. There's four options I use regularly with `ls`:

* `-a` or `--all`: Show all files, including those starting with a period.
* `-h` or `--human-readable`: Instead of showing the raw number of bytes, show file sizes in a human-friendly format (4k, 1G, etc.)
* `-l`: Show a long listing. (That's a lower-case "L," not a "1" or an "I.") This shows you much more information about each file and directory.
* `-F` or `--classify`: Put a character at the end of some file names to indicate what they are. Executable files (programs) get an `*`, directories get a `/`,

Note that most options have a single-letter version (proceeded by a single dash) and a longer version (proceeded by a double-dash). They're interchangeable -- using the short or long version of an option has exactly the same effect.

So, the most verbose way of using those options would be:

```bash
ls --all --human-readable -l --classify
```

Sometimes (particularly when you're writing options in a script instead of typing them on the command-line) you'll use the long versions for clarity. Most of the time when you're typing on the command-line though, you'll use the short versions. Here's what that would look like:

```bash
ls -a -h -l -F
```

Because **all** short options are only one character long, you can chain them together with only one dash in front of them. This is how most people type them on the command-line:

```bash
ls -ahlF
```

Note that the order of the short options does not matter -- `-Flah` is the same as `-halF`.

Now let's add an argument in there:

```bash
ls -Flah /var/log
```

While options change **how** the program works, arguments generally are used to tell it **what to work on.**

We used the standard `-Flah` that you're used to, but we added an *argument* -- the directory that we wish to run `ls` on. In this case, `/var/log`.

Let's go over some options and arguments for the `mkdir` command:

* `-p` or `--parents`: Normally if you try to create a directory inside a directory that doesn't exist, mkdir will give you an error. With the `-p` option, it will try to create that "parent" directory instead of giving you an error.
* `-v` or `--verbose`: Prints a message for each directory it creates, instead of just doing it silently.

Many programs have a `--verbose` option, and it's often useful when trying to figure out why a program isn't doing what you think it should be doing.

So `mkdir` has optional options (and yes, there are mandatory options we'll cover later) and at least one required argument. If you don't tell mkdir what directories to create, it can't create them. You can give `mkdir` more than one argument, though! If you give it multiple arguments separated by spaces, it will create directories for all of them.

For `ls` on the other hand, the options are optional **and** the argument is optional -- if you leave off the argument, `ls` will just show you the contents of the current directory.

```bash
ubuntu@completegeek:~$ ls
ubuntu@completegeek:~$ pwd
/home/ubuntu
ubuntu@completegeek:~$ mkdir foobar/potato
mkdir: cannot create directory ‘foobar/potato’: No such file or directory
ubuntu@completegeek:~$ mkdir -pv foobar/potato
mkdir: created directory 'foobar'
mkdir: created directory 'foobar/potato'
ubuntu@completegeek:~$ ls
foobar
ubuntu@completegeek:~$ ls -Flah foobar/
total 12K
drwxrwxr-x 3 ubuntu ubuntu 4.0K Feb  7 15:23 ./
drwxr-x--- 5 ubuntu ubuntu 4.0K Feb  7 15:23 ../
drwxrwxr-x 2 ubuntu ubuntu 4.0K Feb  7 15:23 potato/
ubuntu@completegeek:~$
```

## CHECKPOINT: Options and Arguments

1. Inside your home directory, create a directory "peach" with the directory "eggplant" inside it. Use only one command.
2. Without changing directories, list all of the contents of the eggplant directory, including file sizes. Use only one command.
3. In the command `touch testfile.txt`, is "testfile.txt" an option or an argument? Why?
4. In only one command, list the contents of the `/etc` directory, including showing the classification of each file and directory in the `/etc` folder.
5. In the command you used to answer #4, what was an option and what was an argument?
6. In your home directory, using one command only, create the directory "apple" and the directory "sauce" inside "apple," and create the "grape" directory with the directory "juice" inside "grape."

# Getting Help

Nobody remembers everything. No matter how much you study this information, you'll forget some (most?) of it. What's important is to remember that the information exists, and be able to find it again. That includes this chapter -- you won't remember all of it, but please keep it handy so you can refer back to it.

I'd strongly recommend you take ongoing notes about what you're learning, in a way that works for you -- a text file, a notes app, paper and pencil -- but take notes. This will be your first resource.

We'll be learning about how to get help with Unix commands and programs, but by necessity we'll also be reviewing what we learned in the last chapter about the structure of commands, and how you run programs. This is another absolutely vital foundational skill you'll need throughout your career ... noticing a theme? This volume of the guide is all about foundational skills and knowledge you'll use for your entire career.

## "man" Pages

Man is short for "manual" by the way. Back in the early days when Unix and these applications were first written, memory and disk space was limited and expensive. The three letters "man" saves from "manual" made a difference.

These man pages are documentation pages that come with your operating system or the applications you install. (A properly written Linux/Unix application should also install man pages when you install the application.)

Man pages can be difficult to read, and reading them is definitely a skill that you'll need to learn. They're generally accurate, but often not very helpful. I've often found myself solving a problem with a program in some other way (Google, etc.) and then once I understand the solution, I re-read the man page only to discover that the answer was there all along, I just didn't understand it. (Or the correct answer was implied instead of stated outright.)

To read man pages, we'll use the man application. After the name of the man application, you'll include as an *argument* the name of the program you want information about. (We'll cover arguments in more depth later in this chapter.)

So, to read the manual page for the "touch" application, you'd issue the following command:

```bash
man touch
```

(There's obvious puns here, but I'm choosing not to perpetuate Unix's culture of bad dad jokes.)

Let's look at the man page for touch, piece by piece, as most man pages are structured the same.

### Man Page Header

First, there's the header:

```bash
TOUCH(1)                 User Commands                TOUCH(1)

NAME
       touch - change file timestamps
```

The header tells us this is the "touch" command. The number in parenthesis tells us what man section we're in (1) and that this is a user command. (Intended to be run by users such as us.) There are other man sections; we'll talk about them shortly. Under NAME it gives us the program name and a very brief description of what it does. As you'll see further on, it's not a very good description.

### Man Page Synopsis

Next we come to the synopsis. This gives us a very brief summary of the touch command and its options and arguments.

```bash
SYNOPSIS
       touch [OPTION]... FILE...
```

This tells us that to use the touch command, you type "touch," then include the options you want. The ellipsis after [OPTION] tells us that you can use more than one option. The fact that "OPTION" is in brackets means these options are optional -- you don't have to include any option at all. (And yes, before you ask, there are non-optional options. Don't hate me.)

Then you need to include the names of at least one file. This is considered an "argument," not an option, because you're not changing the way a program works like an option does -- you're just giving it an argument to take action on. The ellipsis tells us that we can include more than one file. And the fact that FILE is *not* in brackets means that it is *not* optional -- we must specify at least one file name.

### Man Page Description

The description gives a more detailed explanation of what the program does, along with details on all the optional options and mandatory options and arguments.

So reading the description it looks like `touch` will update the access and modification times of each file.

But the second line tells us that touch will create the file if it doesn't exist. This is 98% of the usage of touch in my experience -- it's only in very special cases that we'll want to change the date on a file, but it's common to want to create one.

Then there's a little bit of awkward poetry: `"Mandatory arguments to long options are mandatory for short options too."` We'll explain that in a bit.

Let's look at some of the options:

`-a` means that touch will change only the access time. (Remember that the first line of the description is that touch updates the access **and** modification times of each file.)

`-c` means that, even if touch would otherwise create a file, it won't do that. `-c` is the short version of the option. You could also write `--no-create` and it would accomplish the same thing. That's the long version of the option.

Short options can be joined together. You don't have to write `-c -a`, you can just write `-ca` and it will have the same effect.

Long options have two dashes in front of them so they can be distinguished from short options that are joined together.

In addition to the arguments we've already discussed, for example putting a filename in a `touch` command to tell it what file to "touch," options can have arguments too. Look at the --date option.

Instead of using the current time and date, the --date option causes touch to use whatever date and time you specify. The "STRING" that you specify is the option's argument -- the date to use.

```bash
ubuntu@completegeek:~$ touch file1
ubuntu@completegeek:~$ touch --date="2021-01-01" file2
ubuntu@completegeek:~$ touch -d "2022-12-31" file3
ubuntu@completegeek:~$ touch -d file4
touch: invalid date format ‘file4’
ubuntu@completegeek:~$ ls -l
total 0
-rw-rw-r-- 1 ubuntu ubuntu 0 Feb 14 15:12 file1
-rw-rw-r-- 1 ubuntu ubuntu 0 Jan  1  2021 file2
-rw-rw-r-- 1 ubuntu ubuntu 0 Dec 31  2022 file3
ubuntu@completegeek:~$
```

We just ran `touch file` and it created `file` with today's date and the current time. OK, just as we expect.

Next, let's specify New Year's Day 2021 -- we put that as an argument to the `--date` option when we created `file2`.

We used the last day in 2022 as the date for file3. Note that the long option uses an equal sign, but the short option uses a space. I'm honestly not really sure why.

As our little poem said, mandatory arguments to long options are also mandatory for short options. If we try the -d option without the mandatory argument, it complains, because it thinks the `file4` is actually the date, and that doesn't make sense.

## Additional man page sections

Here we have an additional, and quite helpful section, "DATE STRING," that is not in every man page; this is specific to touch. DATE STRING explains exactly how to write a date string that `touch` will understand. Then we have author copyright, and bug reporting sections, all of which are fairly self-explanatory.

## Navigating around in man pages

The touch man page is fairly short, but some man pages are very long. The `find` man page is 1302 lines long.

Go ahead and open the `find` man page, and I'll give you some keystrokes you can use to move around in that man page.

* `G`: Move to the end of the man page
* `g`: Move to the beginning of the man page
* [space]: Scroll down one screen of text
* `/`: Search for text.
* `q`: Exit the man page
* `n`: Go to the next search match (the match is on the top line of the screen)
* `N`: Go to the previous search match

Search may be a little confusing, so I'll walk you through a simple search:

1. Hit `g` to move to the start of the man page
2. Hit `/` to start searching
3. Type `delete` and hit `[ENTER]` to search for "delete."
4. Hit `n` to go to the next search match or `n` to go to the previous.

Now I'll tell you the **best** news about these keystrokes. They're absolutely the same when you're viewing files in `less`. They're even the same keystrokes you'll use when you're editing files in `vi.` This is the essence of why I love Linux -- you build up skills in one place that you can leverage in a bunch of other places!

## Man page sections

Man pages are divided up into 8 sections, to make it easier to find specifically what you're looking for. And of course, you can see a list of those sections by typing `man man-pages`:

Section 1 is user commands. What we've been dealing with so far. Commands a normal user can use.

Sections 2, 3, 4, and 5 are useful only when you're programming -- you won't spend much time there in this volume.

Sections 6 and 7 are pretty self-explanatory.

Section 8 is for system-administration commands. You'll use these commands when you put on your "system administrator" hat, which you'll do fairly often.

So if you do `man ls` you'll see it's in section 1, as you'd expect.

The command you use to shut down a computer, halt, is in section 8: `man halt`.

What if a command is in multiple sections? You can specify the section as an option to man:

```bash
ubuntu@completegeek:~$ man hd
ubuntu@completegeek:~$ man 1 hd
ubuntu@completegeek:~$ man 4 hd
```

The commands `man hd` and `man 1 hd` get you the same results, because `man` defaults to section 1. There's an entirely different man page for `hd` in section 4, though, which the third command shows you.

Not all man page sections are installed in Ubuntu by default.

## Apropos

You can use the `apropos` command to search through man pages to find something. (The `apropos` command is based on [the word "apropos."](https://www.merriam-webster.com/dictionary/apropos) You don't pronounce the "s.")

Let's say you want to run the `ls` command to list directory contents, but you don't remember the command to do that. As long as you remember that you're trying to "list" directory contents, you can get there.

```bash
apropos -s 1 list
```

You could leave out the "-s" option and it's argument, but it makes sense to limit the search to section 1. You'll get about 38 man pages, with "ls" right there in the middle.

You can list all installed man pages from a particular section with `apropos -s 2 .` (The dot means "show me everything". )

## Info pages

Linux and Unix were built by lots of different people over decades. One group of folks who contributed a lot to Linux are the [GNU](https://www.gnu.org/home.en.html) team. These very talented programmers decided that man pages weren't good enough for them, so they invented "info" pages. It's an entirely different way of getting help than man pages, that (to me) is harder to use than man pages. ([Not that I'm bitter](https://www.reddit.com/r/linuxadmin/comments/27dxrr/does_anybody_use_gnu_info/) about this choice.) Still, you'll need to know the basics of info pages.

If you take a look at the bottom of the `ls` man page, it directs you to use `info` instead for full details. You'll see a lot of notes like that in man pages for tools built by the GNU team.

```BASH
SEE ALSO
       Full documentation <https://www.gnu.org/software/coreutils/ls>
       or available locally via: info '(coreutils) ls invocation'
```

The command `info '(coreutils) ls invocation'` that they suggest will work, but the simpler `info ls` will work too.

Info is actually super complex and powerful, but we're going to focus on just the basics:

* `[BACKSPACE]` and `[SPACE]`: Scroll up and down by screen
* `[HOME]` and `[END]`: Scroll to the top or bottom of a section (they call it a node)
* `n` and `p`: Go to the next or prevous node in the current level.

Go ahead and play with those.


## More help

These days doing a web search is probably the first move for a lot of people (even before man pages). Searching for error messages is a great tool for troubleshooting. You'll get lots of practice searching as you go through this course. Try and make your searches specific -- you'll get much more relevant results by searching for "how to use **gnu** info pages" instead of "how to use info pages."

You should refer back to this section next time you're figuring out a problem and try some of the resources below -- they've got pretty reliable info without a bunch of spammy ads or popups.

* [The Linux Documentation Project (TLDP)](https://tldp.org) is a pretty awesome resource. I end up searching it quite a bit.
* The [NixCraft](https://www.cyberciti.biz) article site has a lot of good articles on basic Linux stuff.
* The cloud company [DigitalOcean](https://www.digitalocean.com) has a lot of good documentation that doesn't just apply to their services. I'll often try a search for "digitalocean THING" instead of just "THING." I know I'll get something that's pretty accurate and up-to-date. For instance, "digitalocean apache" got me a good page on installing Apache on Ubuntu. (Apache is a web server. We'll talk more about that later.)


## CHECKPOINT: Getting Help

1. Should you be taking notes, in whatever way is most comfortable for you?
2. Look up something in those notes. I'll wait.
3. I know you probably weren't taking notes. But you should really start!
4. Is there a short version of the `ls` option `--author`?
5. Who wrote the `printf` application?
6. The `mkdir` man page shows you **two** other ways you can get help on `mkdir.` One of them is the info pages we talked about. What's the other?
7. How should you report any bugs you find in the `find` program?
8. The `date` command displays the current date. But it can also display any date you tell it to. Have it display the date on the West Coast of the USA (Pacific time zone) for next Tuesday at 4 PM.

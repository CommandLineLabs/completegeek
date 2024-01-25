# Getting Help

Nobody remembers everything. No matter how much you study this information, you'll forget some (most) of it. What's important is to remember that the information exists, and be able to find it again.

I'd strongly recommend you take ongoing notes about what you're learning, in a way that works for you -- a text file, a notes app, paper and pencil -- but take notes. This will be your first resource.

We'll be learning about how to get help with Unix commands and programs, but by necessity we'll also be learning about the structure of commands, and how you run programs. This is another absolutely vital foundational skill you'll need throughout your career ... noticing a theme? This volume of the guide is all about foundational skills and knowledge you'll use for your entire career.

## "man" Pages

Man is short for "manual" by the way. Back in the early days when Unix and these applications were first written, memory and These are documentation pages that come with your operating system or the applications you install. (A properly written Linux/Unix application should also install man pages when you install the application.)

Man pages can be difficult to read, and reading them is definitely a skill that you'll need to learn. They're generally accurate, but often not very helpful. I've often found myself solving a problem with a program in some other way (Google, etc.) and then once I understand the solution, I re-read the man page only to discover that the answer was there all along, I just didn't understand it. (Or the correct answer was implied instead of stated outright.)

To read man pages, we'll use the man application. After the name of the man application, you'll include as an *argument* the name of the program you want information about. (We'll cover arguments in more depth later in this chapter.)

So, to read the manual page for the "touch" application, you'd issue the following command:

```bash
man touch
```

(There's obvious puns here, but I'm choosing not to perpetuate Unix's culture of bad dad jokes.)

Let's look at the man page for touch, piece by piece, as all man pages are structured mostly the same.

### Man Page Header

First, there's the header:

```man
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

This tells us that to use the touch command, you type "touch," then include the options you want. The ellipsis after [OPTION] tells us that you can use more than one option. The fact that "OPTION" is in brackets means these options are optional -- you don't have to include them at all. (And yes, before you ask, there are non-optional options. Don't ask me.)

Then you need to include the names of at least one file. This is considered an "argument," not an option, because you're not changing the way a program works like an options does -- you're just giving it an argument to take action on. The ellipsis tells us that we can include more than one file. And the fact that FILE is *not* in brackets means that it is *not* optional -- we must specify at least one file name.

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

-----------------------------
Reading man pages

Man page sections

arguments and options to commands
mandatory and optional options

--help and -h

-v and -vvvv and --verbose

apropos

Fucking info

TLDP and web pages in general

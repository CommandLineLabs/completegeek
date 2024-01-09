# Complete Geek Guide Master Outline

## Volume 1: Linux, the Command-Line, and BASH Scripting

* [Introduction](../README.md)
* [Chapter 1: Getting Started](./001-getting-started.md)
* [Chapter 2: Making, Removing, and Changing Directories](./002-directories.md)
* [Chapter 3: Linux History, Philosophy, and Benefits](./003-operating-systems-and-history.md)

## Chapter x

How to get help. Man pages, TLDP, other resources. Fucking info pages.

## Chapter x

Let's learn about absolute versus relative paths

## Chapter x

Let's learn about making files and looking at directory entries.

* touch a file
* Let's edit some files with nano
* moving and renaming files
* There's no such thing as renaming, just use mv.
* cp
* rm (the buzzsaw of unix)
    * Use the "everyone who uses a table saw long enough loses a finger" analogy for rm.

## Chapter 8

Let's learn about permissions and ownership -- how to read them, how to set them. Numeric and Symbolic.

## Chapter 10

Nano is for newbs. Let's learn some vim.
Why you need to know vim (it's everywhere)

## Chapter XX -- Everything is a file

* Valid Filenames
* Wildcards
* Devices
* Filesystems

## Weird Permissions

* SetUID
* SetGID
* Sticky

## Hard links and soft links

## Processes

* ps
* top
* proc

## Redirection and Pipes

This is the hidden strength of Linux.
cat
>
>>
Herefiles
STDIN, STDOUT, STDERR

## Putting processes together in complex pipelines

cat $FOOFILE | sort | uniq | wc -l
etc.

## The find program and how awesome it is

## Sed and AWK

## Regular Expressions

## One-liners you should remember or keep in a text file so you can cut and paste easily

* Remove empty directories under the current directory
* Infinite loops

## simple Bash Scripting

* Shebang line
* Making scripts executable
* if then else statements
* Exit statements and return codes
* Different Shells -- bash vs sh vs zsh, etc
* Variables and quoting in shells
* conditional execution and loops
* grouping commands
* aliases and functions

## Advanced bash scripting

Prompting for input

## Dotfiles

## Volume 2: Websites and Networking

## Chapter x -- Creating a Droplet

If you know what you're doing you can create a virtual machine on any service, or even create a VM on your laptop if it supports that. However, I'll just walk you through creating one on Digital Ocean.

... steps and screenshots for creating a droplet

... including the basics of strong passwords and why you should have strong passwords

## Chapter x

Opening the terminal and SSHing to your droplet
Now that you know about directories, files, and permissions, let's set up SSH Key login instead of password login.

## Technical Skills Future Outline

### System Administration / Automation / DevOps / SRE

* The Practice of System and Network Administration
* The Practice of Cloud System Administration
* Site Reliability Engineering

### Methodologies, Philosophies, and Buzzwords

* Waterfall
* Agile
* etc.

### Version Control

* Brief history of version control from vcs to svn to git and how we created decentralized version control with git and then re-centralized it with GitHub.
* Git.
* Github.
* Writing good commit messages and good pull request messages

### Security and Encryption

* Basics of security on the desktop
* Basics of security on the phone
* Auth including 2-factor auth
* ssh, including setting up ssh keys and ssh key auth
* ssh server configuration
* Basics of setting up a secure Linux server
* Basics of setting up a secure Windows server (if studying Windows)
* FIXME(schof): This can go a lot deeper, both on technical issues and on security as a career.

### Open Source Concepts

### Technical Writing

* Writing Documentation
    * Documentation is not something you do AFTER you finish the job. Documentation is PART of finishing the job.
* Writing good comments

### Configuration Management (Pick one; study more later.)

* Ansible
* Puppet

### Networking

* You must have an understanding of basic networking, including (incomplete and in no particular order): DHCP, DNS, NAT, network troubleshooting tools and methodology, routing, etc. You should understand what's actually going on in your home router / access point.
* There is almost no limit to how deeply you can study networking. Whether or not you make networking your career, getting better at networking will make you better at almost every technical field.
* You can self-study or there are are clearly-defined and widely-recognized study paths and certifications (CCNA, CCNP, CCIE, etc.)

### Cloud Environment (Pick one; study more later.)

* AWS
* OpenStack
* Google Cloud
* Microsoft Azure

## Non-Technical Job Skills

* Communication
* Writing well
* Hiring and interviews
* Negotiating for compensation

## Business and Management Skills

* [Joel on Software](https://www.amazon.com/Joel-Software-Occasionally-Developers-Designers/dp/1590593898)
* [More Joel On Software](https://www.amazon.com/More-Joel-Software-Occasionally-Developers/dp/1430209879)
* [Mythical Man-Month](https://www.amazon.com/Mythical-Man-Month-Software-Engineering-Anniversary/dp/0201835959/ref=sr_1_1?crid=62GZK0EBAMWG) The original "you can't get a baby in one month by getting nine women pregnant" book.
* Managing Humans by Michael Lopp

## Financial Skills

### Personal Finance & Investing

* [A Random Walk Down Wall Street](https://www.amazon.com/Random-Walk-Down-Wall-Street/dp/0393358380)
* [The Investor's Manifesto](https://www.amazon.com/Investors-Manifesto-Prosperity-Armageddon-Everything-ebook/dp/B002U3CBY8) and EVERY book by William J. Bernstein.
* The Millionaire Next Door
* The Richest Man in Babylon

## Life Skills

* Getting Things Done (GTD)

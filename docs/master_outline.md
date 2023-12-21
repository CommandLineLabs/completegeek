# Complete Geek Master Outline

## Introduction and Pre-Requisites

This document will lead you from not much to complete mastery. Unfortunately, this will cost you some money. I've tried to keep the expense minimal, but it's not zero. Even minimal is a bit of a joke, because you'll need a Mac or Windows laptop, which is definitely not minimal.

You should read through each chapter, and then try the exercises in each chapter. If you can't make the exercises work, re-read the chapter. Do not continue unless you've groked the material in the chapter. Every chapter in this book builds on previous chapters, and you can't skip anything.

### Hardware

Yep, you'll need a laptop or desktop computer, or regular access to one. This book is written assuming you have a Mac OS X computer. I'll later add support for Windows computers and Chromebooks. There's not much to do getting around that, but I'll try to add some scholarship options later for people who can't afford their own laptop.

### Software (Installed on your computer)

You'll need a web browser (which is free).

You'll need a terminal program, which you'll use to type commands to your computer and to other computers. This comes built-in on an OS X computer, and is a free download on a Windows computer.

You'll need password-management software. I use [1Password](https://1password.com), which costs (as of December 2022) $2.99 monthly. An alternative is [LastPass](https://www.lastpass.com) which I don't like as much as 1Password, but has the advantage of being free.

### Online Services

You'll need to pay for a Droplet (a virtual machine) on Digital Ocean or another service. I'll walk you through this later, but it will cost you about $4.00 a month for this.

### Skills

I'll teach you everything you need to know about Linux, but you'll need to be at least competent at using a Mac or Windows computer. Teaching you that is out of scope for this book, but I hope to provide references for this in the future.

## Chapter 0 -- Why Linux?

The knowledge and skills don't go stale.

## Chapter 1 -- Creating a Droplet

If you know what you're doing you can create a virtual machine on any service, or even create a VM on your laptop if it supports that. However, I'll just walk you through creating one on Digital Ocean.

... steps and screenshots for creating a droplet

... including the basics of strong passwords and why you should have strong passwords

## Chapter 2

Opening the terminal and SSHing to your droplet

## Chapter 3

Let's learn about making directories, changing directories, seeing what directory you're in, and removing directories.

## Chapter 4

Let's learn about making files and looking at directory entries.

## Chapter 5

Let's learn about absolute versus relative paths

## Chapter 6

Let's edit some files with nano

## Chapter 7

Let's digress a bit into the history of Linux and Unix as a multi-user operating system.

## Chapter 8

Let's learn about permissions and ownership -- how to read them, how to set them. Numeric and Symbolic.

## Chapter 9

Now that you know about directories, files, and permissions, let's set up SSH Key login instead of password login.

## Chapter 10

Nano is for newbs. Let's learn some vim.

## Chapter 11

How to get help. Man pages, TLDP, other resources. Fucking info pages.

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

## Unix grew, it wasn't designed

Individual parts of it were designed, but the whole came together organically. THis is why lots of stuff isn't consistent and doesn't make sense.

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

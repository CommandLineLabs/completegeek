# Chapter 1: Getting Started

## Introduction

The first thing that we're going to learn involves the Linux command-line. We'll be studying Linux and Unix operating systems as the foundation for everything else that we're learning.

To do that, and to ensure that we have a consistent environment for everyone, we'll be installing a virtual machine on your laptop. That virtual machine will be running Ubuntu Linux. (There are other varieties of Linux and Unix that we'll cover later. For now, we'll focus on Ubuntu.)

What is a virtual machine (VM)? It's a program that runs on your laptop that *pretends* that it's an entire computer. To understand that, we'll need to understand a little bit about the parts a non-virtual computer has.

Your laptop has a few important parts:

* It has a **CPU**: The thing that actually does all the processing (following instructions that you or someone else wrote)
* It has a **GPU**: A specialized type of CPU intended to be used for complicated graphics (and now often used for crypto or AI calculations)
* It has a **display**: A screen that lets you see what's going on
* It has **RAM**: Short-term memory that the CPU uses as kind of a scratch-pad. It gets erased every time you turn off or reboot your computer
* It has **long-term storage**, either a **hard drive** or an **SSD**: This is a place for your CPU to write data, that lasts even when the computer is turned off or rebooted. It's where programs are installed, and your Word or Excel documents are saved.

A virtual machine pretends that it has all those parts -- it has parts that pretend to be a CPU, pretend to be a display, pretend to be RAM, etc. You can install a brand-new operating system on it (different from what's running on your laptop) and from the point of view of that virtualized operating system, it thinks it's running on a regular computer. It doesn't necessarily know that it's on a VM. This provides us an easy and cheap way of accessing a Linux VM. Plus, if you mess something up, it's really easy to delete the VM and start over!

We'll eventually use VM's hosted in the cloud, such as on Amazon AWS or Digital Ocean, but at first, we're going to do VMs on your laptop or desktop.

Now we'll need to go through the process of installing some VM software and installing an operating system. By the end of this chapter, you should be able to log into the virtualized Ubuntu operating system we'll install.

What follows is instructions for setting up a VM on both Windows and MacOS. You'll do *one* of those, depending on which type of laptop you have. You don't need to do both.

## Setting up a virtual machine on a MacOS (Apple) computer

You'll need to install VirtualBox, which is a free virtual machine program. There are other virtual machine programs you can use that will work just fine, but the only one we'll walk you through is VirtualBox.

Older MacOS computers have CPU chips made by Intel. Newer MacOS computers (those released since roughly 2020) have a M1 or M2 CPU based on ARM processors and made by Apple. The two types of chip are not compatible with each other.

You can tell what kind of chip your MacOS computer is based on by clicking the Apple icon in the upper left-hand corner of your screen, and then clicking "About this Mac." You'll see a line titled either "Chip" or "Processor."

To the right of "Chip" or "Processor" it will say either "Apple M1 Max" (or Apple M1- or M2-anything) if you have an ARM-based Mac. It will say "Intel" somewhere in the line if you have an Intel-based Mac. For instance, my Intel MacBook Pro says, "2.5 GHz Quad-Core Intel Core i7." Yours will probably say different stuff, but if it includes "Intel," it's an Intel-based Mac.

### On Intel-Based Macs

First, we'll need to install the VM software. For Intel-based Macs, we're going to install virtual machine software called VirtualBox. This is the software that "pretends" to be an actual physical computer for the virtual machines running on it. Go to the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads) and click the "MacOS / Intel hosts" link to download the installer.

Now run that downloaded installer and accept all the default choices.

Once VirtualBox is installed, we'll need to install Vagrant. Vagrant is a virtual machine automation tool that will make it very easy to for us to create virtual machines. Go to the [Vagrant download page](https://developer.hashicorp.com/vagrant/downloads) and scroll to "MacOS." You'll see two choices, "AMD64" or "ARM64." Click the "AMD64" download link to download the installer.

Run the installer and accept all the default choices. Once it's installed, you'll need to open up a terminal window. Start the "Terminal" application from inside the "/Applications/Utilities" folder. You should see a command prompt in a white window.

The prompt itself shows what directory you are in. For instance, when I started Command Prompt, my prompt was "`schof@intelmac ~ %`". The tilde ("~") means I'm in my home directory. Your prompt will be somewhat different. You'll use the following commands to see directory contents and change directories:

* `ls[ENTER]` -- shows you the contents of a directory
* `cd DIRECTORY_NAME[ENTER]` -- changes to a different directory
* `cd ..[ENTER]` -- goes up one directory level
* `mkdir DIRECTORY_NAME[ENTER]` -- creates a directory
* `pwd[ENTER]` -- print out the full name of the current directory

I decided to keep my virtual machine files in my Documents folder, so I typed "`cd Documents`" and hit ENTER. My prompt changed to be "`schof@intelmac Documents %`" which is how I know it worked.

In the Documents folder I created a directory called "completegeek_vm" and then changed to the completegeek_vm directory:

```bash
mkdir completegeek_vm
cd completegeek_vm
```

You'll know you've done this correctly when your command prompt includes:
`completegeek_vm`. (Of course, yours will be slightly different depending on your name.) To check that I did everything correctly, I entered the "`pwd`" command to see what directory I am in:

```bash
schof@intelmac completegeek_vm % pwd
/Users/schof/Documents/completegeek_vm
schof@intelmac completegeek_vm %
```

Now that we're in the correct directory, we'll type the following command (after every command you'll hit [ENTER]) to create a virtual machine:

`vagrant init ubuntu/jammy64`

This should give you a message that "A Vagrantfile has been placed in this directory."

The Vagrantfile is the configuration file for your VM. Now you actually need to create your virtual machine. To do that, you'll type:

`vagrant up`

You'll see some status messages print on your screen. The "Downloading" part may take a while depending on how fast your Internet connection is.

Once that's completed, you've built your first VM! **To connect to it at any time in the future,** you'll change directories to your completegeek_vm directory(if necessary), and issue the command "vagrant ssh":

```bash
cd ~/Documents/completegeek_vm
vagrant ssh
```

You should now see a welcome message on the screen, and at the bottom you should see a new command-prompt, in green, that says, "`vagrant@ubuntu-jammy:~$`".

To exit the VM, type "`exit`" and hit ENTER. After you've done that, you can shut down the VM by typing "`vagrant halt`" and hitting ENTER.

You can start up the VM again any time you want by first making sure you're in the completegeek_vm directory and then typing `vagrant up` again.

Now continue to CHECKPOINT 1 at the bottom of this page.

### On ARM-based Macs

If you have an ARM-based Mac, you'll need to install Ubuntu Multipass to get an Ubuntu Linux VM running. Go to the [Multipass download page](https://multipass.run/install) and click the "macOS" link. That will download the installer to your computer. Run the installer and click "Continue" to accept all the default choices.

Now open up a terminal window (start the "Terminal" application from inside the "/Applications/Utilities" folder). You should see a command prompt. Type the following command and hit [ENTER]:

```bash
multipass launch --name completegeek
```

You should see progress printing to the terminal window (this may take a while depending on how slow your Internet connection is).

Once that command completes, you'll need to double-click the "Multipass" application in your Applications folder. That will put the Multipass "M" icon in your menu bar at the top of the screen.

Click the M icon and then click "completegeek (running)" and then "Open Shell". This will open up a new terminal window with a green command prompt at the bottom reading "`ubuntu@completegeek:~$`". If it does, you've successfully started the VM and connected to it. To start and stop your VM, click the M icon, then "completegeek" and then either "Start" or "Stop."

Once you've stopped the VM (or any time you want), you can close the white Terminal windows it opened up.

Now continue to CHECKPOINT 1 at the bottom of this page.

## Setting up a virtual machine on a Windows computer

First, we'll need to install the VM software. For Windows, we're going to install virtual machine software called VirtualBox. This is the software that "pretends" to be an actual physical computer for the virtual machines running on it. Go to the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads) and click the "Windows hosts" link. This should download the installer for VirtualBox.

Run (Open) the installer, allow it to make changes to your device, and accept all the default choices (say "Yes" or "Next" to everything).

Once VirtualBox is installed, we'll need to install Vagrant. Vagrant is a virtual machine automation tool that will make it very easy to for us to create virtual machines. Go to the [Vagrant download page](https://developer.hashicorp.com/vagrant/downloads) and scroll to "Windows." You'll see two choices, "AMD64" or "i686."

AMD64 is for 64-bit computers with 64-bit operating systems, and i686 is for 32-bit computers with 32-bit operating systems. (Don't worry about what that means; we'll cover it later.) **Unless your computer is really old it almost certainly has a 64-bit operating system and computer, so use the AMD64 download link.**

If your computer is old, and you're not sure if it is 64-bit or 32-bit, Microsoft [wrote a page with instructions](https://support.microsoft.com/en-us/windows/32-bit-and-64-bit-windows-frequently-asked-questions-c6ca9541-8dce-4d48-0415-94a3faa2e13d) about how to find out.

Use whichever download link is appropriate for your system, and run (open) the installer. Click "Next or "Yes" to everything. You'll need to restart your computer after you finish running the installer.

After your computer reboots, you'll need to run the command prompt. Search for "cmd" and click the "Command Prompt" application.

Once you're in the "Command Prompt" application, you'll see a black screen with white text. This is the Windows version of the Linux command-line prompt. You type commands and hit enter to have your computer do things. All of this will make a lot more sense once we cover the Linux command-line, but unfortunately we kind of have to dump you in the deep end right now to get things going.

Our next step is to create our virtual machine files. You'll need to decide where to store them, and then navigate to where you want to keep them.

The prompt itself shows what directory you are in. For instance, when I started Command Prompt, my prompt was "`C:/Users/jms`". Yours will be different unless your initials are also "JMS." You'll use the following commands to see directory contents and change directories:

* `dir[ENTER]` -- shows you the contents of a directory
* `cd DIRECTORY_NAME[ENTER]` -- changes to a different directory
* `cd ..[ENTER]` -- goes up one directory level
* `mkdir DIRECTORY_NAME[ENTER]` -- creates a directory

I decided to keep my virtual machine files in my Documents folder, so I typed "`cd Documents`" and hit ENTER. My prompt changed to be "`C:/Users/jms/Documents`" which is how I know it worked.

In the Documents folder I created a directory called "completegeek_vm" and then changed to the completegeek_vm directory:

```bash
mkdir completegeek_vm
cd completegeek_vm
```

You'll know you've done this correctly when your command prompt says:
`C:\Users\jms\Documents\completegeek_vm`
(Of course, yours will be slightly different depending on your name.)

Now we'll type the following command (after every command you'll hit [ENTER]) to create a virtual machine:

`vagrant init ubuntu/jammy64`

This should give you a message that "A Vagrantfile has been placed in this directory."

The Vagrantfile is the configuration file for your VM. Now you actually need to create your virtual machine. To do that, you'll type:

`vagrant up`

You'll see some status messages print on your screen. The "Downloading" part may take a while depending on how fast your Internet connection is.

Once that's completed, you've built your first VM! **To connect to it at any time in the future,** you'll change directories to your completegeek_vm directory(if necessary), and issue the command "vagrant ssh":

```bash
cd C:\Users\jms\Documents\completegeek_vm
vagrant ssh
```

You should now see a welcome message on the screen, and at the bottom you should see a new command-prompt, in green, that says, "`vagrant@ubuntu-jammy:~$`".

To exit the VM, type "`exit`" and hit ENTER. After you've done that, you can shut down the VM by typing "`vagrant halt`" and hitting ENTER.

You can start up the VM again any time you want by first making sure you're in the completegeek_vm directory and then typing `vagrant up` again.

Now continue to CHECKPOINT 1 at the bottom of this page.

## CHECKPOINT 1: Verifying that your virtual machine is working properly

Now connect to your VM. (The method you use to connect will be different depending on if you're using Vagrant or a different tool.) Once, connected, you should be able to enter the following commands:

* `whoami` -- should show your user name (vagrant or ubuntu)
* `date` -- should show the current date and time (timezone will be UTC, not your local timezone)
* `uptime` -- should show the current time, and the number of minutes since you turned the VM on, as well as the number of users currently logged in (1) and the load average.

Here's an example of what that looked like for me:

```bash
vagrant@ubuntu-jammy:~$ whoami
vagrant
vagrant@ubuntu-jammy:~$ date
Thu Dec 21 19:54:49 UTC 2023
vagrant@ubuntu-jammy:~$ uptime
 19:55:18 up 6 min,  1 user,  load average: 0.01, 0.18, 0.12
vagrant@ubuntu-jammy:~$
```

If your output looks similar to mine, congratulations!

Now let's exit the VM. Type `exit` and hit ENTER.

Now shut down the VM. You've successfully created a VM, connected to it, and run some commands! You've passed Checkpoint 1. Go ahead and move on to Chapter 2. If you didn't pass the checkpoint, check your work or ask questions in the discussion group or in office hours.

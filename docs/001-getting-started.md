# Chapter 1: Getting Started

## Introduction

The first major subject that we're going to learn involves the Linux command-line. We'll be studying Linux and Unix operating systems as the foundation for everything else that we're learning in this course.

The reason that we're taking that approach is because Linux and Unix computers are the underpinning for almost everything that happens in the Internet. Facebook runs on Linux. Google runs on Linux. Your bank and insurance company run (at least partially) on Linux. It's the most common server operating system by a significant margin.

To do that, and to ensure that we have a consistent environment for all the students, we'll be installing a virtual machine on your laptop. That virtual machine will be running a type of Linux called "Ubuntu Server." (There are other varieties of Linux and Unix that we'll cover later. For now, we'll focus on Ubuntu.)

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

You'll need to install Ubuntu Multipass to get an Ubuntu Linux VM running on your Mac system. Go to the [Multipass download page](https://multipass.run/install) and click the "macOS" link. That will download the installer to your computer. Run the installer and click "Continue" to accept all the default choices.

Now open up a terminal window (start the "Terminal" application from inside the "/Applications/Utilities" folder). You should see a command prompt, something like "schof@testmac ~ %". (Your mac username, then "@", then the name of your your mac, then " ~ %".) This is the MacOS command prompt. You type commands and hit [ENTER] to have your computer do things. All of this will make a lot more sense once we cover the Linux command-line, but unfortunately we kind of have to dump you in the deep end right now to get things going.

Type the following command and hit [ENTER]:

```bash
multipass launch --name completegeek
```

This will create the completegeek Ubuntu VM.

You should see progress printing to the terminal window (this may take a while depending on how slow your Internet connection is).

Multipass should start printing some information to the Command Prompt about "Retrieving image." How long that takes depends on the speed of your Internet connection. It will then start the "completegeek" image. You'll know it's done when you see the prompt again at the bottom of the screen.

Next you'll need to double-click the "Multipass" application in your Applications folder. That will put the Multipass "M" icon in your menu bar at the top of the screen.

Click the M icon and then click "completegeek (running)" and then "Open Shell". This will open up a new terminal window with a green command prompt at the bottom reading "`ubuntu@completegeek:~$`". If it does, you've successfully started the VM and connected to it. You can also do that multiple times to open up multiple shells to the same VM.

To exit the VM, type "`exit`" and hit ENTER. You can then open another terminal window to the VM by clicking the M icon again.

To shutdown your VM, at the "`ubuntu@completegeek`" command prompt, enter the following command:

```bash
sudo shutdown -h now
```

Once you've stopped the VM (or really, any time you want), you can close the white Terminal window it opened up.

To start your VM in the future, click the M icon, then "completegeek" and then "Start."

To delete your VM entirely (for instance if you've messed it up or you're not sure where you got to in a series of commands and want a fresh start) then you'll need to go to the terminal shell (the same place where you typed in "`multipass launch...`"), **NOT** the shell you get to from the Multipass "Open Shell"  menu item. Note that the command prompt should **NOT** say "ubuntu@completegeek," it should say your name and the name of your computer.

In that terminal, you'll type:

```bash
multipass delete completegeek
multipass purge
```

To create the completegeek VM again after deleting it, you'll use the launch command again. Open up the terminal window for your laptop (the prompt should show you that you're on your laptop) and type:

```bash
multipass launch --name completegeek
```

Now continue to CHECKPOINT 1 at the bottom of this page.

## Setting up a virtual machine on a Windows computer

First, we'll need to install the VM software. For Windows, we're going to install virtual machine software called VirtualBox. This is the software that "pretends" to be an actual physical computer for the virtual machines running on it. Go to the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads) and click the "Windows hosts" link. This should download the installer for VirtualBox.

Run (Open) the installer, allow it to make changes to your device, and accept all the default choices (say "Yes" or "Next" to everything).

Once VirtualBox is installed, we'll need to install Multipass. Go to the [Multipass download page](https://multipass.run/install) and click the Windows icon to go the installation instructions. Download Multipass from the supplied link. Double-click the downloaded installer.

Click "Yes" on "Do you want to allow this app to make changes to your device?" Then click "Next" and "I Agree." Change the selector on the "Hypervisor" window to "Oracle VM VirtualBox." Either choice will work, but not all Windows systems are compatible with the "Microsoft Hyper-V" choice. Assuming you've installed VirtualBox following these instructions, it should work on any OS type of Windows 10 or Windows 11. (If you know your computer can run Microsoft Hyper-V and Hyper-V is not grayed-out, feel free to pick it.)

On the "Add Multipass to PATH" screen, leave it on the recommended choice and click "Next."

Click "Next" on the "Choose Install Location" screen.

On the "Choose Components" screen, don't change anything and click "Install." When it's done, click "Finish."

Now you'll need to run the command prompt. Search for "cmd" and click the "Command Prompt" application.

Once you're in the "Command Prompt" application, you'll see a black screen with white text. This is the Windows version of the Linux command-line prompt. You type commands and hit [ENTER] to have your computer do things. All of this will make a lot more sense once we cover the Linux command-line, but unfortunately we kind of have to dump you in the deep end right now to get things going.

Now you'll see the prompt in the Command Prompt window. My prompt was "`C:/Users/jms`". Yours will be different unless your initials are also "JMS."

Type the following command:

 ```bash
 multipass launch --name completegeek
 ```

This will create the completegeek Ubuntu VM.

Multipass should start printing some information to the Command Prompt about "Retrieving image." How long that takes depends on the speed of your Internet connection. It will then start the "completegeek" image. You'll know it's done when you see the prompt again at the bottom of the screen.

Now there should be a Multipass "M" icon in the system tray at the bottom-right of the screen. Right-click that and select "completegeek (running)" and then "Open Shell."

This will open up a new terminal window with a green command prompt at the bottom reading "`ubuntu@completegeek:~$`". If it does, you've successfully started the VM and connected to it. You can also do that multiple times to open up multiple shells to the same VM.

To exit the VM, type "`exit`" and hit ENTER. You can then open another terminal window to the VM by clicking the M icon again.

To shutdown your VM, at the "`ubuntu@completegeek`" command prompt, enter the following command:

```bash
sudo shutdown -h now
```

You can start up the VM again any time you want by right-clicking the "M" icon in the system tray, clicking "completegeek" and then clicking "Start."

To delete your VM entirely (for instance if you've messed it up or you're not sure where you got to in a series of commands and want a fresh start) then you'll need to go to the Command Prompt (the same place where you typed in "`multipass launch...`"), **NOT** the shell you get to from the Multipass "Open Shell"  menu item. Note that the command prompt should **NOT** say "ubuntu@completegeek," it should say "`C:/Users/jms`" or something similar.

In that terminal, you'll type:

```bash
multipass delete completegeek
multipass purge
```

To create the completegeek VM again after deleting it, you'll use the launch command again. Open up the terminal window for your laptop (the prompt should show you that you're on your laptop) and type:

```bash
multipass launch --name completegeek
```

Now continue to CHECKPOINT 1 at the bottom of this page.

## CHECKPOINT 1: Verifying that your virtual machine is working properly

Now connect to your VM. Once connected, you should be able to enter the following commands:

* `whoami` -- should show your user name (ubuntu)
* `date` -- should show the current date and time (timezone will be UTC, not your local timezone)
* `uptime` -- should show the current time, and the number of minutes since you turned the VM on, as well as the number of users currently logged in (1) and the load average.

Here's an example of what that looked like for me:

```bash
ubuntu@completegeek:~$ whoami
ubuntu
ubuntu@completegeek:~$ date
Thu Dec 21 19:54:49 UTC 2023
ubuntu@completegeek:~$ uptime
 19:55:18 up 6 min,  1 user,  load average: 0.01, 0.18, 0.12
ubuntu@completegeek:~$
```

If your output looks similar to mine, congratulations!

Now let's exit the VM. Type `exit` and hit ENTER.

Now delete and purge the completegeek VM. You will probably mess up your VM in the future, and you'll need to know how to get a fresh start.

Once you've deleted and purged the completegeek VM, create a new one and connect to it. Verify that it's working.

Now shut down the VM. You've successfully created a VM, connected to it, and run some commands! You've passed Checkpoint 1. Go ahead and move on to [Chapter 2](002-directories.md). If you didn't pass the checkpoint, check your work or ask questions in the discussion group or in office hours.

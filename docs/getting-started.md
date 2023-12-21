# Chapter 1: Getting Started

## Introduction

The first thing that we're going to learn involves the Linux command-line. We'll be studying Linux and Unix operating systems as the foundation for everything else that we're learning.

To do that, and to ensure that we have a consistent environment for everyone, we'll be installing a virtual machine on your laptop. That virtual machine will be running Ubuntu Linux. (There are other varieties of Linux and Unix that we'll cover later. For now, we'll focus on Ubuntu.)

What is a virtual machine (VM)? It's a program that runs on your laptop that *pretends* that it's an entire computer. To understand that, we'll need to understand a little bit about the parts a non-virtual computer has.

Your laptop has a few important parts:

* It has a **CPU**: The thing that actually does all the processing (following instructions that you or someone else wrote)
* It has a **GPU**: A specialized type of CPU intended to be used for complicated graphics (and now often used for crypto or AI calculations)
* It has a display: A screen that lets you see what's going on
* It has RAM: Short-term memory that the CPU uses as kind of a scratch-pad. It gets erased every time you turn off or reboot your computer
* It has long-term storage, either a hard drive or an SSD: This is a place for your CPU to write data, that lasts even when the computer is turned off or rebooted. It's where programs are installed, or your Word or Excel documents are saved.

A virtual machine pretends that it has all those parts -- it has parts that pretend to be a CPU, pretend to be a display, pretend to be RAM, etc. You can install a brand-new operating system on it (different from what's running on your laptop) and from the point of view of that virtualized operating system, it thinks it's running on a regular computer. It doesn't necessarily know that it's on a VM.

Now we'll need to go through the process of installing some software and installing an operating system. By the end of this chapter, you should be able to log into the virtualized Ubuntu operating system we'll install.

What follows is instructions for setting up a VM on both Windows and MacOS. You'll do *one* of those, depending on which type of laptop you have. You don't need to do both.

## Setting up a virtual machine on a MacOS (Apple) computer

You'll need to install VirtualBox, which is a free virtual machine program. There are other virtual machine programs you can use that will work just fine, but the only one we'll walk you through is VirtualBox.

Older MacOS computers have chips made by Intel. Newer MacOS computers (those released since roughly 2020) have a M1 or M2 chip based on ARM processors and made by Apple. The two types of chip are not compatible with each other.

You can tell what kind of chip your MacOS computer is based on by clicking the Apple icon in the upper left-hand corner of your screen, and then clicking "About this Mac."

To the right of "Chip" it will say either "Apple M1 Max" (or Apple M-anything) if you have an ARM-based Mac. It will say "Intel..." if you have an Intel-based Mac.

### On Intel-Based Macs

If you have an Intel-based Mac, you'll go to the [VirtualBox Download Page](https://www.virtualbox.org/wiki/Downloads) and download the package for "macOS / Intel hosts."

### On ARM-based Macs

If you have an ARM-based Mac, you'll go to

## Setting up a virtual machine on a Windows computer

## CHECKPOINT 1: Verifying that your virtual machine is working properly

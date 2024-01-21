# Operating Systems and Unix History and Culture

FIXME/TODO: This should probably be eliminated as a chapter and the contents introduced when we encounter them.

## What is an Operating System?

So your computer has hardware -- the CPU, network interface, video interface, USB ports, etc.

It also almost certainly has apps installed on it. A word processor like Microsoft Word, a spreadsheet like Microsoft Excel, a web browser like Chrome, Firefox, Edge, or Safari, etc.

In between the hardware and the applications sits the operating system (OS). Your computer's operating system is almost certainly either Windows or MacOS (Macintosh). The operating system provides compatibility to your applications -- they don't have to know about the hardware, they just need to know about the OS. Your OS has to know how to talk to each piece of hardware in your system, and the applications just need to know how to talk to the OS.

Your OS also provides security -- making sure that applications and websites can only access the resources on your computer that they're allowed to use. Imagine how bad it would be if any website could read the files on your hard drive -- the operating system (and the web browser) limit the resources any particular web site is able to access.

Unix and Linux are also operating systems, but instead of being used primarily on people's laptop and desktop computers, they're used primarily on servers. A server is a computer that's used primarily to provide services -- the computers that make Facebook and Instagram work are servers, as are the computers that make your bank's and insurance company's websites work. (Some desktop and laptop computers are set up to use Linux, but if you're using Linux as a desktop operating system, you're probably not in the target market for this guide.)

## Why You Should Pick Linux/Unix to Specialize In

* MacOS (Macintosh) operating systems are used primarily on the desktop.
* Windows operating systems are used primarily on the desktop, but are also used in servers.
* Linux/Unix operating systems are used primarily on the server.

I strongly advise against specializing in desktop support, either of Windows or MacOS or Linux. There's a few reasons for that. Desktop support is always a cost center (it costs companies money, but doesn't make them any). This means it's the first to be cut in layoffs, is not considered prestigious, and does not have a great career path for advancement. In general, you deal with the most annoying people and problems in desktop support -- "I can't print," "the Internet is broken," etc.

Focusing your career on the server side makes sense. It's often a profit center (if your company sells something over the internet) and has much higher potential for advancement and high pay. The problems are just as urgent (or more urgent) as desktop support, but tend to be more interesting.

There's absolutely nothing wrong with deciding to specialize in Windows on the server side. And there's absolutely nothing wrong with getting skilled at server-side Linux and server-side Windows.

I picked Linux for my career and for this guide for a few reasons:

* It's free or low-cost. There's no purchasing anything required, making it a really good choice to learn from
* Some stuff in Windows like the PowerShell command-line is based on or inspired-by the Unix command-line.
* Almost all software that's still being used gets updates, and updates often mean that you need to learn new skills and techniques. When a new version of Windows is released, you'll have to relearn about 50% of the things you know. And it's very hard to predict in advance which 50% it will be. With Unix, you can easily predict what parts of the OS will be stable, and put maximum effort into those. For instance, sed, awk and regular expressions will be roughly the same in 20 years as they are today -- meaning effort you put into learning them today will pay off for your entire career.

## Unix and Linux History

Unix was developed as an operating system in the early 1970's, meaning it's over 50 years old today. Over the years it's had various offshoots and copies, all of which are more-or-less compatible.

The BSD Unixes branched off the original Unix and then branched again, turning into FreeBSD, OpenBSD, NetBSD and others.

Linux began as a copy of the Unix kernel (the central part of the OS) and added the GNU tools, the additional software that goes around the kernel to make a complete OS. GNU is a different project from Linux, and pedants will tell you that it should be referred to as GNU/Linux, but everyone just calls it Linux.

Linux is by far the most popular version of Unix in use, and it's what we're going to be using for all of our projects. Once you learn Linux, learning the other Unixes (FreeBSD, etc.) is relatively simple.

## Unix Culture

Unix is based on a culture of collaboration and open communication. Everything you get with the Linux OS is open source, meaning you can look at the source code (the "recipe" for the software) for every part of it.

Unix is based on the idea of small programs, working together and building something bigger from the parts. Rather than "find" being a function of Microsoft Word, there's a utility called "grep" that does nothing else.

Unix is not chatty. Unix programs give you error messages when something goes wrong, but generally don't have much to say when things go right. This is to facility chaining them together into "pipelines" that accomplish bigger tasks.

Unix gives you enough rope to hang yourself, and all the rest of the rope from the hardware store too. In Windows if you try to erase your main hard drive, you'll have to go through lots of prompts of "are you sure," "are you really sure," etc. If you tell Unix to nuke your hard drive, it will just go ahead and nuke it. Unix is a real "measure twice, cut once" operating system.

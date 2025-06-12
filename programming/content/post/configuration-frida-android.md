---
title: "Configuration Frida Android"
date: 2025-06-12T17:09:47+02:00
math: false
tags: [android, frida]
---

# Getting started with Frida 

In this post, I will briefly talk about how to configure Frida. For this tutorial I used an Android emulator with root permissions, but Frida can also be used for other platforms. 

## **Installation**


First step is to have ADB installed. If you have Android studio, you will probably have it already installed. I summarized some basic commands on the post about [Android forensics](https://jackleila.github.io/programming/public/post/android-forensics-tools/).

To install Frida, we can use Python packet manager pip:


```bash
pip3 install frida-tools
```


Based on the OS and processor we want to use Frida in, we can download the appropiate version [here](https://github.com/frida/frida/releases).


## **Execution**

Then we can proceed to put it in the emulator and execute it:

![Config](https://jackleila.github.io/programming/images/frida_config.png)

![Execution](https://jackleila.github.io/programming/images/frida_exec.png)

And now our Frida setup should be ready:

![Frida](https://jackleila.github.io/programming/images/frida_ps.png)

## **Commands**

The command: 

```bash
frida-ps -Uia
```
Allow us to show the applications installed and its package names:

-U	Connect to USB device 

-i	Show package names

-a	Show applications


---
title: "Reversing With Ghidra I"
date: 2021-10-28T12:04:53+02:00
math: false
categories: [cracking, reversing]
tags: [ghidra]
---



In this post we will take a brief look at Ghidra, a tool developed by the NSA for the reversing. Ghidra is a powerful program with a lot of options, and we will be exploring them in different tutorials by resolving different reversing challenges. In this tutorial we will look at the installation, project creation and overview by resolving a simple crackme.

## Installation

To run Ghidra, you need to install [JDK 11 64-bit](https://adoptium.net/releases.html?variant=openjdk11&jvmVariant=hotspot).
Afterwards, you can find the releases you need to download [here](https://github.com/NationalSecurityAgency/ghidra/releases) and extract it. Then, simply run it 
with:

` ./ghidraRun `

or 

`ghidraRun.bat`

On Windows

## Simple reversing

For this example we will get a binary from the website [Crackmes.one](https://crackmes.one/crackme/5b8a37a433c5d45fc286ad83). It is a very simple example that will allow us to introduce to Ghidra.

We first create a new project under "File -> New Project". Then, once the project is created, we go to File-> Import File and select the crackme we downloaded. The first window we will se is something like this:

![Ghidra Init](/images/menu_init_ghidra.PNG)

We can see that Ghidra detected the language automatically. Afterwards, it shows us a summary of the results. We can now start the CodeBrowser by double-clicking the file and it will asks us if we want to analyse the binary and will show us a lot of options. We can leave it by default for now, and click analyze. We will see the disassembly:

![Ghidra Main](/images/ghidra_main.PNG)

We can start by looking at the Symbol Tree, and expanding the functions node. We can see that all the functions of the program are there. If we click in one, we can see the C code in the Decompiler window. If we click the `main` function, we will see this:

 ![Ghidra Function](/images/main_function_ghidra.PNG)


If we take a look at the code, we notice that param_1 is the number of inputs (argv) and param_2 is our input (argc). 

{{< highlight c "linenos=table,hl_lines=8 15-17,linenostart=199" >}}
	undefined8 main(int param_1,undefined8 *param_2){
	  size_t sVar1;
	  
	  if (param_1 == 2) {
		sVar1 = strlen((char *)param_2[1]);
		if (sVar1 == 10) {
		  if (*(char *)(param_2[1] + 4) == '@') {
			puts("Nice Job!!");
			printf("flag{%s}\n",param_2[1]);
		  }
		  else {
			usage(*param_2);
		  }
		}
		else {
		  usage(*param_2);
		}
	  }
	  else {
		usage(*param_2);
	  }
	  return 0;
	}
{{< / highlight >}}


We can see that the program is storing in sVar1 the lenght of our input and comparing it with 10. If it is 10, it will check that the 5th position is equal to @. So any 10 character string whose 5th position is @ will be a valid password:


In the following posts about Ghidra we will take a deeper look at Ghidra functions by solving more challenges. 
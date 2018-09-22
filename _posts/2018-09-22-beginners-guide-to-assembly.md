---
layout: post
title: A beginners guide to assembly
image: /img/assembly.jpg
---

One topic that has intrigued me for the longest time was low-level programming, particularly the assembly language. The assembly language is , as described by Wikipedia "a low-level symbolic code converted by an assembler.". Essentially its a set of machine code instructions that control the computer CPU. There are multiple variations of it - x86 , x86_64, mipsle and armle to name a few - all of which are slightly different in their own respects. The x86_64 variant is the version found within 64 bit computers, while x86 is the one you'd generally find in a 32 bit computer / operating system. The other mentioend CPU's you would generally find within a Rasperry Pi (ARM) or your commercial router (MIPS). The CPU's instructions allow you to control the devices kernel functions, and allows you to perform functions calls to the kernel library.

For example, a basic x86_64 assembly language code to exit a program would go as follows 

```assembly
push 60;
pop rax;
syscall;
```

The gist of the snippet is to push the system call number for the `exit` call into the RAX register, and then call the system call with `syscall`. A list of system calls for the linux kernel can be found [here](https://syscalls.kernelgrok.com/). Feel free to adjust and tinker to your needs. 

However, the same call would be slightly different in x86. Instead of using the `RAX` & `SYSCALL` assembly opcodes to load into a register and call an syscall, we'd be using `EAX` and `int 0x80` to perform the lower bits call.

As such, it would be along the lines of 

```assembly
push 0x01;
pop eax;
int 0x80
```

Anyhow. These are simple demonstrations and are not entirely practical. However, using this knowledgre & with a little tinkering, you should be able to write some impressive programs to do simple tasks such as executing a shell, or reading and writing a file over a socket.


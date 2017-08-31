DISCLAIMER:
1. The copyright of this project belongs to Imperial College London.
2. From this code I removed some parts on purpose to make it broken.

PintOS is a simple operating system framework for the 80x86 architecture. It supports kernel threads, loading and running user programs, and a file system, but it implements all of these in a simpler way compared to the most popular operating systems we are using such as Linux, Mac OSX and Windows.

-----------------------------
Files/Directories explained.
-----------------------------

1. Starting with ‘pintos/src’:


 	> ‘userprog/’ <: Source code for the user program loader.


	> ‘filesys/’ <: Source code for a basic file system.

	> ‘utils/’ <: These files may come in handy if you decide to try working with Pintos on your own machine. Otherwise, you can ignore them.


2. Secondly, moving into ‘pintos/build’ directory we have:

	> ‘Makefile’ <: A copy of ‘pintos/src/Makefile.build’. It describes how to build the kernel.

	> ‘loader.bin’ <: Memory image for the kernel loader, a small chunk of code written in assembly language that reads the kernel from disk into memory and starts it up. It is exactly 512 bytes long, a size fixed by the PC BIOS.


3. Moving now into ‘pintos/devices’ directory, we have:

	> ‘timer.c’ <:
	> ‘serial.h’ <: Serial port driver. Again, printf() calls this code for you, so you don’t need to do so yourself. It handles serial input by passing it to the input layer (see below).
	> ‘partition.h’ <: Understands the structure of partitions on disks, allowing a single disk to be carved up into multiple regions (partitions) for independent use.

	> ‘speaker.h’ <: Driver that can produce tones on the PC speaker.

	> ‘loader.S’ <: 
	> ‘loader.h’ <: The kernel loader. Assembles to 512 bytes of code and data that the PC BIOS loads into memory and which in turn finds the kernel on disk, loads it into memory, and jumps to start() in ‘start.S’. 
	> ‘init.h’ <: Kernel initialization, including main(), the kernel’s “main program.” You should look over main() at least to see what gets initialized.

	> ‘thread.h’ <: Basic thread support. ‘thread.h’ defines struct thread, which you are likely to modify in all four tasks.

	> ‘switch.h’ <: Basic thread support. ‘thread.h’ defines struct thread, which you are likely to modify in all four tasks.

	> ‘palloc.h’ <: Page allocator, which hands out system memory in multiples of 4 kB pages.

	> ‘malloc.h’ <: A simple implementation of malloc() and free() for the kernel.

	> ‘interrupt.h’ <: Basic interrupt handling and functions for turning interrupts on and off.

	> ‘intr-stubs.h’ <: Assembly code for low-level interrupt handling.


	> ‘ctype.h’ <: 
	> ‘inttypes.h’ <: 
	> ‘limits.h’ <:
	> ‘stdarg.h’ <:
	> ‘stdbool.h’ <:
	> ‘stddef.h’ <:
	> ‘stdint.h’ <:
	> ‘stdio.c’ <:
	> ‘stdio.h’ <:
	> ‘stdlib.c’ <:
	> ‘stdlib.h’ <:
	> ‘string.c’ <:
	> ‘string.h’ <: A subset of the standard C library. See Section C.2 [C99], page 82, for information on a few recently introduced pieces of the C library that you might not have encountered before.
	> ‘debug.h’ <: Functions and macros to aid debugging. See Appendix E [Debugging Tools], page 88, for more information.

	> ‘random.c’ <: 
	> ‘random.h’ <: Pseudo-random number generator. The actual sequence of random values may vary from one Pintos run to another.



	> ‘kernel/list.h’ <: Doubly linked list implementation. Used all over the Pintos code, and you’ll prob- ably want to use it a few places yourself in task 0 and task 1.
	> ‘kernel/bitmap.h’ <: Bitmap implementation. 

	> ‘kernel/hash.h’ <: Hash table implementation.
	> ‘kernel/console.h’ <: 
	> ‘kernel/stdio.h’ <: Implements printf() and a few other functions.


6. Moving into user programs directory we have:

	> ‘process.c’ <: 
	> ‘process.h’ <: Loads ELF binaries and starts processes.
	> ‘pagedir.h’ <: A simple manager for 80x86 hardware page tables. Although you probably won’t want to modify this code for this task, you may want to call some of its functions. 

	> ‘syscall.c’ <:
	> ‘syscall.h’ <: Whenever a user process wants to access some kernel functionality, it invokes a system call. This is a skeleton system call handler. Currently, it just prints a message and terminates the user process. In part 2 of this task you will add code to do everything else needed by system calls.

	> ‘exception.c’ <: 
	> ‘exception.h’ <: When a user process performs a privileged or prohibited operation, it traps into the kernel as an “exception” or “fault.”1 These files handle exceptions. Currently all exceptions simply print a message and terminate the process.

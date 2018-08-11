## Computer Basics


## Chapter 5. Dealing with Files UNIX
- When you access a file, you start by opening it by name. The operating system then gives you a number, called a *file descriptor*.  
- Read is system call 3, and to call it you need to have the file descriptor in %ebx  
- Write is system call 4, and it requires the same parameters as the read system call, except that the buffer should already be filled with the data to write out. The write system call will give back the number of bytes written in %eax or an error code.


#### Buffers and .bss
A buffer is a continuous block of bytes used for bulk data transfer. When you request to read a file, the operating system needs to have a place to store the data it reads. That place is called a buffer.  

Another thing to note is that buffers are a fixed size, set by the programmer. So, if you want to read in data 500 bytes at a time, you send the read system call the address of a 500-byte unused location, and send it the number 500 so it knows how big it is.

#### Standard and Special Files

- STDIN This is the standard input. It is a read-only file, *file descriptor 0*.  
- STDOUT This is the standard output. It is a write-only file, *file descriptor 1*.  
- STDERR This is the standard error. It is a write-only file, *file descriptor 2*.  

#### Building Robust Program Where Does the Time Go?
Programmers schedule poorly. In almost every programming project, programmers will take two, four, or even eight times as long to develop a program or function than they originally estimated. There are many reasons for this problem, including:  
• Programmers don’t always schedule time for meetings or other non-coding activities that make up every day.  
• Programmers often underestimate feedback times (how long it takes to pass change requests and approvals back and forth) for projects.  
• Programmers don’t always understand the full scope of what they are producing.  
• Programmers often have to estimate a schedule on a totally different kind of project than they are used to, and thus are unable to schedule accurately.  
• Programmers often underestimate the amount of time it takes to get a program fully *robust*.  


### Chapter 9. Intermediate Memory Topics

#### How a Computer Views Memory :

A computer looks at memory as a long sequence of numbered storage locations. A sequence of millions of numbered storage locations. Everything is stored in these locations. Your programs are stored there, your data is stored there, everything. Each storage location looks like every other one. The locations holding your program are just like the ones holding your data. In fact, the computer has no idea which are which, except that the executable file tells it where to start executing.  

#### The Memory Layout of a Linux Program
When you program is loaded into memory, each .section is loaded into its own region of memory. All of the code and data declared in each section is brought together, even if they were separated in your source code.
The actual instructions (the `.text` section) are loaded at the address `0x08048000` (numbers starting with 0x are in hexadecimal). The `.data` section is loaded immediately after that, followed by the `.bss` section.  


The last byte that can be addressed on Linux is location 0xbfffffff. Linux starts the stack here and grows it downward toward the other sections.



#### Every Memory Address is a Lie :
- Virtual address vs Physical address  
- Memory swapping - Disk to RAM n vice versa  
- Pages : x86 Processors size is 4096 Bytes  
- Swap death : So many programs loaded cause of which hardly any space left on Physical memory.  Cause of which more of time spent on swapping than execution.
- Resident Set Size RSS : The amount of memory that your program currently has in physical memory is called it’s resident set size.  




[1]: https://github.com/mohammedjasam/Technical-Interview-Guide/blob/master/README.md

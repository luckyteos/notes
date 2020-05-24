

## Introduction

**Basic Operation of a computer**
![enter image description here](https://pxt.azureedge.net/blob/e644eb8aa2a44b1732aca811f598ab695b43420a/static/courses/csintro/algorithms/inputs-process-outputs.png)

## Memory
**Memory Hierarchy**
![enter image description here](https://images.computerhistory.org/revonline/images/500004956.jpg?w=400)
**Caching**
> Copying information into a faster storage medium eg. from hard disk to main memory (RAM)

> Every layer in the memory serves as a cache for the layer beneath it

**Virtual Memory:** Concept of each process having their own separate memory space, which is independent of where the memory allocated for the process is actually stored on the main memory (RAM)

**Page:** Smallest unit of data in memory. Can be given privileges like No permission/R/RW

**Page Table:** Contains the mappings of virtual addresses used in a process, to the actual addresses used in the main memory
> Every process has its own page table. Information about page tables for each process are stored in the CR3 register
> 
![enter image description here](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Virtual_address_space_and_physical_address_space_relationship.svg/1200px-Virtual_address_space_and_physical_address_space_relationship.svg.png =500x450)

**Page Fault:** 
Occurs when:

 - Page is not in the main memory (Paged out)
 - Non-Allocated memory address is accessed
 - Write operation is attempted on a read only page

**Swapping:** Taking memory from stagnant processes, store them maybe in the hard disk, and giving the freed memory space to processes that require memory


**User Mode/Kernel Mode**

![enter image description here](https://gabrieletolomei.files.wordpress.com/2013/10/memory_layout.jpg)

**Heap:** Memory space in process to allow for dynamic allocation of memory. By allocating memory from the heap there is no need to create a new mapping in the page table
> Protections such as R/RW cannot be set on memory allocated from the Heap

**Copy-On-Write:** Duplication of memory space when a process attempts to write to a read only page referenced by multiple processes, for example a shared DLL

**Shared Memory:** Processes are aware that they are sharing the memory

## Processes, Threads, Objects
**Process:** Management unit. Sort of like a container containing items

**Objects:** Runtime instances of static structures such as files, threads and processes stored in kernel space

**Handle:** Reference to an object stored in the kernel space. Access rights should be specified

**Handle Table:** Maps handles in user space to object in kernel space. 
![enter image description here](https://qph.fs.quoracdn.net/main-qimg-0fca3f679c15b5420dc9b78088aa218a)

**Handle Inheritance:** Child processes can inherit parent process handle

**Handle Duplication:** Specifically ask that handle from another process be copied into your process's handle table

**Reference Count:** Keeps count of whether an object is being "used" or referenced. If the reference count of an object is 0, OS may perform garbage collection of the object to free up memory

**Thread:** Basic scheduable system entity. A process should contain at least one thread. A process does not run, a thread is what executes the instructions in a program

### What's common - Process and Thread

![enter image description here](https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg)

### Synchronization
**Cooperation Problem:** Two threads attempt to access the same resource
eg. Two threads attempt to modify the same global variable

**Critical Section**

    x = 10
    
    # Process 1
    def add_to_x():
	    x = x + 1
	
	# Process 2
	def subtract_from_x():
		x = x - 1
If a context switch occurs for example before the new value of variable x is saved in process 1, and process 2 successfully modifies the value of x, then what should be the correct value of x now?

**How can we solve this?**
**Mutex**
* Implemented in the kernel as an object
* Clear owner: Only person who took it can put it back, though if no owner is specified anyone can take it and become the owner of it
* Examples: Log files can use mutex to prevent multiple threads from attempting to write to it at the same time

**EnterCriticalSection - Win32API**
* Does not need system call to transit to kernel mode
* Runs in the user mode
* Only synchronizes threads within a single process

**Other Synchronization Objects:**
* Semaphore
	* Like a gatekeeper
	* Specifies the maximum number of threads allowed to access a particular resource at a point in time
* Events
	* Two possible states: Signalled or not signalled
	* If Event is signalled, any threads can access resource and vice versa
	* Example: Clean a location - Events can be used to signal the status of different activities or tasks

**Interlocked Operations:** I

**More Waitable Objects**
* Processes
* Threads
* File
* Timer
	* Example process: Task scheduler
	
### Inter-process communication (IPC)
* Named Pipes
	* One pipe for sending, one pipe for receiving
	* Can be done in Win32API through CreateFile, ReadFile and WriteFile
* Shared Memory between processes
	* Can be done in Win32API with CreateFileMapping
* "Classic" IPC
	* Clipboard
	* Files
	* Sockets

## PE (Portable Executable) File Format
**AddressOfEntryPoint:** Where the program code begins, relative to the start of the PE File or the MZ Header

**ImageBase:** Ask the OS nicely if the PE image can be loaded at that virtual memory location

**ImportDirectory:** Contains a table of all the libraries imported by a program/image

**ExportDirectory:** Contains reference to functions inside my library that others can use to call them

**Relocation Table:** All the places in the PE image where there are absolute addresses that needs to be changed
* RVA of relocation table in CFF explorer points us to the relative address of the instruction containing the absolute address to be changed 	

## Linking and Loading
### Linking
* Static Linking
	* Happens before the process is created
	* Takes all the object files and links them to form an executable
	* Disadvantages:
		* Image file becomes bigger
		* If location of object file changes, then program would not be able to find the file
* Dynamic Linking
	* Happens after the process is created
	* Two main forms:
		* Implicit
			* Links the required libraries based on the Import Address Table (IAT)
		* Explicit
			* Manually specify using Win32API libraries to load in the program
				* Useful for:
					* Updating a running program or service
					* Malware running in a legitimate program importing libraries it depends on to 		function
					* When program that does not usually need a window needs to show a window in a particular situation
					
**Linker:** Creates the headers of the image file such as DOS Header, NT Header, Section Header

**.lib:** Contains all the different object files

### Loading
**Loader:** Loads the PE image into the process's virtual memory, along with its associated resources (imports etc)
 
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NzE3MzU1OTYsLTM5MTI4NzQyNSwzNz
A0MzgzMDgsLTc4NTA2Mzc4MywtMjI5NDI2NzQ0LDE2MDUyMTE3
NzgsMTg3NDcyMjAxNywxMjE0MTg0MDczXX0=
-->
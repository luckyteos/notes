

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
eyJoaXN0b3J5IjpbLTc4NTA2Mzc4MywtMjI5NDI2NzQ0LDE2MD
UyMTE3NzgsMTg3NDcyMjAxNywxMjE0MTg0MDczXX0=
-->


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
**Handle:** Reference to an object stored in the kernel space
**Handle Table:** Maps handles in user space to object in kernel space. Access rights for each handle 
**Reference Count:** Keeps count of whether an object is being "used" or referenced. If the reference count of an object is 0, OS may perform garbage collection of the object to free up memory
 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk2Nzc3MTg2NywtMTk5Njk5NDAwOSw0MD
g3MzgwNjgsLTU5ODg3NTAzMl19
-->
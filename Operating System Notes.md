

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

**Page Fault:** 
Occurs when:

 - Page is not in the main memory (Paged out)
 - Non-Allocated memory address is accessed
 - Write operation is attempted on a read only page

**Swapping:** Taking memory from stagnant processes, store them maybe in the hard disk, and giving the freed memory space to processes that require memory


**User Mode/Kernel Mode**
![enter image description here](https://gabrieletolomei.files.wordpress.com/2013/10/memory_layout.jpg)

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM2MDQ0MzQ4OCw0MDg3MzgwNjgsLTU5OD
g3NTAzMl19
-->
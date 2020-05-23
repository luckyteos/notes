---


---

<h2 id="introduction">Introduction</h2>
<p><strong>Basic Operation of a computer</strong><br>
<img src="https://pxt.azureedge.net/blob/e644eb8aa2a44b1732aca811f598ab695b43420a/static/courses/csintro/algorithms/inputs-process-outputs.png" alt="enter image description here"></p>
<h2 id="memory">Memory</h2>
<p><strong>Memory Hierarchy</strong><br>
<img src="https://images.computerhistory.org/revonline/images/500004956.jpg?w=400" alt="enter image description here"><br>
<strong>Caching</strong></p>
<blockquote>
<p>Copying information into a faster storage medium eg. from hard disk to main memory (RAM)</p>
</blockquote>
<blockquote>
<p>Every layer in the memory serves as a cache for the layer beneath it</p>
</blockquote>
<p><strong>Virtual Memory:</strong> Concept of each process having their own separate memory space, which is independent of where the memory allocated for the process is actually stored on the main memory (RAM)</p>
<p><strong>Page:</strong> Smallest unit of data in memory. Can be given privileges like No permission/R/RW</p>
<p><strong>Page Table:</strong> Contains the mappings of virtual addresses used in a process, to the actual addresses used in the main memory</p>
<blockquote>
<p>Every process has its own page table. Information about page tables for each process are stored in the CR3 register</p>
</blockquote>
<p><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/Virtual_address_space_and_physical_address_space_relationship.svg/1200px-Virtual_address_space_and_physical_address_space_relationship.svg.png" alt="enter image description here" width="500" height="450"></p>
<p><strong>Page Fault:</strong><br>
Occurs when:</p>
<ul>
<li>Page is not in the main memory (Paged out)</li>
<li>Non-Allocated memory address is accessed</li>
<li>Write operation is attempted on a read only page</li>
</ul>
<p><strong>Swapping:</strong> Taking memory from stagnant processes, store them maybe in the hard disk, and giving the freed memory space to processes that require memory</p>
<p><strong>User Mode/Kernel Mode</strong></p>
<p><img src="https://gabrieletolomei.files.wordpress.com/2013/10/memory_layout.jpg" alt="enter image description here"></p>
<p><strong>Heap:</strong> Memory space in process to allow for dynamic allocation of memory. By allocating memory from the heap there is no need to create a new mapping in the page table</p>
<blockquote>
<p>Protections such as R/RW cannot be set on memory allocated from the Heap</p>
</blockquote>
<p><strong>Copy-On-Write:</strong> Duplication of memory space when a process attempts to write to a read only page referenced by multiple processes, for example a shared DLL</p>
<p><strong>Shared Memory:</strong> Processes are aware that they are sharing the memory</p>
<h2 id="processes-threads-objects">Processes, Threads, Objects</h2>
<p><strong>Process:</strong> Management unit. Sort of like a container containing items</p>
<p><strong>Objects:</strong> Runtime instances of static structures such as files, threads and processes stored in kernel space</p>
<p><strong>Handle:</strong> Reference to an object stored in the kernel space. Access rights should be specified</p>
<p><strong>Handle Table:</strong> Maps handles in user space to object in kernel space.<br>
<img src="https://qph.fs.quoracdn.net/main-qimg-0fca3f679c15b5420dc9b78088aa218a" alt="enter image description here"></p>
<p><strong>Handle Inheritance:</strong> Child processes can inherit parent process handle</p>
<p><strong>Handle Duplication:</strong> Specifically ask that handle from another process be copied into your process’s handle table</p>
<p><strong>Reference Count:</strong> Keeps count of whether an object is being “used” or referenced. If the reference count of an object is 0, OS may perform garbage collection of the object to free up memory</p>
<p><strong>Thread:</strong> Basic scheduable system entity. A process should contain at least one thread. A process does not run, a thread is what executes the instructions in a program</p>
<h3 id="whats-common---process-and-thread">What’s common - Process and Thread</h3>
<p><img src="https://www.cs.uic.edu/~jbell/CourseNotes/OperatingSystems/images/Chapter4/4_01_ThreadDiagram.jpg" alt="enter image description here"></p>


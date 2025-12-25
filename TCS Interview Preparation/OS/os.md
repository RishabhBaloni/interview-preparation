# Operating System Interview Preparation - TCS Prime

## 1. OS Fundamentals (Must-Know)

### What is an Operating System?
An Operating System (OS) is system software that acts as an interface between computer hardware and user applications. It manages hardware resources, provides services to applications, and creates a user-friendly environment for interacting with the computer.

### Why do we need an OS?
- **Hardware Abstraction**: Provides simple interface to complex hardware
- **Resource Management**: Manages CPU, memory, storage, and I/O devices
- **Security**: Controls access to system resources and data
- **Multitasking**: Allows multiple programs to run simultaneously
- **User Interface**: Provides GUI or command-line interface
- **Error Handling**: Manages system errors and exceptions
- **File Management**: Organizes and manages files and directories

### Functions of an Operating System
- **Process Management**: Creating, scheduling, and terminating processes
- **Memory Management**: Allocating and deallocating memory to processes
- **File System Management**: Managing files and directories
- **I/O Management**: Controlling input/output operations
- **Security and Protection**: User authentication and access control
- **Network Management**: Managing network connections and protocols
- **Device Management**: Managing hardware devices and drivers

### Types of Operating Systems
- **Batch OS**: Processes jobs in batches without user interaction
- **Time-Sharing OS**: Multiple users share system resources simultaneously
- **Real-Time OS**: Guarantees response within specific time constraints
- **Distributed OS**: Manages resources across multiple connected computers
- **Network OS**: Provides network services and resource sharing
- **Mobile OS**: Designed for smartphones and tablets
- **Embedded OS**: Designed for embedded systems with limited resources

### OS vs Kernel
| Operating System | Kernel |
|------------------|--------|
| Complete system software | Core part of OS |
| Includes kernel + utilities | Low-level system functions |
| User interface provided | No direct user interface |
| Larger in size | Smaller and compact |
| Examples: Windows, Linux | Examples: Linux kernel, NT kernel |

### User mode vs Kernel mode
**User Mode:**
- Restricted access to hardware
- Cannot execute privileged instructions
- Applications run in user mode
- Limited memory access
- Safer execution environment

**Kernel Mode:**
- Full access to hardware and memory
- Can execute all CPU instructions
- OS kernel runs in kernel mode
- Direct hardware manipulation
- Higher privilege level

### System calls — what and why?
System calls are programming interfaces that allow user programs to request services from the operating system kernel. They provide a controlled way for applications to access hardware resources and OS services.

**Why needed:**
- **Security**: Controlled access to system resources
- **Abstraction**: Hide hardware complexity from applications
- **Standardization**: Consistent interface across different hardware
- **Protection**: Prevent direct hardware access by user programs

### Examples of system calls
- **Process Control**: fork(), exec(), exit(), wait()
- **File Operations**: open(), read(), write(), close()
- **Device Management**: ioctl(), read(), write()
- **Information Maintenance**: getpid(), alarm(), sleep()
- **Communication**: pipe(), shmget(), msgget()
- **Memory Management**: brk(), mmap()

### What is multitasking?
Multitasking is the ability of an operating system to execute multiple tasks or processes concurrently by rapidly switching between them. The CPU time is divided among different processes, giving the illusion of simultaneous execution.

### What is multiprocessing?
Multiprocessing is the use of multiple CPUs or processor cores to execute multiple processes simultaneously. Unlike multitasking (which uses time-sharing on single CPU), multiprocessing provides true parallel execution.

### What is multithreading?
Multithreading is the ability of a process to execute multiple threads concurrently. Threads within the same process share memory space and resources, making communication between them faster and more efficient.

### Multiprocessing vs multithreading
| Multiprocessing | Multithreading |
|-----------------|----------------|
| Multiple processes | Multiple threads within process |
| Separate memory space | Shared memory space |
| Higher overhead | Lower overhead |
| Better fault isolation | Less fault isolation |
| Inter-process communication needed | Direct memory sharing |
| More secure | Less secure |
| Examples: Chrome tabs | Examples: Web server handling requests |

### Batch OS vs Time-sharing OS
**Batch OS:**
- Jobs processed in batches
- No user interaction during execution
- High throughput for similar jobs
- Poor response time
- Examples: Early mainframe systems

**Time-sharing OS:**
- Multiple users share system simultaneously
- Interactive user sessions
- Good response time
- Lower throughput per job
- Examples: Unix, Linux, Windows

### Real-time OS — hard vs soft
**Hard Real-Time OS:**
- Strict timing constraints
- Missing deadline is system failure
- Deterministic behavior required
- Examples: Aircraft control, medical devices

**Soft Real-Time OS:**
- Flexible timing constraints
- Missing deadline degrades performance
- Best-effort timing guarantees
- Examples: Multimedia systems, gaming

## 2. Process Management (Very Common)

### What is a process?
A process is a program in execution. It includes the program code, current activity (program counter), stack, heap, data section, and other resources allocated by the operating system. Each process has its own memory space and system resources.

### Process vs program
| Process | Program |
|---------|---------|
| Dynamic entity (program in execution) | Static entity (code on disk) |
| Has memory allocated | No memory allocated |
| Has process ID (PID) | No PID |
| Active | Passive |
| Temporary (terminates) | Permanent (until deleted) |
| Multiple processes from one program | One program can create multiple processes |

### Process states
- **New**: Process is being created
- **Ready**: Process is waiting to be assigned to CPU
- **Running**: Process is currently executing on CPU
- **Waiting/Blocked**: Process is waiting for I/O or event
- **Terminated**: Process has finished execution

### Process Control Block (PCB)
PCB is a data structure that contains information about a process:
- **Process ID (PID)**: Unique identifier
- **Process State**: Current state of process
- **Program Counter**: Address of next instruction
- **CPU Registers**: Contents of processor registers
- **Memory Management Info**: Page tables, segment tables
- **I/O Status**: List of open files and I/O devices
- **Accounting Info**: CPU usage, time limits

### Context switching
Context switching is the process of saving the state of currently running process and loading the state of next process to be executed. It involves saving PCB of current process and loading PCB of new process.

### What causes context switching?
- **Time slice expiry**: Process exhausts its CPU time quantum
- **I/O request**: Process needs to wait for I/O operation
- **System call**: Process requests OS service
- **Interrupt**: Hardware interrupt occurs
- **Higher priority process**: Preemptive scheduling
- **Process termination**: Current process finishes execution

### What is scheduling?
Scheduling is the process of determining which process should be allocated CPU time and in what order. The OS scheduler decides when to switch from one process to another to maximize system efficiency and user satisfaction.

### Types of schedulers (long, mid, short)
**Long-term Scheduler (Job Scheduler):**
- Selects processes from job pool to ready queue
- Controls degree of multiprogramming
- Executes less frequently
- Decides which programs to admit to system

**Medium-term Scheduler:**
- Handles swapping of processes between memory and disk
- Reduces degree of multiprogramming
- Improves process mix and memory utilization

**Short-term Scheduler (CPU Scheduler):**
- Selects process from ready queue for CPU execution
- Executes very frequently (milliseconds)
- Must be very fast to avoid overhead

### CPU-bound vs I/O-bound process
**CPU-bound Process:**
- Spends more time using CPU
- Few I/O operations
- Examples: Mathematical calculations, image processing
- Benefits from faster CPU

**I/O-bound Process:**
- Spends more time waiting for I/O
- Frequent I/O operations
- Examples: Text editors, web browsers
- Benefits from faster I/O devices

### Orphan process
An orphan process is a child process whose parent process has terminated before the child process completes. The init process (PID 1) adopts orphan processes and becomes their new parent.

### Zombie process
A zombie process is a child process that has completed execution but still has an entry in the process table. It occurs when parent hasn't read the child's exit status using wait() system call.

### Inter-process communication (IPC)
IPC is a mechanism that allows processes to communicate and synchronize their actions. It's needed because processes have separate memory spaces and cannot directly access each other's data.

### IPC mechanisms (pipe, message queue, shared memory)
**Pipes:**
- Unidirectional communication channel
- Data flows from write end to read end
- Examples: Anonymous pipes, named pipes (FIFOs)

**Message Queues:**
- Messages stored in kernel-maintained queue
- Processes send/receive messages
- Messages have types and priorities

**Shared Memory:**
- Multiple processes share same memory segment
- Fastest IPC mechanism
- Requires synchronization mechanisms

### Critical section problem
Critical section is a code segment where shared resources are accessed. The critical section problem is to design a protocol that processes can use to cooperate and avoid race conditions when accessing shared resources.

### Race condition
Race condition occurs when multiple processes access shared data concurrently, and the final result depends on the timing of their execution. It leads to inconsistent and unpredictable results.

### Mutual exclusion
Mutual exclusion ensures that only one process can access a shared resource or critical section at a time. It prevents race conditions and maintains data consistency.

### Semaphores (binary vs counting)
**Binary Semaphore:**
- Can have values 0 or 1
- Used for mutual exclusion
- Also called mutex

**Counting Semaphore:**
- Can have any non-negative integer value
- Used to control access to resources with multiple instances
- Value represents number of available resources

### Mutex vs semaphore
| Mutex | Semaphore |
|-------|-----------|
| Binary (locked/unlocked) | Can be binary or counting |
| Ownership concept | No ownership |
| Only owner can unlock | Any process can signal |
| Simpler implementation | More complex |
| Used for mutual exclusion | Used for synchronization and counting |

## 3. Thread Management

### What is a thread?
A thread is the smallest unit of execution within a process. It's a lightweight process that shares memory space and resources with other threads in the same process but has its own stack, registers, and program counter.

### Thread vs process
| Thread | Process |
|--------|---------|
| Lightweight | Heavyweight |
| Shares memory with other threads | Separate memory space |
| Faster creation and switching | Slower creation and switching |
| Less overhead | More overhead |
| Communication through shared memory | Communication through IPC |
| Crash affects other threads | Crash doesn't affect other processes |

### User-level vs kernel-level threads
**User-level Threads:**
- Managed by user-level thread library
- Kernel unaware of threads
- Faster thread operations
- No system call overhead
- Blocking system call blocks entire process

**Kernel-level Threads:**
- Managed by operating system kernel
- Kernel aware of each thread
- Slower thread operations
- System call overhead
- Blocking system call blocks only that thread
- True parallelism on multiprocessor systems

### Benefits of multithreading
- **Responsiveness**: User interface remains responsive
- **Resource Sharing**: Threads share memory and resources
- **Economy**: Less overhead than creating processes
- **Scalability**: Can utilize multiple processors
- **Parallelism**: True parallel execution on multicore systems
- **Modularity**: Different threads handle different tasks

### Thread lifecycle
1. **New**: Thread is created but not started
2. **Runnable**: Thread is ready to run
3. **Running**: Thread is currently executing
4. **Blocked**: Thread is waiting for resource or event
5. **Terminated**: Thread has completed execution

### What is thread safety?
Thread safety means that a piece of code can be executed concurrently by multiple threads without causing race conditions or data corruption. Thread-safe code produces correct results even when accessed simultaneously by multiple threads.

### What is synchronization?
Synchronization is the coordination of multiple threads or processes to ensure they access shared resources in a controlled manner. It prevents race conditions and maintains data consistency.

### Starvation
Starvation occurs when a process or thread is perpetually denied access to resources it needs to proceed. It happens when the scheduling algorithm consistently favors other processes, leaving some processes waiting indefinitely.

## 4. CPU Scheduling (Conceptual Only)

### What is CPU scheduling?
CPU scheduling is the process of determining which process should be allocated CPU time when multiple processes are ready to execute. The goal is to maximize CPU utilization and system throughput while minimizing response time.

### Scheduling criteria
- **CPU Utilization**: Percentage of time CPU is busy
- **Throughput**: Number of processes completed per unit time
- **Turnaround Time**: Time from submission to completion
- **Waiting Time**: Time spent waiting in ready queue
- **Response Time**: Time from request to first response

### FCFS scheduling
First-Come, First-Served (FCFS) scheduling executes processes in the order they arrive in the ready queue. It's simple to implement but can cause convoy effect where short processes wait for long processes.

### SJF scheduling
Shortest Job First (SJF) scheduling selects the process with the smallest execution time. It's optimal for minimizing average waiting time but requires knowledge of future CPU burst times.

### Priority scheduling
Priority scheduling assigns priorities to processes and executes the highest priority process first. It can be preemptive or non-preemptive and may cause starvation of low-priority processes.

### Round Robin scheduling
Round Robin scheduling assigns equal time slices (quantum) to each process in circular order. It's fair and provides good response time but may have higher overhead due to frequent context switching.

### Preemptive vs non-preemptive scheduling
**Preemptive Scheduling:**
- OS can interrupt running process
- Better response time
- Higher overhead
- Examples: Round Robin, Preemptive Priority

**Non-preemptive Scheduling:**
- Process runs until completion or blocking
- Lower overhead
- Poor response time
- Examples: FCFS, SJF

### Convoy effect
Convoy effect occurs in FCFS scheduling when short processes get stuck behind long processes, leading to poor average waiting time. It's like cars stuck behind a slow truck on a single-lane road.

### Aging in scheduling
Aging is a technique to prevent starvation by gradually increasing the priority of processes that have been waiting for a long time. It ensures that all processes eventually get CPU time.

### Throughput vs turnaround time
**Throughput:**
- Number of processes completed per unit time
- Measures system productivity
- Higher is better

**Turnaround Time:**
- Total time from process submission to completion
- Measures user satisfaction
- Lower is better

## 5. Deadlocks (Prime Favorite)

### What is deadlock?
Deadlock is a situation where two or more processes are blocked forever, each waiting for resources held by the other processes. No process can proceed, creating a circular dependency.

### Four necessary conditions of deadlock
1. **Mutual Exclusion**: Resources cannot be shared simultaneously
2. **Hold and Wait**: Process holds resources while waiting for others
3. **No Preemption**: Resources cannot be forcibly taken from processes
4. **Circular Wait**: Circular chain of processes waiting for resources

### Deadlock prevention
Prevent deadlock by ensuring at least one of the four necessary conditions cannot occur:
- **Mutual Exclusion**: Make resources shareable (not always possible)
- **Hold and Wait**: Require processes to request all resources at once
- **No Preemption**: Allow resource preemption
- **Circular Wait**: Impose ordering on resource requests

### Deadlock avoidance
Avoid deadlock by carefully analyzing resource allocation requests and only granting requests that keep the system in a safe state. Uses algorithms like Banker's algorithm.

### Deadlock detection
Allow deadlock to occur but detect it using algorithms that check for circular wait conditions. Maintain resource allocation graphs and periodically check for cycles.

### Deadlock recovery
Once deadlock is detected, recover by:
- **Process Termination**: Kill one or more processes
- **Resource Preemption**: Take resources from some processes
- **Rollback**: Restore processes to previous safe state

### Banker's algorithm (concept only)
Banker's algorithm is a deadlock avoidance algorithm that simulates resource allocation to determine if granting a request would lead to a safe state. It ensures the system can always satisfy all processes' maximum resource needs.

### Livelock vs deadlock
**Deadlock:**
- Processes are blocked and cannot proceed
- No progress is made
- Processes are in waiting state

**Livelock:**
- Processes are active but make no progress
- Processes keep changing state in response to others
- Resources are being used but no useful work is done

### Starvation vs deadlock
**Starvation:**
- Process is denied resources indefinitely
- Other processes can still make progress
- Can be resolved by aging or fair scheduling

**Deadlock:**
- Multiple processes are blocked
- No process can make progress
- Requires external intervention to resolve

## 6. Memory Management (Very Common)

### What is memory management?
Memory management is the process of controlling and coordinating computer memory, assigning portions called blocks to various running programs to optimize overall system performance.

### Logical vs physical address
**Logical Address:**
- Generated by CPU during program execution
- Also called virtual address
- Used by programmer and process
- Translated to physical address by MMU

**Physical Address:**
- Actual location in main memory
- Used by memory hardware
- Generated by Memory Management Unit (MMU)
- Not directly accessible to user programs

### Address binding (compile/load/runtime)
**Compile Time:**
- Addresses determined during compilation
- Absolute code generated
- Program must be loaded at specific location

**Load Time:**
- Addresses determined when program is loaded
- Relocatable code generated
- More flexible than compile-time binding

**Runtime:**
- Addresses determined during execution
- Most flexible approach
- Allows dynamic memory allocation
- Used in modern operating systems

### Swapping
Swapping is the process of temporarily moving processes from main memory to secondary storage (swap space) and vice versa. It allows the system to run more processes than can fit in main memory simultaneously.

### What is fragmentation?
Fragmentation is the phenomenon where memory space is wasted due to inefficient allocation. It occurs when free memory is broken into small, non-contiguous blocks that cannot be used effectively.

### Internal vs external fragmentation
**Internal Fragmentation:**
- Wasted space within allocated memory blocks
- Occurs in fixed-size allocation schemes
- Memory allocated but not fully used
- Example: Process needs 18KB but gets 20KB block

**External Fragmentation:**
- Free memory exists but is not contiguous
- Occurs in variable-size allocation schemes
- Total free memory sufficient but scattered
- Example: 50KB free in 10KB chunks, need 30KB contiguous

### Paging
Paging is a memory management scheme that eliminates external fragmentation by dividing physical memory into fixed-size blocks called frames and logical memory into blocks of the same size called pages.

### Segmentation
Segmentation is a memory management scheme that divides programs into logical segments (code, data, stack) of variable sizes. Each segment represents a logical unit of the program.

### Paging vs segmentation
| Paging | Segmentation |
|--------|--------------|
| Fixed-size pages | Variable-size segments |
| No external fragmentation | May have external fragmentation |
| Internal fragmentation possible | No internal fragmentation |
| Hardware-based division | Logical division |
| Transparent to programmer | Visible to programmer |
| Single linear address space | Multiple address spaces |

### Page table
Page table is a data structure that maps logical page numbers to physical frame numbers. It's maintained by the OS for each process and used by the MMU for address translation.

### Page fault
Page fault occurs when a process tries to access a page that is not currently in main memory. The OS must load the required page from secondary storage, which may involve replacing another page.

### Thrashing
Thrashing occurs when a system spends more time swapping pages in and out of memory than executing processes. It happens when the system has insufficient memory for the active processes' working sets.

### Virtual memory
Virtual memory is a memory management technique that provides an abstraction of storage resources. It allows processes to use more memory than physically available by using secondary storage as an extension of main memory.

### Demand paging
Demand paging is a virtual memory implementation where pages are loaded into memory only when they are accessed (demanded) by the process. It reduces memory usage and startup time.

### TLB (Translation Lookaside Buffer)
TLB is a high-speed cache that stores recent page table entries to speed up address translation. It reduces the time needed to access memory by avoiding page table lookups for frequently used pages.

## 7. File Systems

### What is a file?
A file is a named collection of related information stored on secondary storage. It's the smallest allotment of logical secondary storage and provides a uniform logical view of information storage.

### File attributes
- **Name**: Human-readable identifier
- **Identifier**: Unique tag within file system
- **Type**: File format information
- **Location**: Pointer to device and location on device
- **Size**: Current file size in bytes
- **Protection**: Access control information
- **Time/Date**: Creation, last modification, last access
- **User Identification**: Owner information

### File operations
- **Create**: Allocate space and create directory entry
- **Write**: Add data to file at current position
- **Read**: Retrieve data from file at current position
- **Reposition (Seek)**: Move file pointer to specific location
- **Delete**: Remove file and free space
- **Truncate**: Reset file length to zero
- **Open**: Prepare file for access
- **Close**: Finish file access and update metadata

### File access methods
**Sequential Access:**
- Information processed in order
- Cannot skip records
- Examples: Tape drives, log files

**Direct Access (Random Access):**
- Can access any record directly
- Uses record number or key
- Examples: Database files, arrays

**Index Sequential Access:**
- Combines sequential and direct access
- Uses index for fast access
- Maintains sequential order

### Directory structure
**Single-Level Directory:**
- All files in one directory
- Simple but limited
- Naming conflicts possible

**Two-Level Directory:**
- Separate directory for each user
- Solves naming conflicts
- Limited organization

**Tree-Structured Directory:**
- Hierarchical organization
- Subdirectories allowed
- Most common structure
- Absolute and relative paths

### Single-level vs tree-structured directory
| Single-Level | Tree-Structured |
|--------------|-----------------|
| Flat structure | Hierarchical structure |
| All files in root | Files in multiple levels |
| Simple implementation | Complex implementation |
| Naming conflicts | No naming conflicts |
| Poor organization | Better organization |
| Fast search | Slower search |

### File allocation methods
Methods to allocate disk space to files:

**Contiguous Allocation:**
- Files stored in contiguous blocks
- Simple and fast access
- External fragmentation problem

**Linked Allocation:**
- Files stored as linked list of blocks
- No external fragmentation
- Sequential access only

**Indexed Allocation:**
- Index block contains pointers to data blocks
- Direct access possible
- Extra overhead for index blocks

### Contiguous allocation
In contiguous allocation, each file occupies a set of contiguous blocks on disk. The directory entry contains the starting block address and length of the file.

**Advantages:**
- Simple implementation
- Fast sequential and direct access
- Minimal head movement

**Disadvantages:**
- External fragmentation
- Difficult to grow files
- Need to know file size in advance

### Linked allocation
In linked allocation, each file is stored as a linked list of disk blocks. Each block contains a pointer to the next block in the file.

**Advantages:**
- No external fragmentation
- Files can grow dynamically
- No need to declare file size

**Disadvantages:**
- Sequential access only
- Extra space for pointers
- Poor reliability (broken link loses data)

### Indexed allocation
In indexed allocation, each file has an index block containing pointers to all blocks of the file. The directory entry points to the index block.

**Advantages:**
- Direct access possible
- No external fragmentation
- Dynamic file growth

**Disadvantages:**
- Extra overhead for index blocks
- Wasted space if file is small
- Complex implementation

### Free space management
Methods to keep track of free disk blocks:

**Bit Vector (Bitmap):**
- One bit per block (0=free, 1=allocated)
- Easy to find contiguous free blocks
- Space efficient for small disks

**Linked List:**
- Free blocks linked together
- No wasted space
- Difficult to find contiguous blocks

**Grouping:**
- First free block contains addresses of other free blocks
- Faster than simple linked list

**Counting:**
- Store address of first free block and count of contiguous free blocks
- Efficient for contiguous allocation

### Hard link vs soft link
**Hard Link:**
- Direct reference to file's inode
- Multiple names for same file
- Cannot cross file systems
- File deleted only when all hard links removed

**Soft Link (Symbolic Link):**
- Contains path to target file
- Can cross file systems
- Can link to directories
- Broken if target file deleted

### What is inode?
Inode (index node) is a data structure that stores metadata about a file or directory, including:
- File size and type
- Ownership and permissions
- Timestamps (creation, modification, access)
- Pointers to data blocks
- Link count

## 8. Disk Management & I/O

### What is disk scheduling?
Disk scheduling is the process of determining the order in which disk I/O requests should be serviced to minimize seek time and maximize throughput. The disk scheduler selects which request to service next from the queue of pending requests.

### FCFS disk scheduling
First-Come, First-Served (FCFS) disk scheduling services requests in the order they arrive. It's simple and fair but may result in poor performance due to excessive head movement.

### SSTF
Shortest Seek Time First (SSTF) scheduling selects the request that requires minimum seek time from current head position. It reduces average seek time but may cause starvation of requests far from current position.

### SCAN
SCAN scheduling (elevator algorithm) moves the disk head in one direction, servicing requests along the way, until it reaches the end, then reverses direction. It provides uniform wait times and prevents starvation.

### C-SCAN
Circular SCAN (C-SCAN) is a variant of SCAN that treats the disk as circular. The head moves in one direction only, jumping from the last cylinder to the first cylinder, providing more uniform wait times.

### Disk scheduling goals
- **Minimize seek time**: Reduce head movement
- **Maximize throughput**: Increase number of requests served
- **Minimize response time**: Reduce waiting time for requests
- **Fairness**: Prevent starvation of requests
- **Predictability**: Provide consistent performance

### I/O buffering
I/O buffering is the temporary storage of data during input/output operations to compensate for speed differences between devices and improve system performance.

**Types:**
- **Single Buffer**: One buffer between user and system
- **Double Buffer**: Two buffers for continuous operation
- **Circular Buffer**: Ring of buffers for streaming data

### Spooling
Spooling (Simultaneous Peripheral Operations On-Line) is a technique where data is temporarily stored in a buffer (spool) before being sent to a slower device like a printer. It allows multiple jobs to be queued and processed sequentially.

## 9. Virtualization & Security (Lightweight)

### What is virtualization?
Virtualization is the creation of virtual versions of computing resources (hardware, OS, storage, network) that allow multiple virtual systems to run on a single physical system. It provides isolation, resource sharing, and flexibility.

### Type-1 vs Type-2 hypervisor
**Type-1 Hypervisor (Bare Metal):**
- Runs directly on physical hardware
- Better performance and security
- Examples: VMware ESXi, Hyper-V Server
- Used in enterprise environments

**Type-2 Hypervisor (Hosted):**
- Runs on top of host operating system
- Easier to install and manage
- Examples: VMware Workstation, VirtualBox
- Used for development and testing

### What is sandboxing?
Sandboxing is a security mechanism that isolates running programs in a restricted environment to prevent them from accessing or modifying system resources. It limits the potential damage from malicious or buggy software.

### What is access control?
Access control is a security mechanism that determines who can access what resources and what operations they can perform. It includes authentication (who you are) and authorization (what you can do).

### Authentication vs authorization
**Authentication:**
- Verifies identity of user or system
- "Who are you?"
- Methods: passwords, biometrics, certificates
- Happens first in security process

**Authorization:**
- Determines what authenticated user can do
- "What can you do?"
- Based on permissions and roles
- Happens after authentication

### Protection vs security
**Protection:**
- Internal mechanisms to control access to resources
- Prevents unauthorized access within system
- Deals with accidental misuse
- Examples: file permissions, memory protection

**Security:**
- External mechanisms to defend against threats
- Protects against malicious attacks
- Deals with intentional attacks
- Examples: firewalls, encryption, intrusion detection

### What is a privilege escalation?
Privilege escalation is the act of gaining higher access privileges than originally granted. It can be:
- **Vertical**: Gaining higher privileges (user to admin)
- **Horizontal**: Gaining access to other users' resources
- Often exploited by attackers to gain system control

## 10. Common Trick / Rapid-Fire Questions

### Why is OS interrupt-driven?
OS is interrupt-driven because:
- **Efficiency**: CPU doesn't waste time polling devices
- **Responsiveness**: Immediate response to hardware events
- **Multitasking**: Allows switching between processes
- **Resource Management**: Handles multiple devices simultaneously
- **Real-time Response**: Critical for time-sensitive operations

### Why context switching is costly?
Context switching is costly because:
- **Save/Restore State**: Must save and load process state
- **Memory Operations**: Multiple memory accesses required
- **Cache Pollution**: New process may invalidate cache
- **TLB Flush**: Translation buffers need updating
- **Overhead**: No useful work done during switching
- **Frequency**: Happens very frequently in multitasking systems

### Can a system work without OS?
Yes, but with limitations:
- **Embedded Systems**: Simple devices with dedicated functions
- **Bare Metal Programming**: Direct hardware programming
- **Boot Loaders**: Initial system startup code
- **Real-time Systems**: Some use minimal kernels
- **Limitations**: No multitasking, no abstraction, difficult programming

### What happens when a process crashes?
When a process crashes:
1. **Signal Generation**: OS generates crash signal (SIGSEGV, SIGKILL)
2. **Process Termination**: Process is immediately terminated
3. **Resource Cleanup**: OS reclaims allocated resources
4. **Memory Deallocation**: Process memory is freed
5. **File Closure**: Open files are closed
6. **Parent Notification**: Parent process is notified
7. **Core Dump**: May generate core dump for debugging

### What happens during booting?
During booting:
1. **Power-On Self Test (POST)**: Hardware initialization
2. **BIOS/UEFI**: Basic input/output system startup
3. **Boot Loader**: Loads operating system kernel
4. **Kernel Loading**: OS kernel loaded into memory
5. **Hardware Detection**: Identify and initialize hardware
6. **Driver Loading**: Load device drivers
7. **System Services**: Start essential system services
8. **User Interface**: Present login screen or desktop

### Why kernel is loaded first?
Kernel is loaded first because:
- **Hardware Control**: Needs to manage hardware resources
- **Memory Management**: Must set up memory management
- **Process Management**: Required to run other programs
- **Security**: Establishes security and protection mechanisms
- **Foundation**: Provides foundation for all other software
- **Privilege**: Runs in highest privilege mode

### Can we have deadlock in single-process system?
No, classical deadlock cannot occur in single-process system because:
- **No Competition**: Only one process exists
- **No Circular Wait**: Cannot wait for itself
- **Resource Availability**: All resources available to single process
- **Exception**: Thread-level deadlock possible in multithreaded single process

### Difference between paging and swapping?
| Paging | Swapping |
|--------|----------|
| Moves pages (fixed-size blocks) | Moves entire processes |
| Part of virtual memory | Memory management technique |
| Transparent to process | Process may be aware |
| Smaller units transferred | Larger units transferred |
| More frequent operation | Less frequent operation |
| Better performance | Higher overhead |

### Can virtual memory be larger than RAM?
Yes, virtual memory can be larger than RAM because:
- **Secondary Storage**: Uses disk as extension of memory
- **Demand Paging**: Only needed pages loaded in RAM
- **Address Space**: Logical address space independent of physical memory
- **Swapping**: Pages moved between RAM and disk as needed
- **Limitation**: Performance degrades with excessive swapping

### What is copy-on-write?
Copy-on-Write (COW) is an optimization technique where multiple processes share the same memory pages until one of them tries to modify the data. Only then is a copy made, saving memory and improving performance.

**Benefits:**
- **Memory Efficiency**: Reduces memory usage
- **Fast Process Creation**: fork() becomes faster
- **Lazy Copying**: Copy only when necessary
- **Shared Libraries**: Multiple processes share library code

### What is time slice?
Time slice (quantum) is the amount of CPU time allocated to a process in time-sharing systems. When the time slice expires, the process is preempted and moved to the ready queue, allowing other processes to execute.

### Why round-robin is fair?
Round-robin is fair because:
- **Equal Time**: Each process gets equal CPU time
- **No Starvation**: Every process eventually gets CPU
- **Predictable**: Response time is bounded
- **Simple**: Easy to implement and understand
- **Democratic**: No process gets preferential treatment

### Why SJF is optimal?
SJF (Shortest Job First) is optimal because:
- **Minimum Average Waiting Time**: Mathematically proven optimal
- **Efficient**: Completes more short jobs quickly
- **Better Throughput**: Maximizes number of completed jobs
- **User Satisfaction**: Short jobs get quick response
- **Limitation**: Requires knowledge of job lengths (impractical)

---

## Key Interview Tips

### For TCS Prime Success:
1. **Understand Concepts**: Focus on "what" and "why" rather than implementation details
2. **Real-world Analogies**: Use everyday examples (restaurant, library, traffic)
3. **Process Flow**: Understand how components work together
4. **Comparison Tables**: Master "A vs B" type questions
5. **State Diagrams**: Visualize process and thread states

### Must-Know Flow:
**Process Lifecycle**: New → Ready → Running → Waiting → Terminated
**Memory Hierarchy**: CPU → Cache → RAM → Disk
**File Operations**: Open → Read/Write → Close

### Common Mistakes to Avoid:
- Confusing process and program
- Mixing up internal and external fragmentation
- Not understanding the difference between paging and segmentation
- Forgetting that threads share memory space
- Confusing deadlock conditions

### Interview-Ready Explanations:
- **Process**: "A program in execution with its own memory space"
- **Thread**: "Lightweight process that shares memory with other threads"
- **Deadlock**: "Circular waiting where no process can proceed"
- **Virtual Memory**: "Illusion of unlimited memory using disk as extension"

Remember: Focus on concepts and real-world applications rather than mathematical formulas or implementation details!
![](http://fondinfo.github.io/images/sys/hatred-pc.png)
# Operating Systems
## Introduction to Computer Science

---

![](http://fondinfo.github.io/images/sys/opsys.svg)
# Operating System

- Automatically started on power-on
- Intermediary between user, applications and hardware
- Functionality: batch, or interactive
- User access: single-user, or multi-user
- Resource management: uni-programming, *multi-programming* (time-sharing), *multi-processing* (multi-core...)

---

# Onion Operating System

![large](http://fondinfo.github.io/images/sys/onion.svg)

---

# Process Management

- Process: an instance of a program, in execution
- Multi-tasking OS: executes multiple programs concurrently, associated with processes
    - Creates and deletes processes
    - Decides which process to assign the CPU to
    - Suspends and resumes processes
- It also offers mechanisms for:
    - *Synchronization* and *deadlock* management
    - *Communication* between processes
    - Communication with *peripherals*

---

![large](http://fondinfo.github.io/images/sys/process-lifecycle.svg)
# Scheduling

- Single CPU: no real parallelism (at any given moment, only one process in execution)
- **Time-sharing**: cyclically, the processor is assigned for a *time-slice* (fixed interval ~10-100ms)
- If the process terminates within the interval
    - A new interval is started, another process is executed
- If it doesn't terminate or blocks (resource waiting)
    - Process suspended, new interval started, another process executed (*preemptive* O.S.)

---

![](http://fondinfo.github.io/images/sys/threads.svg)
# Execution Threads

- Smallest unit of instructions that can be scheduled by the OS
- Possible to divide a process into several tasks, running concurrently
    - Same code base
    - Sharing of *heap* and resources → *Mutexes and semaphores*
    - Different *stack* and *CPU state*

---

![](http://fondinfo.github.io/images/sys/deadlock.svg) Deadlock
# Parallelism and Concurrency

- Parallelism
    - Multiple physical processing units, CPU or cores
- Concurrency
    - Different processes, not necessarily all active
    - Management of simultaneous access to shared resources
    - Typical problems: starvation, deadlock

---

# Virtual Memory

- One or more programs: require more memory than available (primary)
- OS tries to simulate a *large, cheap and fast* memory
    - Management of primary/secondary memory hierarchy
    - Frees program (and programmer) from physical memory size

![large](http://fondinfo.github.io/images/sys/mem-architecture.svg)

---

# Paging

- Memory divided into pages of equal size
- Each running program is assigned a certain number of pages
- When the instruction to be executed is not in primary memory (**page fault**)...
    - If necessary, a page is moved from primary to secondary memory
    - The page containing the instruction is transferred to primary memory
    - Principle of *locality* (data and references are usually grouped)
- Paging policy
    - Usually *LRU (Least Recently Used)*...
    - Instead of *FIFO (First In First Out)*

---

![](http://fondinfo.github.io/images/sys/peripherals.svg)
# Peripheral Management

- High-level I/O procedures for interaction between programs and peripherals
- **BIOS** (Basic I/O System, firmware)
    - Diagnostics and initialization of internal devices (e.g., memory check)
    - Operating system boot (from Boot Sector)
- **Driver**: software programs that allow access to a specific peripheral
- Generally, peripherals are characterized by:
    - Data management speed << CPU
    - Sporadic and unpredictable data transmission

---

![](http://fondinfo.github.io/images/games/indexup.svg)
# Interrupt

- A mechanism is needed to:
    - Manage a peripheral while the CPU performs other activities
    - Avoid continuous CPU polling of peripherals (**polling**) for I/O data availability
- Normal processing state: the CPU ignores peripherals
- A peripheral requests I/O data: activates a line to the CPU (generates an **interrupt**)
    - Suspension of the running process (saving register state, to resume processing after the interrupt)
    - **Interrupt handler** executed (data transfer to/from peripheral, etc.)
    - Reactivation of the suspended process

---

![](http://fondinfo.github.io/images/repr/file-system.svg)
# Other functionalities

- **File system**: logical organization of data into tree structures
- **Shell**: textual or graphical interaction with the user
    - *User management*: personalization and protection of access to resources
    - *Application execution* <br> &nbsp;
- Different types of applications
    - *Horizontal software*, general-purpose (e.g., office)
    - *Vertical software*, for specific industry needs (e.g., hotel)
    - *Custom software*, ad hoc for a client (e.g., website)

---

# Folder Commands

- `pwd` — Show the path of the current working directory
- `cd $folder$` — Change the current working directory
- `mkdir $folder$` — Create a folder
- `rm -r $folder$` — Delete a folder
- `ls $folder$` — List the contents of a folder, with names only
- `ls -la $folder$` — List… with full details

---

# File Commands

- `mv $file$ $dest$` — Move a file
- `cp $file$ $dest$` — Copy…
- `rm $file$` — Delete…
- `touch $file$` — Create an empty file, or update the *timestamp*
- `chown $user$ $file$` — Assign a file to a user
- `chmod $mode$ $file$` — Set the access mode for a file
    - `chmod -w $file$` — File not modifiable
    - `chmod +x $file$` — Executable file

---

# Display Commands

- `echo "$message$"` — Display a message
- `cat $file$` — Display the content of one or more files (also for concatenating them)
- `less $file$` — Display the content of a file, paginated
    - (Type “`:q`” to exit)
- `sort $file$` — Display the lines of a file, sorted
- `xdd $file$` — Display the hexadecimal *dump* of a binary file

---

# Search Commands

- `find . -name $name$` — Search for a file recursively, by name
- `find . -size $size$` — … by size
- `find . -mtime $time$` — … by modification date
- `whereis` — Search for a command
- `grep $regex$ $file$` — Search for a *regex* in a file
- `grep -r` — … in a folder

---

# Process Commands

- `ps aux` — List all running processes
- `top` — List the most recently active processes
- `kill $pid$` — Terminate a process by *id*
- `killall $name$` — Terminate processes by name

---

# Archive and System Commands

- `zip -r $folder$, unzip $file$` — Compress and decompress a zip archive
- `wget $url$` — Download one or more files from a $url$
- `sudo …` — Execute a command as administrator
- `apt install $package$, apt uninstall $package$` — Install or uninstall a system package
- `man $command$` — Display the manual for a command

---

# Operators and Command Composition

- `>` — Redirect output stream to a file
- `<` — Redirect input stream from a file
- `|` — Connect output of one command to input of another
- `*` — Wildcard, any sequence of characters within file names
- `&` — At the end of a command, execute in *background*, shell free for other commands
- `#` — Comment until end of line (as in Python)
- `.` — Current folder
- `..` — Parent folder

---

# Examples

- `echo "Hello world" > hello.txt`
    - Output of `echo` to file `hello.txt`
    - File overwritten, contains text “Hello world”
- `cat < hello.txt`
    - Content of `hello.txt` as input for `cat`
    - Will display the file content to console
- `ls | less`
    - `ls` and `less` started together in two processes
    - Output of `ls` = input for `less`
    - Added pagination to the file list
- `ps aux | grep firefox`
    - `ps aux` and `grep firefox` started together in two processes
    - Output of the first = input for the second
    - Searches for lines containing “`firefox`” in the process list

---

# Python os module

- `chdir, chmod, chown, getcwd, listdir, mkdir, rename, remove, rmdir`
- `walk` — Traverse an entire branch of the file system with a `for` loop <br> Sequence of triples
    - Current folder path
    - List of folders
    - List of files
- `popen, kill` — Launch or terminate a process

>

<https://docs.python.org/3/library/os.html>

---

# Python sys module

- `platform` — system name
- `argv` — list of strings, command-line arguments for the Python script
- `path` — list of paths from which to import modules

*—*

- With `os` and `sys`, practical interaction with OS from Python
    - Installation and update scripts
    - Automation of administration tasks

>

<https://docs.python.org/3/library/sys.html>

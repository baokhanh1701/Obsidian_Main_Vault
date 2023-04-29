An important aspect of a modern system is the collection of system programs.
{User1, Word Processor} -\
{User2, Spreadsheets} ---> [Application Programs] --> [System Programs] --> [OS] ->[Hardware] 
{User3, Compilers}... --/ 

([Computer Hardware] -> Resource like CPU, Memory, I/O Devices)
- System programs provide a convenient environment for program development and execution.
- Some of them are simply user interfaces to system calls.
- Others are considerably more complex.

### File management
- Create.
- Delete.
- Copy.
- Rename.
- Print.
- Dump.
- List, and generally manipulate files and directories.

### Status Information
Ask the system for:
- Date, Time
- Amount of available memory or disk space
- Number of users
- Detailed performance
- Logging, and debugging information etc.

### File modification
- Several text editors may be available to create and modify the content of files stored on disk or other storage devices.
- There may also be special commands to search contents of files or perform transformations of the text.

### Programming-language support
- Compilers
- Assemblers
- Debuggers
- Interpreters
for common programming languages are often provided to the user with the OS.

### Program loading and execution
Once a program is assembled or compiled, it must be loaded into memory to be executed.
- Absolute loaders
> 	*An absolute loader is **a loader that places absolute code into main memory beginning with the initial address(absolute address) assigned by the assembler**. No address manipulation is performed.*
- Relocatable loaders
>	*Another function commonly performed by a loader is that of program re – location. Relocation is simply **moving a program from one area to another in the storage**. It referred to adjustment of address field and not to movement of a program.*
- Linkage editors
>	*The linkage editor is **a processing program that accepts object modules, load modules, control statements, and options as input**.*
- Overlay loaders
> *Overlaying is **a programming method that allows programs to be larger than the computer's main memory**.*

Debugging systems for either higher-level languages or machine language are needed as well.

### Comunications
These programs provide the mechanism for:
- Create virtual connections among processes, users, and computer systems.
- Allowing users to send messages to one another's screens
- To browse webpages
- To send electronic-mail messages
- To log in remotely or to transfer files from one machine to another.

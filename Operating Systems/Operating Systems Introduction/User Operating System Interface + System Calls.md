## User Operating System Interface
### CLI or Command Interpreter
- Some OS includes CLI in the kernel (Windows XP and UNIX treated CLI a special program).
- Some are known as Shell
	- Bourne shell
	- C shell
	- Bourne-Again shell (BASH)
	- Korn shell
- 
### GUI (Graphical User Interface)
## System Calls
- Provide an interface to the services made available by an OS
- Kernel mode is privileged.
	-  If a program executing in kernel mode and crash, the whole system will be crashed.
- User Mode is not as privileged.
- User Mode <-- syscall --> Kernel Mode (Context Switching)
> Syscall is the programmatic way in which a program requests a service from the kernel of the OS.
> These calls are generally available as routines written in C/C++.

Example: **Read data from one file and copy them to another file**
## Types of System Calls
#### Process Control
```
end, abort
load, execute
create process, terminate process
get process attributes, set process attributes
wait for time
wait event, signal event
allocate and free memory
```
#### File Manipulation
```
create, delete file
open, close
read, write, reposition
get file attributes, set file attributes
```
#### Device management
```
request/release devices
read, write, reposition
get device attributes, set device attributes
logically attach or detach devices
```
#### Information Maintenance
```
get time/date, set time/date
get/set system data
get process, file, or device attributes
set process, file, device attributes
```
#### Communications
```
create, delete comm connection
send, recieve messages
transfer status info
attach or detach remote devices
```
[[System Programs]]

![[Pasted image 20230425125615.png]]
Message passing provides a mechanism to allow processes to communicate and to synchronize their actions without sharing the same address space and is particularly useful in a distributed environment, where the communicating processes may reside on different computers connected by a network.

A message-passing facility provides at least two operations:
- Send (message)
- Receive (message)
Messages sent by a process can be of either fixed or variable size.

#### Fixed Size
- The system-level implementation is straightforward.
- But makes the task of programming more difficult.
#### Variable Size
- Requires a more complex system-level implementation.
- But the programming task becomes simpler.

>P and Q want to communicate, they must ==send messages to== and ==receive messages== from each other.
>--> A communication link must exist between them.

There are several methods for logically implementing a link and the `send() / receive()` operations, like:
- Direct or indirect communication
- Synchronous or asynchronous communication
- Automatic or explicit buffering
There are several issues related with features:
- Naming 
- Synchronization
- Buffering

## Naming
Processes must have a way to refer to each other. They can use either ==direct== or ==indirect== communication.

### ==Under direct communication:==
```
send (P, message) 
receive(Q, message)
```

A communication link in this scheme has the following properties:
- A link is established automatically between every pair of processes the want to communicate. The processes need to know only each other's identity to communicate.
- A link is associated with exactly two processes.
- Between each pair of processes, there exists exactly one link.

>This scheme exhibits ==symmetry in addressing:==
>--> Both the sender process and the receiver process must name the other to communicate.

##### Another variant of Direct Communication:
Here, only the sender names the reipient; the recipient is not required to name the sender
```
send(P, message) //Send a message to P
receive(id, message) //Receive a message from any process; the id is set to the name of the process with which communication has taken place.
```
This scheme employs asymmetry in addressing
This disadvantage in both of these schemes (symmetric and asymmetric) is the limited modularity of the resulting process definition.
Changing the identifier a process may necessitate examining all other process definitions.

### ==Under Indirect Communication:==
The messages are sent to and received from mailboxes, or ports.
- A mailbox can be viewed abstractly as an object into which messages can be placed by processes and from which messages can be removed.
- Each mailbox has a unique identification.
- Two processes can communicate only if the processes have a shared mailbox
```
send(A, message) //A is the name of the mailbox
receive(A, message)
```

A communication link in this scheme has the following properties:
- A link is established between a pair of processes only if both members of the pair have a shared mailbox.
- A link may be associated with more than 2 processes.
- Between each paif of communicating processes, there may be a number of different links, with each link corresponding to one mailbox.

```
P1 sends a message to the mailbox A
P2, P2 receive() from A
Which process will receive the message sent by P1?
```
The answer depends on wich of the following methods we choose:
- Allow a link to be associated with 2 processes at most.
- Allow at most 1 process at a time to execute a `receive()` operation.
- Allow the system to select arbitrarily which process will receive the message (either P2, P3, but not both, will receive the message). The system also may define an algorithm for selecting which process will receive the message (Round Robin). The system may identify the receiver to the sender.

> A mailbox maybe ==owned== either by a ==process== or by the ==OS==.

## Synchronization and Asynchronization
Message passing may be either blocking or nonblocking -- also known as synchronous and asynchronous.
==Blocking send: ==The sending procress is blocked until the message is received by the receiving process or by the mailbox.
==Nonblocking send:== The sending process sends the message and resumes operation.
==Blocking receive:== The receiver blocks until a message is available.
==Nonblocking receive==: The receiver retrieves either a valid message or a null.

## Buffering
Whether communication is direct or indirect, messages exchanged by communicating processes reside in a temporary queue. Such queues can be implemented in 3 ways:
- ==Zero capacity==: The queue has a maximum length of zero; thus, the link cannot have any messages waiting for it. In this case, the sender must block until the recipient receives the message.
- ==Bounded capacity:== The queue has finite length n; thus, at most n messages can reside in it. If the queue is not full when a new message is sent, the message is placed in the queue and the sender can continue execution without waiting. The links capacity is finite, however. If the link is full, the sender must block until space is available in the queue. 
- ==Unbounded capacity:== The queues length is potentially infinite; thus, any number of messages can wait in it. The sender never blocks.
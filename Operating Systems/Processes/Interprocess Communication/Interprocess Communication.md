Process executing concurrently in the OS:
- Independent process: They cannot affect or be affected by the other processes executing in the system.
- Cooperating processes: They can affect or be affected by the other processes executing in the system. (Any process that shares data with other processes is a cooperating process.)

<u>Process Cooperation Environment: </u>
- Information sharing
- Computation speedup (Concurrency)
- Modularity
- Convenience

Cooperating processes require an interprocess communication (IPC) mechanism that will allow them to exchange data and information.
There are two fundamental models of interprocess communication:
1. ==Shared memory==
2. Message passing
- In the shared-memory model, a region of memory that is shared by cooperating processeses is established. Processes can then exchange information  by reading and writing data to the shared region.
- In the message passing model, communication takes place by means of messages exchanged betweeen the cooperating processes.
![[Pasted image 20230425104641.png]]
![[Pasted image 20230425104929.png]]
Interprocess communication using shared memory requires communicating processes to establish a region of shared memory.

> A shared-memory region resides in the address space of the process creating the shared-memory segment.

>Other processes that wish to communicate using this shared-memory segment must attach it to their address space.

>Normally, OS tries to prevent 1 process from accessing another process's memory. Shared-memory requires 2 or more processes agree to remove this restriction.

## Producer Consumer Problem

>*A producer process produces information that is consumed by a consumer process*.

%%Example: A compiler produce assembly code, which is consumed by an assembler. The assembler in return produce object modules, which are consumed by the loader.%%

- One solution: Shared-memory
- Allow producer and consumer processes to run concurrently, we must have available a ==buffer of items== that can be filled by the producer and emptied by the consumer.
- This buffer will ==reside in a region of memory== that is shared by the producer and consumer processes.
- A producer can producer one item while the consumer is consuming another item.
- The producer and consumer must be synchronized, so that the consumer does not try to consume on item that has not yet been produced.

## Two kinds of buffers
### Unbounded Buffer
- Places no practical limit on the size of the buffer.
	The consumer may have to wait for new items
	However, the producer can always produce new items.

### Bounded Buffer
- Assumes a fixed buffer size.
	The consumer must wait if the buffer is empty
	And the producer must wait if the buffer is full.

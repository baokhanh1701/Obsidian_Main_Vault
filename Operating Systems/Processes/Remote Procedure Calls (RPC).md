RPC is a protocol that one program can use to request a service from a program located in another computer on a network without having to understand the network's details.
- It is similar in many respects to the IPC mechanism.
- However, because we are dealing with an environment in which the processes are executing on separate systems, we must use a message based communication scheme to provide remote service.
- In contrast to the IPC facility, the messages exchanged in RPC communication are well-structured and are thus no longer just packets of data.
- Each message is addressed to an RPC daemon listening to a port on  the remote system, and each contains an identifier of the function to execute and the parameters to pass to that function.
- The function is then executed as requested, and any output is sent back to the requester in a separate message.

**The semantics of RPCs allow a client to invoke a procedure on a remote host as it would invoke a procedure locally

- The RPC system hides the details that allow communication to take place by providing a stub on the client side.
- Typically, a separate stub exists for each separate remote procedure.
- When the client invokes a remote procedure, the RPC syscalls the appropriate stub, passing it the parameters provided to the remote procedure. This stub locates the prot on tkhe server and marshals the parameters.
- Parameter marshalling involves packaging the parameters into a form that can be transmitted over a network.
- The stub then transmits a message to the server using message passing.
- A similar stub on the Server side receives this message and invokes the procedure on the server.
- If necessary, return values are passed back to the client using the same technique.

![[Pasted image 20230425153859.png]]




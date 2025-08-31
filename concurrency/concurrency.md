# Task Management and Concurrency

FreeRTOS provides a task-based concurrency model, where each task represents an independent thread of execution. Tasks are the basic units of scheduling and synchronization in FreeRTOS.


## Inter-Task Communication and Synchronization
FreeRTOS provides various primitives for inter-task communication and synchronization [1]:
- Queues: Allow tasks to send and receive messages in a FIFO manner.
- Semaphores: Used for synchronization and resource sharing between tasks.
- Mutexes: Provide mutual exclusion and priority inheritance for resource protection.
- Stream Buffers: Allows streams of bytes to be sent between tasks.
- Message Buffers: Allows variable byte length messages to be sent between tasks.

These primitives facilitate safe and efficient data sharing and coordination between tasks, preventing race conditions and deadlocks.

## Differences from General-Purpose OS
FreeRTOS task management and concurrency differ from general-purpose OS in several aspects:
- Lightweight and deterministic task creation and switching
- No advanced scheduling features like CPU affinity or load balancing
- No support for advanced concurrency models like parallel loops or asynchronous I/O


## Sources
[1] FreeRTOS Inter-Task Communication - https://docs.aws.amazon.com/freertos/latest/userguide/inter-task-coordination.html
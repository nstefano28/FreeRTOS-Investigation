# CPU Virtualization and Scheduling

FreeRTOS achieves CPU virtualization through a preemptive, priority-based scheduler.[1].

## Scheduling Algorithm
FreeRTOS uses a fixed-priority scheduling algorithm, where each task is assigned a priority level. The scheduler always selects the highest-priority task that is ready to run. If multiple tasks have the same priority, they are scheduled in a round-robin fashion [1].

The FreeRTOS scheduler supports the following task states:
- **Running**: The task is currently executing on the CPU.
- **Ready**: The task is ready to run but not currently executing.
- **Blocked**: The task is waiting for an event or resource.
- **Suspended**: The task is explicitly suspended and not considered for scheduling.

The scheduler maintains a ready list for each priority level, which contains the tasks that are ready to execute. When a task becomes ready, it is added to the appropriate ready list based on its priority. The scheduler selects the highest-priority task from the ready lists to execute on the CPU.

## Context Switching
Context switching is the process of saving the state of the currently running task and restoring the state of the next task to be executed. FreeRTOS performs context switching in the following scenarios:

1. **When a higher-priority task becomes ready**: If a task with a higher priority than the currently running task becomes ready, the scheduler immediately preempts the running task and switches to the higher-priority task.

2. **When a task voluntarily yields the CPU**: A task can voluntarily give up the CPU by calling the `taskYIELD()` function. This triggers a context switch to the next ready task with the same or lower priority.

3. **When a task is blocked or suspended**: If a task becomes blocked or is explicitly suspended, the scheduler performs a context switch to the next ready task with the highest priority.

FreeRTOS minimizes the overhead associated with saving and restoring task states. The context switching method is typically optimized for each supported architecture.

## Real-Time Scheduling
FreeRTOS provides deterministic real-time behavior through its scheduling algorithms. It supports both time-slicing and cooperative scheduling:
- **Time-slicing**: Tasks with equal priorities are automatically time-sliced, allowing them to share the CPU in a fair manner.
- **Cooperative scheduling**: Tasks can voluntarily yield the CPU using the `taskYIELD()` function [1].

FreeRTOS also offers various scheduling APIs for task management, such as `vTaskPrioritySet()`, `vTaskSuspend()`, and `vTaskResume()`.

## Differences from General-Purpose OS
FreeRTOS scheduling differs from general-purpose OS in several aspects:
- Emphasis on real-time determinism and low latency
- Minimal overhead and memory footprint
- No advanced scheduling algorithms like multilevel feedback queues



## Sources
[1] FreeRTOS Scheduling - https://www.freertos.org/Documentation/02-Kernel/02-Kernel-features/01-Tasks-and-co-routines/04-Task-scheduling

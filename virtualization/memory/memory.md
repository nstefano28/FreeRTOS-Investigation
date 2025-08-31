# Memory Management

FreeRTOS provides a lightweight memory management system tailored for embedded devices with limited RAM. It focuses on efficient memory allocation and minimizing fragmentation.

## Memory Allocation
FreeRTOS offers dynamic memory allocation through its heap management system. FreeRTOS supports multiple heap implementations, each with different tradeoffs between performance, memory overhead, and fragmentation [1]:
1. **Heap_1**: A simple, compact implementation with no support for free operations.
2. **Heap_2**: A best-fit allocator with support for free operations but higher fragmentation.
3. **Heap_3**: A basic wrapper around the C standard library's `malloc()` and `free()` functions.
4. **Heap_4**: A memory allocator optimized for low fragmentation and deterministic behavior.
5. **Heap_5**: A memory allocator that combines the features of Heap_2 and Heap_4.

The choice of heap implementation depends on the specific requirements of the embedded application.

## Memory Allocation APIs
FreeRTOS provides a set of API functions for dynamic memory allocation [1]:

- `pvPortMalloc(size_t xSize)`: Allocates a block of memory of the specified size from the heap.
- `vPortFree(void *pv)`: Frees a previously allocated block of memory.
- `xPortGetFreeHeapSize()`: Returns the total amount of free heap space.
- `xPortGetMinimumEverFreeHeapSize()`: Returns the minimum amount of free heap space that has ever been available.

These APIs allow tasks to dynamically allocate and free memory as needed.


## Differences from General-Purpose OS
FreeRTOS memory management differs from general-purpose OS in several aspects:
- No virtual memory or paging mechanisms
- Limited memory protection features
- Focus on compact and deterministic memory allocation
- Customizable heap implementations for specific embedded requirements



## Sources
[1] FreeRTOS Heap Implementations - https://www.freertos.org/Documentation/02-Kernel/02-Kernel-features/09-Memory-management/01-Memory-management

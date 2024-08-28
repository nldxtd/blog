---
author: nldxtd
title: Record of my self-retained questions in CS areas
date: 2021-09-13
---

I alaways came across questions in computer science areas like programming languages, computer network, operating system. In this article I will record some of the basic questions I encountered over the years, if the question is complecated I will consider making it into a blog...

# Programming languages and compiler

# Computer network

Computer network, connect our isolated computer into Internet which now make up our world. Generally speaking, coumputer network is about how computer send message to and recieve back from other computer. A computer's network stack is made of 7 layers, each plays its role. A network path between 2 computers is called a route, which can pass netword hardware like router and exchanger.

# Operating system

Operating system, aka OS, performs as the connection between user software and underlying hardware, it provide system apis to be called by the user program so the computer can behave in our will. There are several topics to be involved in this region, such as the bacis operating unit, process communication, system call(exceptions/faults/interrupts), memory management, file system, concurrency and sychronization...

## What's the connection and difference between process and thread?

**Process**: A actual running program instance in operating system, it contains all the resources needed to run a program, such as memory, file description, environment variables.

**Thread**: A minimal unit of execution within a process,i t represents a sequence of instructions that can be executed by the CPU.

So each process has at least one thread which is called the main thread normally, the operating system actually schedules on thread to premote the execution of a program.

### Differences Between Process and Thread

| **Aspect**                | **Process**                                              | **Thread**                                               |
|---------------------------|----------------------------------------------------------|----------------------------------------------------------|
| **Definition**            | An independent program running in its own memory space.  | A smaller, lightweight unit of execution within a process.|
| **Memory Space**          | Has its own separate memory space.                       | Shares the memory space of its parent process.            |
| **Resource Allocation**   | More resource-intensive (e.g., memory, file descriptors).| Less resource-intensive; shares resources with other threads.|
| **Isolation**             | Processes are isolated from each other.                  | Threads within a process are not isolated; they can affect each other.|
| **Communication**         | Inter-process communication (IPC) is required for communication between processes (e.g., pipes, sockets). | Threads can directly communicate with each other by reading/writing shared memory.|
| **Context Switching**     | More expensive due to the need to switch memory space and resources. | Less expensive since threads share the same memory space.|
| **Creation Overhead**     | Higher overhead in terms of time and system resources.   | Lower overhead, making thread creation faster and more efficient. |
| **Execution**             | Each process runs independently and can run in parallel on multiple CPUs. | Threads can run in parallel, especially on multi-core systems, within the same process.|
| **Crash Impact**          | If a process crashes, it doesn’t affect other processes. | If a thread crashes, it can potentially crash the entire process. |
| **Scheduling**            | The operating system schedules processes independently.  | The operating system schedules threads, often within the context of their parent process. |

# Computer Architechture
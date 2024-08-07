---
author: nldxtd
title: Process, thread and routine in OS
date: 2021-09-13
description: A brief introduction about process, thread and routines in modern operating system
---

The process/thread/routines set is made the foundation of computer task schedueling. Let's go through
these basic knowledge to deepen our understanding of computer.

## The usual workflow of operating system

In arch classes, we know the CPU is just an instruction processing unit, it reads instruction from the bootstraping code and start the operating system. The operating system is responsible for the schedule of different tasks. The operating system act as a control panel between the user software and hardware, enable the ability of reading from memory/devices and writing to screen, etc. OS scheduled different tasks, tell CPU where to get next instruction us PC reg, thus make up of the computer we are using today.

## Introduction to task set

In operating system, there are several kinds of tasks. The process, the thread, and the routine.
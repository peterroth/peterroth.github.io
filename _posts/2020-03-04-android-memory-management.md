---
title: Memory Management on Android
tags: memory_management android
---
In 2017 I started to follow a free and open source project that aims to protect user privacy and -data on Android systems. It is [Blokada](https://blokada.org), an ad- and tracking blocker. Since then I help it to grow its user base, have big communities on various platforms, manage the default DNS- and host lists.  
Recently I have tried to familiarise myself with its code and was especially interested in the memory management, so I thought I'd optimise that a bit. Here is what I have learnt along the way:  
On Android, applications can't utilise the full [RAM](https://en.wikipedia.org/wiki/Random-access_memory) of the device, instead, every app the user start gets a portion of it. Because Android apps are based on Java, this allocated memory is called the same way as in Java: [heap](https://docs.oracle.com/cd/E13150_01/jrockit_jvm/jrockit/geninfo/diagnos/garbage_collect.html).

## What is heap and how big is that?

Simply phrased, heap is the memory of the running application and similarly to the memory of a physical machine (PC or notebook), it has an upper limit. The manufacturer (or in custom ROMs the maintainer) decides and defines the maximum size; no app nor system configuration can change that. Newer devices have more RAM, hence, bigger heap can be allocated without problems.  
The app's memory is allocated at its start up and lasts during its runtime; so while that is not closed, killed, crashed or the device is not restarted. If the program is sent into the background, the heap isn't totally cleared, a small portion will remain allocated.  
So, how is that you can start a lot of apps but they don't run into memory problems?

## Heap management

The system tracks each memory allocation and if it determines that a piece isn't used anymore, it frees that up removing objects that are not referenced. The mechanism that reclaims unused memory is called [Garbage Collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)) (shortly: GC) and it is triggered by the underlaying Android system; it can't be started manually.  
The GC ensures the program has minimal footprint: it is necessary to be able to start other applications, have enough space in RAM to allocate heap for newer ones. This is how you can run a lot of them in parallel.  
But what happens when something needs more resource than it can access? The application crashes with an OutOfMemory (shortly: OOM) exception and the allocated memory chunk is cleared up totally.

### Additional things

If you want to read more in this topic, please refer to the [Overview of memory management](https://developer.android.com/topic/performance/memory-overview).  
It's possible to see the set limit with the [maxMemory()](https://developer.android.com/reference/java/lang/Runtime#maxMemory()) method.

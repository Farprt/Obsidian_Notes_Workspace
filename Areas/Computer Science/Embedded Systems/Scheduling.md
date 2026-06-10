---
title: "Scheduling"
type: area-note
area: computer-science
subarea: embedded-systems
status: draft
tags:
  - Computer_Science
  - Embedded_System
---
## 12.1 Basics of Scheduling
When there are fewer processors than tasks (the usual case), or when tasks must be performed at a particular time, a **scheduler** must intervene. A scheduler makes the decision about what to do next at certain points in time

### 12.1.1 Scheduling Decisions
A scheduling decision is a decision to execute a task, and it has the following three parts:
- **assignment**: which processor should execute the task;
- **ordering**: in what order each processor should execute its tasks; and
- **timing**: the time at which each task executes.
Each of these three decisions may be made at **design time**, before the program begins executing, or at **run time**, during the execution of the program.

Depending on when the decisions are made, we can distinguish a few different types of schedulers
- **fully-static scheduler**: makes all three decisions at design time. A fully-static scheduler typically does not need semaphores or locks (are difficult to realize with most modern microprocessors because the time it takes to execute a task is difficult to predict precisely, and because tasks will typically have data-dependent execution times)
- **static order scheduler(off-line scheduler):** performs the task assignment and ordering at design time, but defers until run time the decision of when in physical time to execute a task.
- static assignment scheduler: performs the assignment at design time and everything else at run time. Each processor is given a set of tasks to execute, and a **run-time scheduler** decides during execution what task to execute next.
- **fully-dynamic scheduler(on-line schedulers)**: performs all decisions at run time.

A **preemptive scheduler** may make a scheduling decision during the execution of a task, assigning a new task to the same processor.
The interruption of the first task is called **preemption**.

### 12.1.2 Task Models
For a scheduler to make its decisions, it needs some information about the structure of the program. The set of assumptions is called the **task model** of the scheduler.

In situations where a task $\tau \in T$ executes repeatedly, we need to make a distinction between the task τ and the task executions τ1, τ2, · · · .

Task executions may have precedence constraints, a requirement that one execution precedes another. If execution i must precede j, we can write i < j.

![[task-execution-timing-model.png]]

For a task execution i, we define
- **release time** $r_{i}$ (also called the arrival time) to be the earliest time at which a task is enabled. 
- **start time** $s_{i}$ to be the time at which the execution actually starts.
- **finish time** $f_{i}$ to be the time at which the task completes execution.
- The **response time** $o_{i}$ is given by $o_{i}=f_{i}-r_{i}$
- **execution time** $e_{i}$ of $\tau_{i}$ is defined to be the total time that the task is actually executing.
- The **deadline** $d_{i}$ is the time by which a task must be completed.

A scheduler may use priority rather than (or in addition to) a deadline. A priority-based scheduler assumes each task is assigned a number called a priority, and the scheduler will always choose to execute the task with the highest priority

## 12.2 Rate Monotonic Scheduling

Consider a scenario with $T=\{\tau_{1},\tau_{2},\dots,\tau _{n}\}$ of n tasks, where the tasks must execute
periodically.
Specifically, we assume that each task τi must execute to completion exactly once in each time interval $p_{i}$. We refer to pi as the **period** of the task.

The simplest form of the problem has just two tasks, T = {τ1, τ2} with execution times
e1 and e2 and periods $p_{1}$ and $p_{2}$, as depicted in Figure 12.2.
If these two tasks are to execute on the same processor, then it is clear that a non-preemptive scheduler will not yield a feasible schedule.
![[rate-monotonic-scheduling-example.png]]

The figure 12.3 assumes that the time it takes to perform the preemption, called the context switch time, is negligible.

For the two task case, it is easy to show that among all preemptive fixed priority schedulers, RM is optimal with respect to feasibility, under the assumed task model with negligible context switch time. 

First note that the utilization of n independent tasks with execution times $e_{i}$ and periods $p_{i}$ can be written
$$
\mu=\sum_{i=1}^n \frac{e_{i}}{p_{i}}
$$
If µ = 1, then the processor is busy 100% of the time.

It turns out that RM schedulers cannot always achieve 100% utilization. In particular, RM schedulers are constrained to have fixed priority.

Liu and Layland (1973) show that if µ is less than or equal to a utilization bound given by
$$
\mu\leq n(2^{1/n}-1)
$$



## 12.3 Earliest Deadline First
Given a finite set of non-repeating tasks with deadlines and no precedence constraints, a simple scheduling algorithm is **earliest due date (EDD)**, also known as Jackson’s algorithm.

The EDD strategy simply executes the tasks in the same order as their deadlines, with the one with the earliest deadline going first. If two tasks have the same deadline, then their relative order does not matter.


> [!NOTE] Theorem 12.2
> Given a finite set of non-repeating tasks $T=\{\tau_{1},\tau_{2},\dots,\tau_{n}\}$ with associated deadlines d1, d2, · · · , dn and no precedence constraints, an EDD schedule is optimal in the sense that it minimizes the maximum lateness, compared to all other possible orderings of the tasks.

However, EDD does not support arrival of tasks, and hence also does not support periodic or repeated execution of tasks. Fortunately, EDD is easily extended to support these, yielding what is known as **earliest deadline first (EDF)** or Horn’s algorithm


> [!NOTE] Theorem 12.3
> Given a set of n independent tasks T = {τ1, τ2, · · · , τn} with associated deadlines d1, d2, · · · , dn and arbitrary arrival times, any algorithm that at any instant executes the task with the earliest deadline among all arrived tasks is optimal with respect to minimizing the maximum lateness.

- Disadvantage: Although EDF is more expensive to implement than RM, in practice its performance is generally superior.
- Advantage:
1. First, RM is optimal with respect to feasibility only among fixed priority schedulers, whereas EDF is optimal w.r.t. feasibility among dynamic priority schedulers. 
2. In addition, EDF also minimizes the maximum lateness.
3. Also, in practice, EDF results in fewer preemptions (see Exercise 2), which means less overhead for context switching. This often compensates for the greater complexity in the implementation. 
4. In addition, unlike RM, any EDF schedule with less than 100% utilization can tolerate increases in execution times and/or reductions in periods and still be feasible. (sets with utilization up to 100%)

Note that EDF is a dynamic priority scheduling algorithm. If a task is repeatedly executed, it may be assigned a different priority on each execution.

Given a fixed, finite set of tasks with deadlines, Lawler’s strategy constructs the schedule backwards, choosing first the last task to execute. The last task to execute is the one on which no other task depends that has the latest deadline. The algorithm proceeds to construct the schedule backwards, each time choosing from among the tasks whose dependents have already been scheduled the one with the latest deadline. For the previous example, the resulting schedule, labeled LDF in Figure 12.7, is feasible. Lawler’s algorithm is called **latest deadline first (LDF)**. LDF is optimal in the sense that it minimizes the maximum lateness, and hence it is also optimal with respect to feasibility. However, it does not support arrival of tasks.

## 12.5 Multiprocessor Scheduling

### 12.5.1 As Soon/Late As Possible(ASAP, ALAP)
![[asap-alap-scheduling-example.png]]

### 12.5.2 List-Scheduling
![[list-scheduling-example.png]]
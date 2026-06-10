---
title: "Dataflow Models"
type: area-note
area: computer-science
subarea: embedded-systems
status: draft
---
In this section, we consider MoCs that are much more asynchronous than SR. If a reaction of actor A requires data produced by a reaction of actor B, then the reaction of A must occur after the reaction of B. A MoC where such data dependencies are the key constraints on reactions is called a dataflow model of computation. There are several variants of dataflow MoCs, a few of which we consider here.

### 6.3.1 Dataflow Principles
In dataflow models, the signals providing communication between the actors are sequences of message, where each message is called a token. That is, a signal s is a partial function of the form
$$
s:\mathbb{N}\to V_{s}
$$
A (determinate) actor will be described as a function that maps input sequences to output sequences. We will actually use two functions, 
- an **actor function**, which maps entire input sequences to entire output sequences, 
- a **firing function**, which maps a finite portion of the input sequences to output sequences, as illustrated in the following example.

![[dataflow-actor-firing-function.png]]
 Suppose that this is a Scale actor parameterized by a parameter $a\in \mathbb{R}$. 
 Then $F(x_{1},x_{2},x_{3},\dots)=(ax_{1},ax_{2},ax_{3},\dots)$Suppose that when the actor fires, it performs one multiplication in the firing.
 Then the firing function f operates only on the first element of the input sequence, so $f(x_{1},x_{2},x_{3},\dots)=f(x_{1})=(ax_{1})$

In the above example, the firing function can be invoked if one or more tokens are available on the input. The rule requiring one token is called a **firing rule** for the Scale actor. A firing rule specifies the number of tokens required on each input port in order to fire the actor.

Since the firing of the actors is asynchronous, a token sent from one actor to another must be buffered; it needs to be saved until the destination actor is ready to consume it. When the destination actor fires, it consumes one or more input tokens. After being consumed, a token may be discarded 

Dataflow models pose a few interesting problems. 
- One question is how to ensure that the memory devoted to buffering of tokens is bounded. A dataflow model may be able to execute forever (or for a very long time); this is called an **unbounded execution**. For an unbounded execution, we may have to take measures to ensure that buffering of unconsumed tokens does not overflow the available memory.
- A second problem that may arise is **deadlock**. Deadlock occurs when there are cycles.  The Delay actor of Example 6.9 can help prevent deadlock because it is able to produce an initial output token without having any input tokens available.

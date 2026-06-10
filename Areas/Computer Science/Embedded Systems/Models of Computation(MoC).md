---
title: "Models of Computation(MoC)"
type: area-note
area: computer-science
subarea: embedded-systems
status: draft
---
#Embedded_System #Computer_Science 

This chapter focuses on the semantics of **concurrent** composition. The word “concurrent” literally means “running together.” A system is said to be concurrent if different parts of the system (components) conceptually operate at the same time.

The components we consider in this chapter are actors, which react to stimuli at input ports and produce stimuli on output ports.

The semantics of a concurrent composition of actors is governed by three sets of rules that we collectively call a **model of computation (MoC)**.

# 6.1 Structure of Models
In this chapter, we assume that models consist of fixed interconnections of actors like that shown in Figure 6.1(a).

As suggested in Figure 6.1(b-d), any actor network can be reduced to a rather simple form.  If we rearrange the actors as shown in Figure 6.1(b), then the actors form a [[Side-by-Side Composition]] indicated by the box with rounded corners. This box is itself an actor F as shown in Figure 6.1(c) whose input is a three-tuple (s1, s2, s3) of signals and whose output is the same three-tuple of signals. If we let s = (s1, s2, s3), then the actor can be depicted as in Figure 6.1(d), which hides all the complexity of the model.
![[actor-interconnection-models-feedback.png]]

in Figure 6.1(a), actor A may be a function relating signals s1 and s2 as follows,
$$
s_{2}=A(s_{1})
$$
Similarly, actor B relates three signals by
$$
s_{1}=B(s_{2},s_{3})
$$
ctor C is a bit more subtle, since it has no input ports.
Let {∅} be the singleton set, so C can only be applied to ∅. The function C is then given by
$$
C(\emptyset)=s_{3}
$$
This can be represented compactly using the function F in Figure 6.1(d), which is
$$
F(s_{1},s_{2},s_{3})=(B(s_{2},s_{3}),A(s_{1}),C(\emptyset))
$$



> [!NOTE] Fixed-Point Semantics
> the reduced form of Figure 6.1(d) becomes
  $$s=F(s)$$
> where s = (s1, s2, s3).  Its complexity lies in the definition of the function F and the structure of the domain and range of F.
> 
> Given any function F : X → X for any set X, if there is an x ∈ X such that F(x) = x, then x is called a **fixed point**.
> In the SR model of computation, the execution of all actors is simultaneous and instantaneous and occurs at ticks of the global clock. If the actor is determinate, then each such execution implements a function called a **firing function**.
## 6.2 [[Synchronous-Reactive(SR) Models]]

An SR model is a discrete system where signals are absent at all times except (possibly) at **ticks** of a **global clock**. Conceptually, execution of a model is a sequence of global reactions that occur at discrete times, and at each such reaction, the reaction of all actors is simultaneous and instantaneous.

### 6.2.1 Feedback Models

Consider first a simpler example shown in Figure 6.2.

If A is in state s1 when that reaction occurs, then the only possible value for s(n) is s(n) = absent because a reaction must take one of the transitions out of s1, and both of these transitions emit absent. Moreover, once we know that s(n) = absent, we know that the input port x has value absent, so we can determine that A will transition to state s2.

If A is in state s2 when the reaction occurs, then the only possible value for s(n) is s(n) = present, and the machine will transition to state s1. Therefore, s alternates between absent and present.

The semantics of machine A in the feedback model is therefore given by Figure 6.3.
![[simple-feedback-model-semantics.png]]

in each state i we can define a function ai that maps input values to output values,
$$
a_{i}:\left\{ \text{present},\text{absent} \right\}\to \left\{ \text{present},\text{absent} \right\} 
$$
where the function depends on the state the machine is in. This function is defined by the update function.

For the example in Figure 6.2, if the machine is in state s1, then $a_{s_{1}}(x)=\text{absent}$ for all  x ∈ {present, absent}.

The function ai is called the firing function for state i.  Given a firing function, to find the value s(n) at the n-th reaction, we simply need to find a value s(n) such that
$$
s(n)=a_{i}(s(n))
$$
Such a value s(n) is called a fixed point of the function ai.

### 6.2.2 Well-Formed and Ill-Formed Models

There are two potential problems that may occur when seeking a fixed point. 
First, there may be no fixed point. 
Second, there may be more than one fixed point. If either case occurs in a reachable state, we call the system ill formed. Otherwise, it is well formed.

In state s1, we get the unique fixed point s(n) = absent. 
In state s2, however, there is no fixed point. If we attempt to choose s(n) = present, then the machine will transition to s1 and its output will be absent.  But the output has to be the same as the input, and the input is present, so we get a contradiction. A similar contradiction occurs if we
attempt to choose s(n) = absent.
![[ill-formed-feedback-no-fixed-point.png]]

 In state s1, both s(n) = absent and s(n) = present are fixed points.  Either choice is valid. Since state s1 is reachable, this feedback model is ill formed.
![[ill-formed-feedback-multiple-fixed-points.png]]

### 6.2.3 Constructing a Fixed Point

If the type Vs of the signal s or the signals it is an aggregate of is finite, then one way to find a fixed point is by exhaustive search, which means to try all values. If exactly one fixed point is found, then the model is well formed. However, exhaustive search is expensive

For each reachable state i,
1. Start with s(n) unknown.
2. Determine as much as you can about fi(s(n)), where fi is the firing function in state i. Note that in this step, you should use only the firing function, which is given by the state machine; you should not use knowledge of how the state machine is connected on the outside.
3. Repeat step 2 until all values in s(n) become known (whether they are present and what their values are), or until no more progress can be made.
4. If unknown values remain, then reject the model.

This procedure may reject models that have a unique fixed point. Consider machine D shown in Figure 6.6. In state s1, if the input is unknown, we cannot immediately tell what the output will be.

A state machine for which the procedure works in all reachable states is said to be constructive
![[well-formed-feedback-fixed-point.png]]

## 6.3 [[Dataflow Models]] of Computation
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

### 6.3.2 Synchronous Dataflow

Synchronous dataflow (SDF) is a constrained form of dataflow where for each actor, every firing consumes a fixed number of input tokens on each input port and produces a fixed number of output tokens on each output port

Consider a single connection between two actors, A and B, as shown in Figure 6.8. The notation here means that when A fires, it produces M tokens on its output port, and when B fires, it consumes N tokens on its input port. M and N are positive integers. Suppose that A fires qA times and B fires qB times. All tokens that A produces are consumed by B if and only if the following balance equation is satisfied
$$
q_{A}M=q_{B}N
$$

![[missing-sdf-balance-equation-figure-placeholder.png]]

An SDF model that has a non-zero solution to the balance equations is said to be consistent. If the only solution is zero, then it is inconsistent. An inconsistent model has no unbounded execution with bounded buffers.

Consistency is sufficient to ensure bounded buffers, but it is not sufficient to ensure that an unbounded execution exists. In particular, when there is feedback, as in Figure 6.1, then deadlock may occur. Deadlock bounds an execution.
To allow for feedback, the SDF model treats Delay actors specially. Recall from Example 6.9, that the Delay actor is able to produce output tokens before it receives any input tokens, and then it subsequently behaves like a trivial SDF actor that copies inputs to outputs.

Figure 6.11 shows an SDF model with initial tokens on a feedback loop. These replace a Delay actor that is able to initially produce four tokens. The balance equations are
$$
\begin{align}
3q_{A}=2q_{B} \\
2q_{B}=3q_{A}
\end{align}
$$
The least positive integer solution is qA = 2, and qB = 3, so the model is consistent.
 With four initial tokens on the feedback connection, as shown, the following schedule can be repeated forever,
$$
A, B, A, B, B.
$$
Were there any fewer than four initial tokens, however, the model would deadlock. If there were only three tokens, for example, then A could fire, followed by B, but in the resulting state of the buffers, neither could fire again.


![[missing-sdf-initial-tokens-feedback-placeholder.png]]
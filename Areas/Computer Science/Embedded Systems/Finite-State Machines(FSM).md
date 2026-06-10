---
title: "Finite-State Machines(FSM)"
type: area-note
area: computer-science
subarea: embedded-systems
status: draft
---
#Computer_Science #Embedded_System 

## 3.2 The Notion of State
Intuitively, the state of a system is its condition at a particular point in time.

Formally, we define the state to be an encoding of everything about the past that has an effect on the system’s reaction to current or future inputs. The state is a summary of the past.

## 3.3 Finite-State Machines
A state machine is a model of a system with discrete dynamics that at each reaction maps valuations of the inputs to valuations of the outputs, where the map may depend on its current state. A **finite-state machine (FSM)** is a state machine where the set States of possible states is finite.

the set of states is given by $States=\left\{ State 1,State 2, State 3 \right\}$
At the beginning of each sequence of reactions, there is an initial state, State1, indicated in the diagram by a dangling arrow into it.

### 3.3.1 Transitions
Transitions between states govern the discrete dynamics of the state machine and the mapping of input valuations to output valuations.
![[garage-door-fsm-model.png]]
### 3.3.2 When a Reaction Occurs
Nothing in the definition of a state machine constrains when it reacts. The environment determines when the machine reacts. Chapters 5 and 6 describe a variety of mechanisms and give a precise meaning to terms like event triggered and time triggered.

If no guard on any transition out of the current state evaluates to true, then the machine will remain in the same state.

 If the input is absent and no guard on any transition out of the current state evaluates to true, then the machine will **stutter**.
![[fsm-default-transition.png]]A convenient way to do this is using a default transition, shown in Figure 3.6. In that figure, the default transition is denoted with dashed lines and is labeled with “true / ”. A default transition is enabled if no non-default transition is enabled and if its guard evaluates to true.

### 3.3.3 Update Functions
a finite-state machine is a five-tuple
$$
(States, Inputs, Outputs, update, initialState)
$$
where
- States is a finite set of states;
- Inputs is a set of input valuations;
- Outputs is a set of output valuations;
- update : States × Inputs → States × Outputs is an update function, mapping a state and an input valuation to a next state and an output valuation;
- initialState is the initial state.

The FSM reacts in a sequence of reactions.  We can number these states starting with 0 for the initial state. 
Specifically, **let $s:\mathbb{N}\to States$ be a function that gives the state of an FSM at reaction $n\in \mathbb{N}$. Initially, s(0) = initialState.**
Let $x:\mathbb{N}\to Inputs$ and $y:\mathbb{N}\to \text{Outputs}$ denote that input and output valuations at each
reaction. The dynamics of the state machine are given by the following equation:
$$
(s(n+1),y(n))=update(s(n),x(n))
$$

![[fsm-update-function-example.png]]

## 3.4 Extended State Machines
An **extended state machine** solves this problem by augmenting the FSM model with variables that may be read and written as part of taking a transition between states.

That figure shows a variable c, declared explicitly at the upper left to make it clear that c is a variable and not an input or an output. The transition indicating the initial state initializes the value of this variable to zero.
![[extended-garage-door-state-machine.png]]

The general notation for extended state machines is shown in Figure 3.9. This differs
from the basic FSM notation of Figure 3.3 in three ways. 

First, variable declarations are shown explicitly to make it easy to determine whether an identifier in a guard or action refers to a variable or to an input or an output. 

Second, upon initialization, variables that have been declared may be initialized. The initial value will be shown on the transition that indicates the initial state. 

Third, transition annotations now have the form
$$
\begin{align}
 & \text{guard/output action} \\
 & \text{set action(s)}
\end{align}
$$
![[extended-state-machine-notation.png]]

## 3.5 Nondeterminism
Most interesting state machines react to inputs and produce outputs. These inputs must come from somewhere, and the outputs must go somewhere. We refer to this “somewhere” as the **environment** of the state machine.

If for any state of a state machine, there are two distinct transitions with guards that can evaluate to true in the same reaction, then the state machine is nondeterministic. In a diagram for such a state machine, the transitions that make the state machine nondeterministic may be colored red.
![[nondeterministic-pedestrian-fsm.png]]

In both cases, a nondeterministic FSM specifies a family of possible reactions rather than a single reaction. Operationally, all reactions in the family are possible. A model that specifies likelihoods (in the form of probabilities) is a **stochastic model**, quite distinct from a nondeterministic model.

### 3.5.1 Formal Model

Formally, a nondeterministic FSM is represented as a five-tuple, similar to a deterministic FSM.
$$
\text{(States, Inputs, Outputs, possibleUpdates, initialState)}
$$

- possibleUpdates : $\text{States}\times \text{Inputs}\to2^{\text{States}\times \text{Inputs}}$ is an **update relation**, mapping a state and an input valuation to a set of possible (next state, output valuation) pairs;

The form of the function possibleUpdates indicates there can be more than one next state and/or output valuation given a current state and input valuation.

![[nondeterministic-fsm-formal-model.png]]


# 5. Composition of State Machines

The first composition technique we consider is concurrent composition. Two or more state machines react either simultaneously or independently. If the reactions are simultaneous, we call it **synchronous composition**. If they are independent, then we call it **asynchronous composition**.

## 5.1 Concurrent Composition
To study concurrent composition of state machines, we will proceed through a sequence
of patterns of composition. These patterns can be combined to build arbitrarily complicated systems. 
We begin with the simplest case, side-by-side composition, where the state machines being composed do not communicate. 
We then consider allowing communication through shared variables, showing that this creates significant subtleties that can complicate modeling. 
We then consider communication through ports, first looking at serial composition, then expanding to arbitrary interconnections. We consider both synchronous and asynchronous composition for each type of composition.

### 5.1.1 Side-by-Side Synchronous Composition

The first pattern of composition that we consider is **[[Side-by-Side Composition]]**, illustrated for two actors in Figure 5.2.
![[side-by-side-composition-actors.png]]

In the simplest scenario, if the two actors are extended state machines with variables, then those variables are also disjoint. We will later consider what happens when the two state machines share variables. Under synchronous composition, a reaction of C is a simultaneous reaction of A and B.

A synchronous side-by-side composition of finite state machines is itself an FSM.
![[side-by-side-composition-fsm-example.png]]

Moreover, if the two state machines A and B are deterministic, then the synchronous side-by-side composition is also deterministic. We say that a property is compositional if a property held by the components is also a property of the composition. For synchronous side-by-side composition, determinism is a compositional property.

state machines A and B are given by the five tuples,
$$
\begin{align}
A=(States_{A}, Inputs_{A}, Outputs_{A}, update_{A}, initialState_{A}) \\
B=(States_{B}, Inputs_{B}, Outputs_{B}, update_{B}, initialState_{B})
\end{align}
$$
Then the synchronous side-by-side composition C is given by
$$
\begin{align}
 & States_{C}=States_{A}\times States_{B} \\
 & Inputs_{C}=Inputs_{A}\times Inputs_{B} \\
 & Outputs_{C}=Outputs_{A}\times Outputs_{B} \\
 & initialState_{C}=(initialState_{A},initialState_{B})
\end{align}
$$
and the update function is defined by
$$
update_{C}((s_{A},s_{B}),(i_{A},i_{B}))=((s'_{A},s'_{B}),(o_{A},o_{B}))
$$
where
$$
(s'_{A},o_{A})=update_{A}(s_{A},i_{A})
$$
and
$$
(s'_{B},o_{B})=update_{B}(s_{B},i_{B})
$$
![[synchronous-side-by-side-composition-semantics.png]]

### 5.1.2 Side-by-Side Asynchronous Composition
In an asynchronous composition of state machines, the component machines react independently. This statement is rather vague, and in fact, it has several different interpretations. Each interpretation gives a semantics to the composition. The key to each semantics is how to define a reaction of the composition C in Figure 5.2. Two possibilities are:

- Semantics 1. A reaction of C is a reaction of one of A or B, where the choice is nondeterministic.
- Semantics 2. A reaction of C is a reaction of A, B, or both A and B, where the choice is nondeterministic. A variant of this possibility might allow neither to react.
Semantics 1 is referred to as an interleaving semantics, meaning that A or B never react simultaneously. Their reactions are interleaved in some order.

For the example in Figure 5.3, semantics 1 results in the composition state machine shown in Figure 5.5.  This machine is nondeterministic. From state (s1, s3), when C reacts, it can move to (s2, s3) and emit no output, or it can move to (s1, s4) and emit b.

Note that if we had chosen semantics 2, then it would also be able to move to (s2, s4).
![[asynchronous-side-by-side-composition-semantics.png]]

### 5.1.3 Shared Variables

An extended state machine has local variables that can be read and written as part of taking a transition. Sometimes it is useful when composing state machines to allow these variables to be shared among a group of machines.
![[shared-variables-composition-model.png]]

### 5.1.4 Cascade Composition

Consider two state machines A and B that are composed as shown in Figure 5.7. The output of machine A feeds the input of B. This style of composition is called cascade composition or serial composition.

In the figure, output port o1 from A feeds events to input port i2 of B. Assume the data type of o1 is V1 (meaning that o1 can take values from V1 or be absent), and the data type of i2 is V2. Then a requirement for this composition to be valid is that
$$
V_{1} \subseteq V_{2}
$$
This asserts that any output produced by A on port o1 is an acceptable input to B on port i2. The composition **type checks**.
![[cascade-composition-actors.png]]

![[cascade-composition-fsm-semantics.png]]

### 5.1.5 General Composition
Side-by-side and cascade composition provide the basic building blocks for building more complex compositions of machines.
![[general-fsm-composition-interconnections.png]]

## 5.2 Hierarchical State Machines

In this section, we consider hierarchical FSMs. 

The key idea in hierarchical state machines is state refinement. In Figure 5.13, state B has a refinement that is another FSM with two states, C and D. What it means for the machine to be in state B is that it is in one of states C or D
![[hierarchical-fsm-refinement-example.png]]
If it is C, and guard g4 is true, the transition is taken to D and action a4 is performed. But then, as part of the same reaction, the top-level FSM reacts. If guard g1 is also true, then the machine transitions to state A. It is important that logically these two transitions are simultaneous and instantaneous, so the machine does not actually go to state D.

Another subtlety is that if two (non-absent) actions are performed in the same reaction,
they may conflict.

Such subtleties can be avoided by using a **preemptive transition**, shown in Figure 5.15, which has the semantics shown in Figure 5.16. The guards of a preemptive transition are evaluated before the refinement reacts, and if any guard evaluates to true, the refinement does not react. A preemptive transition is shown with a (red) circle at the originating end of the transition.
![[hierarchical-fsm-preemptive-transition-model.png]]

Notice in Figures 5.13 and 5.14 that whenever the machine enters B, it always enters C, never D, even if it was previously in D when leaving B. The transition from A to B is called a **reset transition** because the destination refinement is reset to its initial state, regardless of where it had previously been.

In Figure 5.17, the transition from A to B is a **history transition**, an alternative to a reset transition. When a history transition is taken, the destination refinement resumes in whatever state it was last in (or its initial state on the first entry).

The semantics of the history transition is shown in Figure 5.18. The initial state is labeled (A, C) to indicate that the machine is in state A, and if and when it next enters B it will go to C. The first time it goes to B, it will be in the state labeled (B, C) to indicate that it is in state B and, more specifically, C. If it then transitions to (B, D), and then back to A, it will end up in the state labeled (A, D), which means it is in state A, but if and when it next enters B it will go to D. That is, it remembers its history, specifically where it was when it left B.
![[hierarchical-fsm-history-transition.png]]


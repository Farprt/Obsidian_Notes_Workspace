---
title: "Side-by-Side Composition"
type: area-note
area: computer-science
subarea: embedded-systems
status: draft
---
#Computer_Science #Embedded_System 

### 5.1.1 Side-by-Side Synchronous Composition

The first pattern of composition that we consider is **[[Side-by-Side Composition]]**, illustrated for two actors in Figure 5.2.
![[side-by-side-composition-actors.png]]

In the simplest scenario, if the two actors are extended state machines with variables, then those variables are also disjoint. We will later consider what happens when the two state machines share variables. Under synchronous composition, a reaction of C is a simultaneous reaction of A and B.

A synchronous side-by-side composition of finite state machines is itself an FSM.
![[side-by-side-composition-fsm-example.png]]
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

---
layout: project
type: project
image: img/eprescription-fsm.png
title: "Electronic Prescription Lifecycle FSM"
date: 2026
published: true
labels:
  - Python
  - Finite State Machines
  - Software Design
  - Test-Driven Development
  - FHIR
summary: "A deterministic finite state machine modeling the full lifecycle of an electronic prescription — from drafted through dispensed, expired, or cancelled."
---

**Source & tests:** [GitHub](https://github.com/roycenainoa/eprescription-fsm) &nbsp;·&nbsp; Python · `transitions`

<img src="../img/eprescription-fsm.png" style="height:440px; width:auto; display:block; margin:12px auto; border:1px solid #e5e7eb; border-radius:6px;">

## About

This project models the lifecycle of an electronic prescription as a deterministic finite state machine, implemented in Python with the `transitions` library. It accompanies a short research report, *Electronic Prescription Lifecycle Modeling with Finite State Machines* (Cornwell, 2026).

## States and transitions

Six discrete states — `drafted` (initial), `signed`, `transmitted`, `dispensed`, `expired`, `cancelled` — connected by the events sign, transmit, dispense, expire, and cancel. Any event that isn't valid for the active state raises an `InvalidTransitionError`, and any event dispatched against a terminal state raises a `TerminalStateError`, so illegal lifecycles are impossible by construction.

## See it run

`demo.py` walks the machine through each accepted workflow:

```text
[scenario] Standard lifecycle (drafted to dispensed)
  events: ['sign', 'transmit', 'dispense']
    sign       -> signed
    transmit   -> transmitted
    dispense   -> dispensed
  final state: dispensed   terminal: True

[scenario] Cancellation from transmitted
  events: ['sign', 'transmit', 'cancel']
    sign       -> signed
    transmit   -> transmitted
    cancel     -> cancelled
  final state: cancelled   terminal: True
```

## Beyond the core machine

It also includes a relational persistence layer, a background expiry scheduler, a FHIR `MedicationRequest` parser, and a concurrency-safe dispatch method, backed by a test suite covering the transition rules.

## Learning outcome

Modeling a real, regulated workflow as an explicit state machine made the value of the approach concrete: illegal states simply can't be reached, and the whole lifecycle is documented in one place. It also connected directly to the e-prescription domain I later worked in professionally.

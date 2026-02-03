---
name: software-engineering
description: Apply software engineering best practices including SOLID principles, design patterns (GoF), Domain-Driven Design, Event-Driven Architecture, and clean code principles from industry leaders
user-invocable: true
---

# Software Engineering Rules

> *"The best code is not the longest code, it is the most efficient code."*

## Purpose

These rules establish the methodology for designing, implementing, and maintaining high-quality software systems. Drawing from the foundational work of Eric Evans (Domain-Driven Design), Robert C. Martin (SOLID principles), the Gang of Four (Design Patterns), and the engineering practices of Netflix, Spotify, Uber, AWS, and academia (MIT, Harvard, UPV), this guide covers architecture, design patterns, and fundamental algorithms.

---

## Core Philosophy

### The Three Pillars of Software Excellence

```
┌─────────────────────────────────────────────────────────────────┐
│              SOFTWARE EXCELLENCE                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│     SIMPLICITY ─────────────────────────────────────────────    │
│     │ "The art of maximizing work not done"                     │
│     │ • Solve the problem at hand, nothing more                 │
│     │ • Three similar lines > premature abstraction             │
│     │ • Delete code freely; unused code is debt                 │
│     └───────────────────────────────────────────────────────    │
│                                                                 │
│     CLARITY ────────────────────────────────────────────────    │
│     │ "Code is read far more often than written"                │
│     │ • Intention-revealing names                               │
│     │ • Self-documenting code over comments                     │
│     │ • Explicit over implicit                                  │
│     └───────────────────────────────────────────────────────    │
│                                                                 │
│     MAINTAINABILITY ────────────────────────────────────────    │
│     │ "Plan for change, not for perfection"                     │
│     │ • Loosely coupled, highly cohesive modules                │
│     │ • Easy to understand, safe to modify                      │
│     │ • Tests as living documentation                           │
│     └───────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## SOLID Principles

### The Foundation of Object-Oriented Design

Robert C. Martin's SOLID principles are the cornerstone of maintainable object-oriented software:

```
┌─────────────────────────────────────────────────────────────────┐
│                    SOLID PRINCIPLES                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  S ─ SINGLE RESPONSIBILITY ─────────────────────────────────    │
│  │ "A class should have one, and only one, reason to change"    │
│  │                                                              │
│  │ ✓ Each module owns one piece of functionality                │
│  │ ✓ Changes to one feature affect one module                   │
│  │ ✗ God classes that do everything                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  O ─ OPEN/CLOSED ───────────────────────────────────────────    │
│  │ "Open for extension, closed for modification"                │
│  │                                                              │
│  │ ✓ Add new behavior through new code                          │
│  │ ✓ Existing code remains stable                               │
│  │ ✗ Modifying existing code for every new feature              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  L ─ LISKOV SUBSTITUTION ───────────────────────────────────    │
│  │ "Subtypes must be substitutable for their base types"        │
│  │                                                              │
│  │ ✓ Derived classes honor base class contracts                 │
│  │ ✓ No surprising behavior when substituting                   │
│  │ ✗ Square inheriting from Rectangle (classic violation)       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  I ─ INTERFACE SEGREGATION ─────────────────────────────────    │
│  │ "No client should depend on methods it doesn't use"          │
│  │                                                              │
│  │ ✓ Many specific interfaces over one general interface        │
│  │ ✓ Clients see only what they need                            │
│  │ ✗ Fat interfaces forcing unnecessary implementations         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  D ─ DEPENDENCY INVERSION ──────────────────────────────────    │
│  │ "Depend on abstractions, not concretions"                    │
│  │                                                              │
│  │ ✓ High-level modules define interfaces                       │
│  │ ✓ Low-level modules implement interfaces                     │
│  │ ✗ Direct dependencies on concrete implementations            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Design Smells (Uncle Bob)

When these principles are violated, code exhibits **design smells**:

| Smell | Description | Principle Violated |
|-------|-------------|-------------------|
| **Rigidity** | Hard to change; every change causes cascade | OCP, SRP |
| **Fragility** | Changes break unexpected parts | LSP, DIP |
| **Immobility** | Hard to reuse; too coupled | ISP, DIP |
| **Viscosity** | Easier to hack than do it right | All |
| **Needless Complexity** | Over-engineered | SRP, YAGNI |

---

## Design Patterns (Gang of Four)

### Creational Patterns

```
┌─────────────────────────────────────────────────────────────────┐
│                  CREATIONAL PATTERNS                            │
│              "How objects are created"                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FACTORY METHOD ────────────────────────────────────────────    │
│  │ Define interface for creating objects; subclasses decide     │
│  │ which class to instantiate                                   │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Class can't anticipate object types to create              │
│  │ • Class wants subclasses to specify objects                  │
│  │ • Need to localize creation logic                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ABSTRACT FACTORY ──────────────────────────────────────────    │
│  │ Create families of related objects without specifying        │
│  │ concrete classes                                             │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • System should be independent of product creation           │
│  │ • System configured with multiple product families           │
│  │ • Related objects must be used together                      │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  BUILDER ───────────────────────────────────────────────────    │
│  │ Construct complex objects step by step; same process         │
│  │ creates different representations                            │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Object requires many construction steps                    │
│  │ • Different representations needed from same process         │
│  │ • Need immutable objects with many parameters                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  SINGLETON ─────────────────────────────────────────────────    │
│  │ Ensure class has single instance; provide global access      │
│  │                                                              │
│  │ ⚠️  Use sparingly:                                           │
│  │ • Often a design smell; consider dependency injection        │
│  │ • Makes testing difficult                                    │
│  │ • Hidden dependencies                                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Structural Patterns

```
┌─────────────────────────────────────────────────────────────────┐
│                  STRUCTURAL PATTERNS                            │
│              "How objects are composed"                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ADAPTER ───────────────────────────────────────────────────    │
│  │ Convert interface of class into another interface clients    │
│  │ expect                                                       │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Want to use existing class with incompatible interface     │
│  │ • Integrating with third-party libraries                     │
│  │ • Need to create reusable class working with others          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FACADE ────────────────────────────────────────────────────    │
│  │ Provide unified interface to set of interfaces in            │
│  │ subsystem                                                    │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Need simple interface to complex subsystem                 │
│  │ • Many dependencies between clients and implementation       │
│  │ • Want to layer subsystems                                   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DECORATOR ─────────────────────────────────────────────────    │
│  │ Attach additional responsibilities to object dynamically     │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Need to add responsibilities without subclassing           │
│  │ • Extensions should be reversible                            │
│  │ • Multiple independent extensions possible                   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMPOSITE ─────────────────────────────────────────────────    │
│  │ Compose objects into tree structures; treat individual       │
│  │ and compositions uniformly                                   │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Represent part-whole hierarchies                           │
│  │ • Clients should ignore difference between compositions      │
│  │ • Tree-structured data (UI components, file systems)         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Behavioral Patterns

```
┌─────────────────────────────────────────────────────────────────┐
│                  BEHAVIORAL PATTERNS                            │
│              "How objects communicate"                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  STRATEGY ──────────────────────────────────────────────────    │
│  │ Define family of algorithms; make them interchangeable       │
│  │                                                              │
│  │ Structure:                                                   │
│  │ ┌─────────┐    ┌───────────────────┐                         │
│  │ │ Context │───▶│ <<Strategy>>      │                         │
│  │ └─────────┘    │ +execute()        │                         │
│  │                └─────────┬─────────┘                         │
│  │                    ┌─────┴─────┐                             │
│  │              ┌─────┴───┐ ┌─────┴───┐                         │
│  │              │Strategy │ │Strategy │                         │
│  │              │    A    │ │    B    │                         │
│  │              └─────────┘ └─────────┘                         │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Many related classes differ only in behavior               │
│  │ • Need different variants of algorithm                       │
│  │ • Algorithm uses data clients shouldn't know about           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  OBSERVER ──────────────────────────────────────────────────    │
│  │ Define one-to-many dependency; when one changes, all         │
│  │ dependents notified                                          │
│  │                                                              │
│  │ Structure:                                                   │
│  │ ┌───────────┐        ┌─────────────┐                         │
│  │ │ Subject   │───────▶│ Observer    │                         │
│  │ │           │ 1    * │ +update()   │                         │
│  │ │+attach()  │        └──────┬──────┘                         │
│  │ │+detach()  │               │                                │
│  │ │+notify()  │        ┌──────┴──────┐                         │
│  │ └───────────┘        │ Concrete    │                         │
│  │                      │ Observer    │                         │
│  │                      └─────────────┘                         │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Change to one object requires changing others              │
│  │ • Object should notify others without knowing who            │
│  │ • Publish-subscribe scenarios                                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMMAND ───────────────────────────────────────────────────    │
│  │ Encapsulate request as object; parameterize, queue,          │
│  │ log, support undo                                            │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Parameterize objects with actions                          │
│  │ • Queue, schedule, or execute requests at different times    │
│  │ • Support undo/redo operations                               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  STATE ─────────────────────────────────────────────────────    │
│  │ Allow object to alter behavior when internal state           │
│  │ changes                                                      │
│  │                                                              │
│  │ Use when:                                                    │
│  │ • Object behavior depends on state                           │
│  │ • Operations have large conditional statements               │
│  │ • State transitions explicit and numerous                    │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Domain-Driven Design (DDD)

### The Eric Evans Approach

> *"Complex software projects fail not because of technical challenges, but because of poor communication between technical and domain experts."*

### Strategic Design

```
┌─────────────────────────────────────────────────────────────────┐
│                  DDD STRATEGIC DESIGN                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BOUNDED CONTEXT ───────────────────────────────────────────    │
│  │ Explicit boundary within which a domain model is defined     │
│  │ and consistent                                               │
│  │                                                              │
│  │ • Each context has its own Ubiquitous Language               │
│  │ • Models in different contexts can evolve independently      │
│  │ • In microservices: often maps 1:1 with a service            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  UBIQUITOUS LANGUAGE ───────────────────────────────────────    │
│  │ Shared vocabulary between developers and domain experts      │
│  │                                                              │
│  │ • Embedded in code (class names, methods, variables)         │
│  │ • Used in conversations, documentation, tests                │
│  │ • Eliminates translation between business and tech           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CONTEXT MAPPING ───────────────────────────────────────────    │
│  │ Relationships between bounded contexts                       │
│  │                                                              │
│  │ Patterns:                                                    │
│  │ • Partnership: Two teams succeed or fail together            │
│  │ • Shared Kernel: Small shared model                          │
│  │ • Customer/Supplier: Upstream/downstream relationship        │
│  │ • Conformist: Downstream conforms to upstream                │
│  │ • Anti-Corruption Layer: Isolates from foreign model         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  CORE DOMAIN ───────────────────────────────────────────────    │
│  │ The part of the domain that differentiates your business     │
│  │                                                              │
│  │ • Should be as small as possible                             │
│  │ • Best developers should work on it                          │
│  │ • Highest investment in modeling quality                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Tactical Design

```
┌─────────────────────────────────────────────────────────────────┐
│                  DDD TACTICAL PATTERNS                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ENTITY ────────────────────────────────────────────────────    │
│  │ Object with identity that persists over time                 │
│  │                                                              │
│  │ • Has unique identifier                                      │
│  │ • Mutable state                                              │
│  │ • Equality based on ID, not attributes                       │
│  │ • Example: User, Order, Account                              │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  VALUE OBJECT ──────────────────────────────────────────────    │
│  │ Object defined by its attributes, not identity               │
│  │                                                              │
│  │ • Immutable                                                  │
│  │ • Equality based on attribute values                         │
│  │ • No side effects                                            │
│  │ • Example: Money, Address, DateRange                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  AGGREGATE ─────────────────────────────────────────────────    │
│  │ Cluster of entities/value objects treated as unit            │
│  │                                                              │
│  │ Rules:                                                       │
│  │ • One entity is the Aggregate Root                           │
│  │ • External access only through root                          │
│  │ • Root ensures consistency of the whole                      │
│  │ • Transactional boundary                                     │
│  │                                                              │
│  │ Example: Order (root) contains OrderLines                    │
│  │ ┌──────────────────────────────────┐                         │
│  │ │  Aggregate: Order               │                         │
│  │ │  ┌─────────────────────────┐    │                         │
│  │ │  │ Root: Order            │    │                         │
│  │ │  │ - orderId              │    │                         │
│  │ │  │ - customerId           │    │                         │
│  │ │  │ - status               │    │                         │
│  │ │  └──────────┬──────────────┘    │                         │
│  │ │             │                   │                         │
│  │ │  ┌──────────▼──────────────┐    │                         │
│  │ │  │ OrderLine (internal)   │    │                         │
│  │ │  │ - productId            │    │                         │
│  │ │  │ - quantity             │    │                         │
│  │ │  │ - price                │    │                         │
│  │ │  └─────────────────────────┘    │                         │
│  │ └──────────────────────────────────┘                         │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  REPOSITORY ────────────────────────────────────────────────    │
│  │ Abstraction for accessing aggregates                         │
│  │                                                              │
│  │ • Shields domain from persistence details                    │
│  │ • Operates on aggregates, not entities                       │
│  │ • Feels like in-memory collection                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  DOMAIN SERVICE ────────────────────────────────────────────    │
│  │ Stateless operation that doesn't belong to entity            │
│  │                                                              │
│  │ • Implements domain logic spanning multiple aggregates       │
│  │ • Named after domain activity                                │
│  │ • No identity or state                                       │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FACTORY ───────────────────────────────────────────────────    │
│  │ Encapsulates complex creation logic                          │
│  │                                                              │
│  │ • Creates aggregates in valid state                          │
│  │ • Hides construction complexity                              │
│  │ • Ensures invariants from creation                           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Event-Driven Architecture (EDA)

### Core Concepts

```
┌─────────────────────────────────────────────────────────────────┐
│              EVENT-DRIVEN ARCHITECTURE                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ┌─────────────┐     ┌─────────────┐     ┌─────────────┐        │
│  │  Producer   │────▶│  Event Bus  │────▶│  Consumer   │        │
│  │             │     │  (Broker)   │     │             │        │
│  └─────────────┘     └─────────────┘     └─────────────┘        │
│                                                                 │
│  KEY CHARACTERISTICS:                                           │
│  • Loose coupling between components                            │
│  • Asynchronous communication                                   │
│  • Scalability through parallel processing                      │
│  • Resilience through decoupling                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Event Sourcing

```
┌─────────────────────────────────────────────────────────────────┐
│                  EVENT SOURCING                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Instead of storing current state, store sequence of events:    │
│                                                                 │
│  Traditional: [Current State: Balance = $150]                   │
│                                                                 │
│  Event Sourced:                                                 │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ AccountCreated(id: 123)                      → $0        │   │
│  │ MoneyDeposited(id: 123, amount: 100)         → $100      │   │
│  │ MoneyWithdrawn(id: 123, amount: 30)          → $70       │   │
│  │ MoneyDeposited(id: 123, amount: 80)          → $150      │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                 │
│  BENEFITS:                                                      │
│  • Complete audit trail                                         │
│  • Time travel (reconstruct any past state)                     │
│  • Debug production issues                                      │
│  • Analytics on historical data                                 │
│                                                                 │
│  CHALLENGES:                                                    │
│  • Event schema evolution                                       │
│  • Eventual consistency                                         │
│  • Query complexity                                             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### CQRS (Command Query Responsibility Segregation)

```
┌─────────────────────────────────────────────────────────────────┐
│                         CQRS                                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  Separate read and write models:                                │
│                                                                 │
│            COMMANDS                        QUERIES              │
│         (Write Side)                    (Read Side)             │
│                                                                 │
│  ┌─────────────────┐             ┌─────────────────┐            │
│  │    Command      │             │     Query       │            │
│  │    Handler      │             │     Handler     │            │
│  └────────┬────────┘             └────────┬────────┘            │
│           │                               │                     │
│           ▼                               ▼                     │
│  ┌─────────────────┐             ┌─────────────────┐            │
│  │  Domain Model   │             │   Read Model    │            │
│  │  (Complex)      │             │   (Optimized)   │            │
│  └────────┬────────┘             └────────┬────────┘            │
│           │                               │                     │
│           ▼                               ▼                     │
│  ┌─────────────────┐             ┌─────────────────┐            │
│  │   Event Store   │────────────▶│  Read Database  │            │
│  │   (Source)      │   Events    │  (Projections)  │            │
│  └─────────────────┘             └─────────────────┘            │
│                                                                 │
│  BENEFITS:                                                      │
│  • Independent scaling of reads/writes                          │
│  • Optimized data models for each side                          │
│  • High availability through projections                        │
│                                                                 │
│  CHALLENGES:                                                    │
│  • Increased complexity                                         │
│  • Eventual consistency                                         │
│  • Data synchronization                                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Fundamental Algorithms and Data Structures

### From MIT 6.006 and Harvard CS50

Understanding algorithmic complexity is essential for writing efficient code:

```
┌─────────────────────────────────────────────────────────────────┐
│              TIME COMPLEXITY HIERARCHY                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FASTER ─────────────────────────────────────────────── SLOWER  │
│                                                                 │
│  O(1)      Constant     Hash table lookup                       │
│  O(log n)  Logarithmic  Binary search                           │
│  O(n)      Linear       Array traversal                         │
│  O(n log n) Linearithmic Merge sort, Quick sort                 │
│  O(n²)     Quadratic    Nested loops, Bubble sort               │
│  O(2ⁿ)     Exponential  Recursive Fibonacci (naive)             │
│  O(n!)     Factorial    Permutations                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Essential Data Structures

```
┌─────────────────────────────────────────────────────────────────┐
│              DATA STRUCTURES                                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  ARRAYS ────────────────────────────────────────────────────    │
│  │ Access: O(1)  │  Insert/Delete: O(n)  │  Search: O(n)        │
│  │ Use: Random access, known size                               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  LINKED LISTS ──────────────────────────────────────────────    │
│  │ Access: O(n)  │  Insert/Delete: O(1)  │  Search: O(n)        │
│  │ Use: Frequent insertions/deletions, unknown size             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HASH TABLES ───────────────────────────────────────────────    │
│  │ Access: O(1)* │  Insert/Delete: O(1)* │  Search: O(1)*       │
│  │ Use: Key-value mapping, fast lookup                          │
│  │ *Average case; worst case O(n) with collisions               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  BINARY SEARCH TREES ───────────────────────────────────────    │
│  │ Access: O(log n)*│ Insert/Delete: O(log n)*│ Search: O(log n)*│
│  │ Use: Sorted data, range queries                              │
│  │ *Balanced; worst case O(n) if unbalanced                     │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HEAPS ─────────────────────────────────────────────────────    │
│  │ Find Min/Max: O(1) │ Insert: O(log n) │ Delete: O(log n)     │
│  │ Use: Priority queues, scheduling                             │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  TRIES ─────────────────────────────────────────────────────    │
│  │ Search: O(m) where m = key length                            │
│  │ Use: Autocomplete, spell checking, prefix matching           │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Algorithm Selection Guide

```
┌─────────────────────────────────────────────────────────────────┐
│              ALGORITHM SELECTION                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  SEARCHING:                                                     │
│  • Unsorted data → Linear Search O(n)                           │
│  • Sorted array → Binary Search O(log n)                        │
│  • Key-value → Hash Table O(1)                                  │
│  • Prefix matching → Trie O(m)                                  │
│                                                                 │
│  SORTING:                                                       │
│  • General purpose → Merge Sort O(n log n) stable               │
│  • In-place needed → Quick Sort O(n log n) avg                  │
│  • Nearly sorted → Insertion Sort O(n) best                     │
│  • Integer range → Counting Sort O(n+k)                         │
│                                                                 │
│  GRAPHS:                                                        │
│  • Shortest path (unweighted) → BFS O(V+E)                      │
│  • Shortest path (weighted) → Dijkstra O(E log V)               │
│  • All pairs → Floyd-Warshall O(V³)                             │
│  • Minimum spanning tree → Prim/Kruskal                         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Microservices Lessons

### From Netflix, Spotify, and Uber

```
┌─────────────────────────────────────────────────────────────────┐
│              MICROSERVICES PRINCIPLES                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  NETFLIX DEFINITION:                                            │
│  "Loosely coupled, service-oriented architecture with bounded   │
│   context. If it isn't loosely coupled, you can't independently │
│   deploy. If you don't have bounded context, you have to know   │
│   too much about what's around you."                            │
│                                                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  KEY LESSONS:                                                   │
│                                                                 │
│  1. OWNERSHIP ──────────────────────────────────────────────    │
│  │ • Each team owns their service end-to-end                    │
│  │ • You build it, you run it                                   │
│  │ • On-call for code you ship (Netflix)                        │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  2. RESILIENCE ─────────────────────────────────────────────    │
│  │ • Design for failure from the start                          │
│  │ • Circuit breakers (Hystrix)                                 │
│  │ • Graceful degradation                                       │
│  │ • Chaos engineering (constantly practice failing)            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  3. OBSERVABILITY ──────────────────────────────────────────    │
│  │ • Distributed tracing (Jaeger at Uber)                       │
│  │ • Centralized logging                                        │
│  │ • Metrics and alerting                                       │
│  │ • Service mesh                                               │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  4. AUTONOMY WITH GUARDRAILS (Spotify) ─────────────────────    │
│  │ • Small, autonomous squads                                   │
│  │ • Shared frameworks and platforms                            │
│  │ • Golden paths, not mandates                                 │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  UBER'S WARNING:                                                │
│  With over 1,000 services, architecture became "Death Star"     │
│  - tangled dependencies made the system difficult to manage.    │
│  Solution: Global standards for documentation, reliability,     │
│  stability, and fault tolerance.                                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Code Quality Principles

### Clean Code Characteristics

```
┌─────────────────────────────────────────────────────────────────┐
│              CLEAN CODE (Robert Martin)                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  NAMING ────────────────────────────────────────────────────    │
│  │ • Intention-revealing names                                  │
│  │ • Avoid mental mapping (i, j, k → index, row, column)        │
│  │ • Use domain vocabulary                                      │
│  │ • Don't encode types in names                                │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  FUNCTIONS ─────────────────────────────────────────────────    │
│  │ • Small (< 20 lines ideal)                                   │
│  │ • Do one thing                                               │
│  │ • One level of abstraction                                   │
│  │ • Few arguments (ideally 0-2)                                │
│  │ • No side effects                                            │
│  │ • Command/Query separation                                   │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  COMMENTS ──────────────────────────────────────────────────    │
│  │ • Code should be self-explanatory                            │
│  │ • Comments for "why", not "what"                             │
│  │ • Legal comments, TODOs, clarification                       │
│  │ • Don't comment bad code—rewrite it                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  ERROR HANDLING ────────────────────────────────────────────    │
│  │ • Use exceptions, not return codes                           │
│  │ • Provide context with exceptions                            │
│  │ • Don't return null                                          │
│  │ • Don't pass null                                            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### The Rule of Three

Before abstracting, ask: "Do I have three examples?"

```
                    First instance        Second instance
                         │                      │
                         │                      │
                         ▼                      ▼
                    [Copy code]           [Copy code]
                         │                      │
                         │                      │
                         └──────────┬───────────┘
                                    │
                         Third instance?
                                    │
                                    ▼
                         [NOW abstract]
```

**Rationale:** Premature abstraction creates complexity. Three instances reveal the true pattern.

---

## Documentation Standards

### Mandatory API Documentation

All public functions, methods, classes, and interfaces **MUST** be documented in English using the language-appropriate documentation format. Documentation blocks appear immediately above the code they describe.

```
┌─────────────────────────────────────────────────────────────────┐
│              DOCUMENTATION FORMATS BY LANGUAGE                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  LANGUAGE          FORMAT              TOOL                     │
│  ─────────────────────────────────────────────────────────────  │
│  Java              JavaDoc             javadoc                  │
│  JavaScript/TS     JSDoc               jsdoc, typedoc           │
│  Python            Docstrings          Sphinx, pydoc            │
│  C#                XML Documentation   Sandcastle               │
│  C/C++             Doxygen             Doxygen                  │
│  Go                GoDoc               godoc                    │
│  Rust              Rustdoc             rustdoc (///  or //!)    │
│  Ruby              YARD/RDoc           yard, rdoc               │
│  PHP               PHPDoc              phpDocumentor            │
│  Swift             Swift Markup        Xcode                    │
│  Kotlin            KDoc                Dokka                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Documentation Block Structure

Every documented element MUST include:

```
┌─────────────────────────────────────────────────────────────────┐
│              REQUIRED DOCUMENTATION ELEMENTS                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. PURPOSE ───────────────────────────────────────────────     │
│  │ Brief description of WHAT the function/class does            │
│  │ • First sentence is the summary (appears in listings)        │
│  │ • Additional paragraphs for detailed explanation             │
│  │ • Focus on behavior, not implementation                      │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  2. PARAMETERS (@param) ───────────────────────────────────     │
│  │ For each input parameter:                                    │
│  │ • Name and type                                              │
│  │ • Description of what it represents                          │
│  │ • Valid ranges or constraints                                │
│  │ • Default values if applicable                               │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  3. RETURN VALUE (@returns/@return) ───────────────────────     │
│  │ • Type of the return value                                   │
│  │ • Description of what is returned                            │
│  │ • Possible return values/states                              │
│  │ • null/undefined conditions                                  │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  4. EXCEPTIONS (@throws/@exception) ───────────────────────     │
│  │ • Exception type                                             │
│  │ • Conditions that trigger the exception                      │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  5. EXAMPLES (@example) ───────────────────────────────────     │
│  │ • Usage examples for complex functions                       │
│  │ • Expected output                                            │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Documentation Examples by Language

```java
// ═══════════════════════════════════════════════════════════════
// JAVA (JavaDoc)
// ═══════════════════════════════════════════════════════════════

/**
 * Calculates the compound interest for a given principal amount.
 *
 * <p>This method uses the standard compound interest formula:
 * A = P(1 + r/n)^(nt) where A is the final amount.</p>
 *
 * @param principal   The initial investment amount in dollars.
 *                    Must be a positive value.
 * @param rate        The annual interest rate as a decimal
 *                    (e.g., 0.05 for 5%).
 * @param times       Number of times interest is compounded per year.
 *                    Must be at least 1.
 * @param years       The investment duration in years.
 *                    Must be a positive value.
 * @return            The final amount after compound interest,
 *                    rounded to 2 decimal places.
 * @throws IllegalArgumentException if principal, rate, or years
 *                                  is negative, or if times < 1.
 * @see #calculateSimpleInterest(double, double, double)
 * @since 1.0.0
 */
public double calculateCompoundInterest(
    double principal,
    double rate,
    int times,
    double years
) {
    // Implementation
}
```

```javascript
// ═══════════════════════════════════════════════════════════════
// JAVASCRIPT/TYPESCRIPT (JSDoc)
// ═══════════════════════════════════════════════════════════════

/**
 * Fetches user data from the API and transforms it for display.
 *
 * Makes an authenticated request to the user endpoint and maps
 * the response to the internal User model format.
 *
 * @async
 * @param {string} userId - The unique identifier of the user.
 * @param {Object} [options] - Optional configuration.
 * @param {boolean} [options.includeProfile=false] - Include extended profile.
 * @param {string[]} [options.fields] - Specific fields to retrieve.
 * @returns {Promise<User>} The user object with requested data.
 * @throws {NotFoundError} If the user does not exist.
 * @throws {AuthenticationError} If the request is not authenticated.
 * @example
 * // Basic usage
 * const user = await fetchUser('usr_123');
 *
 * @example
 * // With options
 * const user = await fetchUser('usr_123', {
 *   includeProfile: true,
 *   fields: ['name', 'email']
 * });
 */
async function fetchUser(userId, options = {}) {
    // Implementation
}
```

```python
# ═══════════════════════════════════════════════════════════════
# PYTHON (Docstrings - Google Style)
# ═══════════════════════════════════════════════════════════════

def process_transaction(
    account_id: str,
    amount: Decimal,
    transaction_type: TransactionType,
    metadata: dict[str, Any] | None = None
) -> TransactionResult:
    """Process a financial transaction on the specified account.

    Validates the transaction, applies business rules, and persists
    the result to the database. Sends notifications on success.

    Args:
        account_id: The unique identifier of the target account.
            Must be a valid UUID string.
        amount: The transaction amount. Must be positive for credits,
            negative for debits.
        transaction_type: The type of transaction (DEPOSIT, WITHDRAWAL,
            TRANSFER).
        metadata: Optional key-value pairs for additional transaction
            context. Defaults to None.

    Returns:
        TransactionResult containing the transaction ID, new balance,
        and timestamp.

    Raises:
        AccountNotFoundError: If account_id doesn't match any account.
        InsufficientFundsError: If withdrawal exceeds available balance.
        ValidationError: If amount is zero or transaction_type invalid.

    Example:
        >>> result = process_transaction(
        ...     account_id="acc_123",
        ...     amount=Decimal("100.00"),
        ...     transaction_type=TransactionType.DEPOSIT
        ... )
        >>> print(result.new_balance)
        Decimal('1100.00')
    """
    # Implementation
```

```go
// ═══════════════════════════════════════════════════════════════
// GO (GoDoc)
// ═══════════════════════════════════════════════════════════════

// ProcessOrder validates and processes a customer order.
//
// It performs inventory checks, calculates totals including tax,
// and reserves items for fulfillment. The order is persisted
// in a pending state until payment confirmation.
//
// Parameters:
//   - ctx: Context for cancellation and deadline propagation.
//   - order: The order to process, must have at least one item.
//
// Returns the processed order with calculated totals and order ID,
// or an error if validation fails or inventory is insufficient.
//
// Example:
//
//	order := &Order{CustomerID: "cust_123", Items: items}
//	processed, err := ProcessOrder(ctx, order)
//	if err != nil {
//	    log.Fatal(err)
//	}
//	fmt.Printf("Order %s total: $%.2f\n", processed.ID, processed.Total)
func ProcessOrder(ctx context.Context, order *Order) (*ProcessedOrder, error) {
    // Implementation
}
```

```rust
// ═══════════════════════════════════════════════════════════════
// RUST (Rustdoc)
// ═══════════════════════════════════════════════════════════════

/// Parses a configuration file and returns the application settings.
///
/// Reads the TOML configuration file at the specified path and
/// deserializes it into a `Config` struct. Environment variable
/// overrides are applied after file parsing.
///
/// # Arguments
///
/// * `path` - Path to the configuration file. Supports absolute
///   and relative paths.
///
/// # Returns
///
/// Returns `Ok(Config)` with the parsed configuration on success,
/// or `Err(ConfigError)` if the file cannot be read or parsed.
///
/// # Errors
///
/// This function will return an error if:
/// * The file does not exist (`ConfigError::NotFound`)
/// * The file cannot be read (`ConfigError::IoError`)
/// * The TOML is malformed (`ConfigError::ParseError`)
///
/// # Examples
///
/// ```
/// use myapp::config::parse_config;
///
/// let config = parse_config("config.toml")?;
/// println!("Server port: {}", config.server.port);
/// ```
pub fn parse_config(path: &str) -> Result<Config, ConfigError> {
    // Implementation
}
```

### Self-Documenting Code Principles

Documentation complements—but does not replace—readable code:

```
┌─────────────────────────────────────────────────────────────────┐
│              SELF-DOCUMENTING CODE                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  NAMING ───────────────────────────────────────────────────     │
│  │ ✗ int d;           // elapsed time in days                   │
│  │ ✓ int elapsedDays;                                           │
│  │                                                              │
│  │ ✗ getUserInfo()    // What info?                             │
│  │ ✓ getUserProfile()                                           │
│  │                                                              │
│  │ ✗ process()        // Process what?                          │
│  │ ✓ validateAndPersistOrder()                                  │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  FUNCTIONS ────────────────────────────────────────────────     │
│  │ • Name describes the action performed                        │
│  │ • Parameters have descriptive names                          │
│  │ • Return type indicates result                               │
│  │ • Single responsibility (one reason to change)               │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  CONSTANTS ────────────────────────────────────────────────     │
│  │ ✗ if (status == 3)                                           │
│  │ ✓ if (status == OrderStatus.SHIPPED)                         │
│  │                                                              │
│  │ ✗ setTimeout(fn, 86400000)                                   │
│  │ ✓ setTimeout(fn, Duration.days(1).toMillis())                │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  STRUCTURE ────────────────────────────────────────────────     │
│  │ • Related code grouped together                              │
│  │ • Logical flow from top to bottom                            │
│  │ • Consistent formatting and indentation                      │
│  │ • Small, focused modules                                     │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
│  COMMENTS: WHEN TO USE ────────────────────────────────────     │
│  │ ✓ WHY (intent, business context, non-obvious decisions)      │
│  │ ✓ WARNING (edge cases, gotchas, workarounds)                 │
│  │ ✓ TODO (temporary, tracked in issue system)                  │
│  │ ✗ WHAT (the code already says what it does)                  │
│  │ ✗ HOW (if unclear, refactor the code)                        │
│  └─────────────────────────────────────────────────────────     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### License Headers

**Every new source code file MUST include a license header** referencing the project's `LICENSE` or `LICENSE.md` file at the repository root.

```
┌─────────────────────────────────────────────────────────────────┐
│              LICENSE HEADER REQUIREMENTS                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  PLACEMENT:                                                     │
│  • First lines of every new source file                         │
│  • After shebang (#!) if present                                │
│  • Before any code or imports                                   │
│                                                                 │
│  CONTENT:                                                       │
│  • Reference to LICENSE/LICENSE.md at project root              │
│  • Copyright notice with year and holder                        │
│  • SPDX identifier (recommended)                                │
│                                                                 │
│  BEFORE CREATING A NEW FILE:                                    │
│  1. Check for LICENSE or LICENSE.md at project root             │
│  2. Identify the license type (MIT, Apache 2.0, GPL, etc.)      │
│  3. Use appropriate header format for that license              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### License Header Examples

```java
// ═══════════════════════════════════════════════════════════════
// MIT License
// ═══════════════════════════════════════════════════════════════

/*
 * SPDX-License-Identifier: MIT
 *
 * Copyright (c) 2024 [Copyright Holder]
 *
 * This file is part of [Project Name].
 * See LICENSE file in the project root for full license information.
 */
package com.example.app;
```

```python
# ═══════════════════════════════════════════════════════════════
# Apache 2.0 License
# ═══════════════════════════════════════════════════════════════

# SPDX-License-Identifier: Apache-2.0
#
# Copyright 2024 [Copyright Holder]
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

"""Module docstring here."""
```

```javascript
// ═══════════════════════════════════════════════════════════════
// GPL-3.0 License
// ═══════════════════════════════════════════════════════════════

/**
 * SPDX-License-Identifier: GPL-3.0-or-later
 *
 * Copyright (C) 2024 [Copyright Holder]
 *
 * This program is free software: you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation, either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program. If not, see <https://www.gnu.org/licenses/>.
 */

'use strict';
```

```rust
// ═══════════════════════════════════════════════════════════════
// BSD-3-Clause License
// ═══════════════════════════════════════════════════════════════

// SPDX-License-Identifier: BSD-3-Clause
//
// Copyright (c) 2024, [Copyright Holder]
// All rights reserved.
//
// See LICENSE file in the project root for full license terms.

//! Module documentation here.
```

```go
// ═══════════════════════════════════════════════════════════════
// Minimal Header (when LICENSE file is comprehensive)
// ═══════════════════════════════════════════════════════════════

// SPDX-License-Identifier: MIT
// Copyright (c) 2024 [Copyright Holder]
// See LICENSE for license information.

package main
```

### Documentation Checklist

```
┌─────────────────────────────────────────────────────────────────┐
│              DOCUMENTATION CHECKLIST                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  FOR EVERY PUBLIC API:                                          │
│  [ ] Documentation block present                                │
│  [ ] Written in English                                         │
│  [ ] Purpose clearly described                                  │
│  [ ] All parameters documented with types                       │
│  [ ] Return value documented                                    │
│  [ ] Exceptions/errors documented                               │
│  [ ] Examples for complex functions                             │
│                                                                 │
│  FOR EVERY NEW FILE:                                            │
│  [ ] License header present                                     │
│  [ ] References LICENSE/LICENSE.md at project root              │
│  [ ] Copyright year and holder correct                          │
│  [ ] SPDX identifier included (recommended)                     │
│                                                                 │
│  FOR CODE READABILITY:                                          │
│  [ ] Names are intention-revealing                              │
│  [ ] No magic numbers (use named constants)                     │
│  [ ] Comments explain "why", not "what"                         │
│  [ ] Complex logic has explanatory comments                     │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Checklist

### Before Writing Code
- [ ] Requirements understood
- [ ] Domain language defined
- [ ] Bounded contexts identified
- [ ] Data structures chosen appropriately
- [ ] Algorithm complexity analyzed

### During Development
- [ ] SOLID principles followed
- [ ] Appropriate patterns applied (not forced)
- [ ] Functions small and focused
- [ ] Names intention-revealing
- [ ] Tests written alongside code

### Before Merge
- [ ] Code reviewed
- [ ] Complexity justified
- [ ] No premature optimization
- [ ] No premature abstraction
- [ ] Documentation updated where needed

---

## Anthropic's AI Safety Engineering Philosophy

### The Foundation: Constitutional AI and Value Alignment

Anthropic pioneered Constitutional AI (CAI), an approach to AI safety where systems are trained to be helpful, harmless, and honest (HHH) through explicit principles rather than relying solely on human feedback. This philosophy extends to all software engineering practices.

```
┌─────────────────────────────────────────────────────────────────┐
│         ANTHROPIC'S ENGINEERING PHILOSOPHY (HHH)                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  HARMLESSNESS ──────────────────────────────────────────────    │
│  │ • Safety-first architecture                                  │
│  │ • Defense in depth: multiple layers of protection            │
│  │ • Graceful degradation under adversarial conditions          │
│  │ • Privacy by design: minimize data collection & retention    │
│  │ • Security: constant threat modeling, penetration testing    │
│  │                                                              │
│  │ "Build systems that actively resist causing harm"            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HELPFULNESS ───────────────────────────────────────────────    │
│  │ • User-centered design: solve real problems effectively      │
│  │ • Clear, actionable outputs: avoid ambiguity                 │
│  │ • Intelligent defaults: optimize for common use cases        │
│  │ • Progressive disclosure: advanced features when needed      │
│  │ • Accessibility: design for all users, not just power users  │
│  │                                                              │
│  │ "Maximize value delivered to users"                          │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
│  HONESTY ───────────────────────────────────────────────────    │
│  │ • Transparent limitations: document what system can't do     │
│  │ • Honest uncertainty: express confidence levels              │
│  │ • Clear error messages: explain failures, suggest fixes      │
│  │ • No dark patterns: never mislead users                      │
│  │ • Audit trails: maintain comprehensive logs for debugging    │
│  │                                                              │
│  │ "Always communicate truth, including uncertainty"            │
│  └──────────────────────────────────────────────────────────    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Responsible Scaling Policy (RSP)

Anthropic's Responsible Scaling Policy provides a framework for safely deploying increasingly capable AI systems. This translates to software engineering as:

```
┌─────────────────────────────────────────────────────────────────┐
│              RESPONSIBLE SCALING PRINCIPLES                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  1. CAPABILITY EVALUATION                                       │
│     • Continuously assess system capabilities and risks          │
│     • Red-team testing: adversarial evaluation before release   │
│     • Benchmark against known failure modes                     │
│                                                                 │
│  2. STAGED DEPLOYMENT                                           │
│     • Alpha → Beta → General Availability (with gates)          │
│     • Monitoring dashboards at each stage                       │
│     • Rollback mechanisms: instant revert on critical issues    │
│                                                                 │
│  3. SAFETY BUFFERS                                              │
│     • Deploy below maximum capability initially                 │
│     • Gradual feature unlocking as safety is validated          │
│     • Circuit breakers: automatic shutdown on anomaly detection │
│                                                                 │
│  4. CONTINUOUS MONITORING                                       │
│     • Real-time metrics: latency, error rates, abuse patterns   │
│     • Automated alerts for anomalous behavior                   │
│     • Human-in-the-loop for critical decisions                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Interpretability and Mechanistic Understanding

Anthropic emphasizes mechanistic interpretability—understanding *how* systems work internally, not just *what* they do. Applied to software engineering:

**Principles:**
- **Transparency by Default**: Code should reveal its logic, not hide it
- **Debuggability**: Every subsystem should be inspectable at runtime
- **Trace-Driven Development**: Comprehensive logging for post-mortem analysis
- **Model Inspections**: Regular code reviews with security focus
- **Ablation Testing**: Remove components to understand their contribution

**Example: Observable Systems**

```python
# BAD: Black box function
def process_request(data):
    result = complex_pipeline(data)
    return result

# GOOD: Observable, traceable function (Anthropic style)
def process_request(data, trace_context=None):
    """
    Process request with full traceability.
    
    Args:
        data: Input data to process
        trace_context: Optional tracing context for observability
    
    Returns:
        ProcessedResult with embedded trace metadata
    """
    trace = trace_context or new_trace()
    
    with trace.span("validate_input"):
        validation_result = validate(data)
        trace.log("validation", validation_result)
        
        if not validation_result.is_valid:
            trace.log_error("Validation failed", validation_result.errors)
            raise ValidationError(validation_result.errors)
    
    with trace.span("transform"):
        intermediate = transform(data)
        trace.log("transform_output", intermediate)
    
    with trace.span("enrich"):
        enriched = enrich(intermediate)
        trace.log("enrich_output", enriched)
    
    result = ProcessedResult(
        data=enriched,
        trace_id=trace.trace_id,
        duration_ms=trace.elapsed_ms()
    )
    
    trace.finalize()
    return result
```

### Constitutional Constraints in Code

Translate AI constitutional principles to software guardrails:

```
┌─────────────────────────────────────────────────────────────────┐
│              CONSTITUTIONAL CONSTRAINTS                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  CONSTRAINT TYPES:                                              │
│                                                                 │
│  • Input Validation: Reject malformed/malicious inputs          │
│  • Rate Limiting: Prevent abuse and ensure fair access          │
│  • Content Filtering: Block harmful outputs before delivery     │
│  • Capability Restrictions: Limit what system can do            │
│  • Audit Logging: Record all significant actions                │
│  • Timeout Enforcement: Prevent resource exhaustion             │
│                                                                 │
│  IMPLEMENTATION:                                                │
│                                                                 │
│  1. Define constraints explicitly in configuration              │
│  2. Enforce at multiple layers (defense in depth)               │
│  3. Log constraint violations for analysis                      │
│  4. Gracefully degrade when constraints trigger                 │
│  5. Regularly review and update constraint policies             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Iterative Deployment with Safety Checks

Anthropic's approach to deploying AI systems incrementally with continuous safety evaluation:

**Process:**

1. **Internal Alpha**
   - Deploy to internal users first
   - Collect comprehensive metrics and feedback
   - Red-team testing by security experts

2. **Controlled Beta**
   - Small subset of external users
   - A/B testing for unexpected behaviors
   - Circuit breakers and killswitches active

3. **Graduated Rollout**
   - Percentage-based deployment (1% → 5% → 25% → 100%)
   - Monitor key safety metrics at each stage
   - Automatic rollback on anomalies

4. **Post-Deployment Monitoring**
   - Real-time dashboards for safety metrics
   - Regular safety reviews and audits
   - Continuous improvement based on user feedback

### Anthropic Engineering Best Practices Checklist

```
┌─────────────────────────────────────────────────────────────────┐
│         ANTHROPIC-INSPIRED ENGINEERING CHECKLIST                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  BEFORE DEPLOYMENT:                                             │
│  [ ] Safety evaluation completed (red-team testing)             │
│  [ ] Failure modes documented and mitigations in place          │
│  [ ] Rate limits and abuse prevention configured                │
│  [ ] Monitoring and alerting dashboards deployed                │
│  [ ] Rollback procedure tested and ready                        │
│  [ ] Privacy impact assessment completed                        │
│                                                                 │
│  CODE QUALITY:                                                  │
│  [ ] Full observability: logs, traces, metrics                  │
│  [ ] Input validation on all external data                      │
│  [ ] Error messages are helpful and honest                      │
│  [ ] System limitations clearly documented                      │
│  [ ] No security vulnerabilities (SAST/DAST passed)             │
│                                                                 │
│  ALIGNMENT WITH HHH:                                            │
│  [ ] Harmlessness: No paths to causing user harm                │
│  [ ] Helpfulness: Solves real user problems effectively         │
│  [ ] Honesty: Communicates capabilities and limitations         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Key Takeaways from Anthropic's Philosophy

1. **Safety is Not Optional**: Build safety into architecture from day one
2. **Transparency Builds Trust**: Users should understand system behavior and limitations
3. **Iterative Deployment**: Ship incrementally with safety gates at each stage
4. **Measure Everything**: Comprehensive observability enables rapid problem detection
5. **Alignment by Design**: Ensure intended behavior matches actual behavior through testing
6. **Responsible Scaling**: Capability should grow proportionally with safety measures

---

## Remember

> *"Enterprises quickly realize that microservices don't eliminate complexity—they redistribute it."*
> — Industry Consensus

> *"Having aggregates and repositories in your code base is not enough. For DDD to work, you really need to care about the problem you are trying to solve."*
> — Eric Evans philosophy

> *"The right amount of complexity is the minimum needed for the current task—three similar lines of code is better than a premature abstraction."*

**The Golden Rules:**
1. Simple is better than clever
2. Explicit is better than implicit
3. Flat is better than nested
4. Readability counts
5. Practicality beats purity

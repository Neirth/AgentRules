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

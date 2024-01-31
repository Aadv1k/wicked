Title=Compendium of Python A
Date=2024-01-26
Order=1

### The Python Object Protocol

A "good" object protocol, allows one to control meta, hence being able to modify the behaviour and the notation of the language itself. Python achieves this through dunder methods. Allowing python to be a *multi-paradign* language

### Make use of dunder methods for better readability, and extensibility

```
Special cases aren't special enough to break the rules.
Although practicality beats purity.
```

Providing an implementation of dunder `len` and `getitem` allows the class to be more explicit, in the sense it holds some data.

It is also worth mentioning a builtin's len method != dunder len, since directly reads the `ob_size` field in python bytecode

Infix methods, such as ones those enable LHS and RHS representations, such as dunder le, gt etc should also be provided if is appropriate to do so

**Muggle Methods:** a feature not generally publicized, but makes 

### Containers

- `listcomps` and `gencomps` are preferable over `filter` and `map` which largely are remnants of legacy python, it is almost always better to use explicit generators over such functions

- `array.array` is a thin-wrapper around C's continuous memory aka Arrays. Great for storing homogeneous data, at low memory, since a list needs to allocate extra space to **amortize** the cost of a `append()` call. 

- Tuple type also saves on memory as it is immutable, and is stored as a fixed-sized array. A tuple (which doesn't hold mutable type) is known as runtime.

- Pythons `match..case` should be used for matching the structure of an object, arbitiary conditions.

### Dictionaries

- `ChainMap` merges all dictionaries to form a singular look-up-table. Updating this, auto-updates all the objects held in the table
- **hashable** in python is anything that has a dunder hash function and doesn't change across the runtime

### Data Classes

- collections.namedtuple is albeit a legacy feature that extends the base tuple class to add support for infix, repr, comparasion and other "good to have" operations on what was otherwise a bare class. 

- **typing.NamedTuple** is a newer implementation and also supports type-checking through static code analysers

- use dataclasses as a scaffold for classes with the intention of adding custom methods later. Relying solely on dataclasses might lead to a code smell, especially if there are many "dumb" classes

- make use of __slots__ when heavily contrained. It instead of allowing dict like class access, sets the elements at runtime and doesn't allow modifiication. Saving memory

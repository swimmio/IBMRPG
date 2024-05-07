---
title: Dynamic Resizing in ArrayList
---
This document will cover the dynamic resizing process in the ArrayList component, which includes:

1. Understanding the concept of dynamic resizing
2. How dynamic resizing is implemented in the ArrayList component.

# Understanding the concept of dynamic resizing

Dynamic resizing in the context of an ArrayList refers to the ability of the ArrayList to adjust its capacity based on the number of elements it contains. When elements are added and the ArrayList is full, it increases its size. Conversely, when elements are removed and the ArrayList is less than half full, it decreases its size.

# How dynamic resizing is implemented in the ArrayList component

The ArrayList component in this repository is implemented in RPG language. The dynamic resizing is handled by the `arrayAdd` and `arrayRemove` procedures. When an element is added using `arrayAdd`, the ArrayList checks if it has enough capacity to store the new element. If not, it increases its size. Similarly, when an element is removed using `arrayRemove`, the ArrayList checks if it is less than half full. If so, it decreases its size.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

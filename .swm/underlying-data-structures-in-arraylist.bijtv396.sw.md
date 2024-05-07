---
title: Underlying Data Structures in ArrayList
---
This document will cover the underlying data structures used in the ArrayList implementation in the IBMRPG repo. We'll cover:

1. The structure of the ArrayList
2. The functions provided by the ArrayList

<SwmSnippet path="/QRPGLESRC/ARRAYLIST.RPGLE" line="30">

---

# Structure of the ArrayList

The ArrayList is implemented in RPGLE language. It provides a dynamic array data structure, which means the size of the array can be increased or decreased dynamically. The ArrayList is implemented using a template data structure `arrayTpl` and `entryTpl`. The `arrayTpl` data structure represents the ArrayList itself, while the `entryTpl` represents an entry in the ArrayList.

```rpgle
       ctl-opt nomain option(*srcstmt) bnddir('QC2LE':'UTILS');

       dcl-c ARRAY_SIZE %size(arrayTpl);
       dcl-c ENTRY_SIZE %size(entryTpl);
       dcl-c DEFAULT_SIZE 16;

      /include qcopysrc,memcpy
      /include qcopysrc,quicksort
      /include qcopysrc,utils

       dcl-ds arrayTpl qualified template align;
         data pointer;
         size uns(10);
         allocatedSize uns(10);
         modCount uns(10);
         sortDirection ind;
       end-ds;

       dcl-ds entryTpl qualified template align;
         parentPtr pointer;
         objectPtr pointer;
```

---

</SwmSnippet>

<SwmSnippet path="/QCOPYSRC/ARRAYLIST.RPGLE" line="30">

---

# Functions provided by the ArrayList

The ArrayList provides a set of functions for manipulating the ArrayList. These include `arrayNew` for creating a new ArrayList, `arrayDispose` for disposing an ArrayList, `arraySort` for sorting the ArrayList, `arrayTrimToSize` for trimming the ArrayList to its current size, `arrayClear` for clearing the ArrayList, `arraySize` for getting the size of the ArrayList, `arrayIsEmpty` for checking if the ArrayList is empty, `arraySet` for setting an element at a specific index in the ArrayList, and `arrayGet` for getting an element at a specific index from the ArrayList.

```rpgle
       dcl-pr arrayNew pointer extproc('ARRAYNEW');
         initialSize uns(10) const options(*nopass);
       end-pr;

       dcl-pr arrayDispose extproc('ARRAYDISPOSE');
         arrayPtr pointer;
       end-pr;

       dcl-pr arraySort extproc('ARRAYSORT');
         arrayPtr pointer;
         compareProcedure pointer(*proc) const;
         direction ind const options(*nopass);
       end-pr;

       dcl-pr arraySortNumbers extproc('ARRAYSORTNUMBERS');
         arrayPtr pointer;
         direction ind const options(*nopass);
       end-pr;

       dcl-pr arraySortStrings extproc('ARRAYSORTSTRINGS');
         arrayPtr pointer;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

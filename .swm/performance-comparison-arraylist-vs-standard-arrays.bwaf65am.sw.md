---
title: 'Performance Comparison: ArrayList vs Standard Arrays'
---
This document will cover the performance metrics of the ArrayList component in the IBMRPG repository, specifically:

1. Understanding the ArrayList component
2. Comparing the performance of ArrayList to standard arrays.

<SwmSnippet path="/QCOPYSRC/ARRAYLIST.RPGLE" line="30">

---

# Understanding the ArrayList component

The ArrayList component in the IBMRPG repository is implemented in the `ARRAYLIST.RPGLE` file. It provides various methods for manipulating the size of the array, adding and removing elements, and getting elements at specific indices. These methods are implemented as external procedures in RPGLE.

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

# Comparing the performance of ArrayList to standard arrays

The performance of the ArrayList component compared to standard arrays depends on the specific use case. ArrayLists provide dynamic resizing, which can be beneficial when the size of the array is not known in advance or changes frequently. However, this comes with a performance cost for resizing and can consume more memory than a standard array. On the other hand, standard arrays have a fixed size, which can be more efficient in terms of memory usage and performance when the size of the array is known and does not change. However, they lack the flexibility of ArrayLists.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

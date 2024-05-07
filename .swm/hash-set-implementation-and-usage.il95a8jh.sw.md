---
title: Hash Set Implementation and Usage
---
This document will cover the implementation and usage of Hash Set in the IBMRPG repository. We'll cover:

1. The structure of a Hash Set
2. The key methods and their functionality

<SwmSnippet path="/QRPGLESRC/HASHSET.RPGLE" line="37">

---

# Structure of a Hash Set

The Hash Set is implemented using three data structures: `hashSetTpl`, `bucketTpl`, and `entryTpl`. `hashSetTpl` is the main structure that holds the buckets, size, allocated size, load factor, and threshold. Each bucket, defined by `bucketTpl`, contains a pointer to an entry. Each entry, defined by `entryTpl`, contains a pointer to the next entry, a pointer to the value, the size of the value, and the hash code of the value.

```rpgle
       dcl-ds hashSetTpl qualified template;
         bucketsPtr pointer;
         size uns(10);
         allocatedSize uns(10);
         loadFactor packed(3:2);
         threshold uns(10);
       end-ds;

       dcl-ds bucketTpl qualified template align;
         entryPtr pointer;
       end-ds;

       dcl-ds entryTpl qualified template align;
         nextEntryPtr pointer;
         valuePtr pointer;
         valueSize uns(10);
         hashCode zoned(63);
         *n char(13);
       end-ds;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/HASHSET.RPGLE" line="60">

---

# Key Methods and Their Functionality

The Hash Set implementation includes several key methods. `hashSetNew` creates a new Hash Set. `hashSetDispose` disposes of a Hash Set. `hashSetClear` clears a Hash Set. `hashSetSize` returns the size of the Hash Set. `hashSetContains` checks if a value is in the Hash Set. `hashSetAdd` adds a value to the Hash Set. `hashSetAddString` and `hashSetAddNumber` are convenience methods for adding strings and numbers to the Hash Set. `hashSetRemove` removes a value from the Hash Set. There are also several helper methods like `getHashCode`, `getBucketIndex`, `getBucket`, `getNearestExpOf2`, `disposeEntry`, `ensureCapacity`, `addEntry`, and `rebuild`.

```rpgle
       dcl-proc hashSetNew export;

         dcl-pi *n pointer;
           initialSize uns(10) const;
           loadFactor packed(3:2) const options(*nopass);
         end-pi;

         dcl-ds hashSet likeds(hashSetTpl) based(hashSetPtr);
         dcl-ds bucket likeds(bucketTpl) based(bucketPtr);
         dcl-ds entry likeds(entryTpl) based(entryPtr);
         dcl-s hashSetPtr pointer inz(*null);
         dcl-s bucketPtr pointer inz(*null);
         dcl-s entryPtr pointer inz(*null);
         dcl-s loadFactor_ packed(3:2) inz;
         dcl-s i uns(10) inz;

         if (%parms > 1);
           loadFactor_ = loadFactor;
         else;
           loadFactor_ = LOAD_FACTOR;
         endif;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

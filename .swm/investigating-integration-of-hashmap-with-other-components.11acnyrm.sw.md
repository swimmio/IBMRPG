---
title: Investigating Integration of HashMap with Other Components
---
This document will cover the integration of the HashMap with other components and structures within the repo. We'll cover:

1. The structure of the HashMap
2. The functions provided by the HashMap
3. How the HashMap interacts with other components.

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="38">

---

# The structure of the HashMap

The HashMap is structured using three data structures: `hashMapTpl`, `bucketTpl`, and `entryTpl`. These structures define the layout of the HashMap, its buckets, and its entries respectively.

```rpgle
       dcl-ds hashMapTpl qualified template;
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
         keyPtr pointer;
         keySize uns(10);
         valuePtr pointer;
         valueSize uns(10);
         hashCode zoned(63);
         *n char(9);
       end-ds;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="63">

---

# The functions provided by the HashMap

The HashMap provides several functions for interacting with it. These include `hashMapNew` for creating a new HashMap, `hashMapDispose` for disposing of a HashMap, `hashMapClear` for clearing a HashMap, `hashMapSize` for getting the size of a HashMap, `hashMapPut` and `hashMapPutSS` for adding entries to the HashMap, `hashMapGet` and `hashMapGetSS` for retrieving entries from the HashMap, and `hashMapContainsKey` and `hashMapContainsValue` for checking if a key or value exists in the HashMap.

```rpgle
       dcl-proc hashMapNew export;

         dcl-pi *n pointer;
           initialSize uns(10) const;
           loadFactor packed(3:2) const options(*nopass);
         end-pi;

         dcl-ds hashMap likeds(hashMapTpl) based(hashMapPtr);
         dcl-ds bucket likeds(bucketTpl) based(bucketPtr);
         dcl-ds entry likeds(entryTpl) based(entryPtr);
         dcl-s hashMapPtr pointer inz(*null);
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

# How the HashMap interacts with other components

The HashMap is listed under the Maps section of the repo, indicating that it is one of the main data structures used in the repo. It likely interacts with other components through the functions it provides, allowing other components to store and retrieve data in a structured manner.

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

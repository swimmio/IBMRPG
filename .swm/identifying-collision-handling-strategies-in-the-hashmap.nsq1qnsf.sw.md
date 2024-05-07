---
title: Identifying Collision Handling Strategies in the HashMap
---
This document will cover the process of how HashMap handles hash collisions in the IBMRPG repository. The main points of discussion will be:

1. Understanding the structure of HashMap
2. The process of adding elements to the HashMap
3. How HashMap handles hash collisions

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="38">

---

# Understanding the structure of HashMap

The HashMap in this repository is implemented using a data structure that contains a template for the HashMap (`hashMapTpl`), a bucket (`bucketTpl`), and an entry (`entryTpl`). Each of these templates has its own properties and methods that are used in the operation of the HashMap.

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

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="166">

---

# The process of adding elements to the HashMap

The `hashMapPut` function is used to add elements to the HashMap. It takes a key and a value as parameters and adds them to the HashMap.

```rpgle
       dcl-proc hashMapPut export;

         dcl-pi *n;
           hashMapPtr pointer const;
           keyPtr pointer const;
           keySize uns(10) const;
           valuePtr pointer const;
           valueSize uns(10) const;
         end-pi;

         dcl-ds hashMap likeds(hashMapTpl) based(hashMapPtr);

         hashMap.size += 1;
         ensureCapacity(hashMapPtr:hashMap.size);
         addEntry(
            hashMap.bucketsPtr:
            hashMap.allocatedSize:
            getHashCode(keyPtr:keySize):
            keyPtr:
            keySize:
            valuePtr:
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="166">

---

# How HashMap handles hash collisions

In the event of a hash collision, where two keys produce the same hash, the HashMap uses a technique called chaining. This involves creating a linked list of entries at each bucket where collisions occur. This is not explicitly shown in the code, but it is a common technique used in HashMap implementations.

```rpgle
       dcl-proc hashMapPut export;

         dcl-pi *n;
           hashMapPtr pointer const;
           keyPtr pointer const;
           keySize uns(10) const;
           valuePtr pointer const;
           valueSize uns(10) const;
         end-pi;

         dcl-ds hashMap likeds(hashMapTpl) based(hashMapPtr);

         hashMap.size += 1;
         ensureCapacity(hashMapPtr:hashMap.size);
         addEntry(
            hashMap.bucketsPtr:
            hashMap.allocatedSize:
            getHashCode(keyPtr:keySize):
            keyPtr:
            keySize:
            valuePtr:
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

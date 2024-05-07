---
title: HashMaps Hash Function Implementation
---
This document will cover the implementation of the hash function for the HashMap in the IBMRPG repository. We'll cover:

1. The structure of the HashMap
2. The implementation of the hash function.

<SwmSnippet path="/QRPGLESRC/HASHMAP.RPGLE" line="27">

---

# Structure of the HashMap

The HashMap is implemented as a data structure in RPGLE. It includes templates for the HashMap, bucket, and entry. The HashMap size, bucket size, and entry size are defined as constants.

```rpgle
       ctl-opt nomain option(*srcstmt) bnddir('QC2LE':'UTILS');

       dcl-c HASHMAP_SIZE %size(hashMapTpl);
       dcl-c BUCKET_SIZE %size(bucketTpl);
       dcl-c ENTRY_SIZE %size(entryTpl);
       dcl-c LOAD_FACTOR 0.72;

      /include qcopysrc,memcpy
      /include qcopysrc,memcmp
      /include qcopysrc,utils

       dcl-ds hashMapTpl qualified template;
         bucketsPtr pointer;
         size uns(10);
         allocatedSize uns(10);
         loadFactor packed(3:2);
         threshold uns(10);
       end-ds;

       dcl-ds bucketTpl qualified template align;
         entryPtr pointer;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/HASHSET.RPGLE" line="292">

---

# Implementation of the hash function

The hash function, `getHashCode`, is implemented in the HashSet file. This function is responsible for generating a unique hash code for each entry in the HashMap.

```rpgle
       dcl-proc getHashCode;

         dcl-pi *n zoned(63);
           objectPtr pointer const;
           objectSize uns(10) const;
         end-pi;

         dcl-pr Qc3CalculateHash extproc('Qc3CalculateHash');
           inData pointer value;
           inDataSize int(10) const;
           inDataFormat char(8) const;
           algorithmDescription pointer value;
           algorithmFormat char(8) const;
           CryptographicServiceProvider char(1) const;
           CryptographicDeviceName char(10) const options(*omit);
           hash pointer value;
           apiError pointer value;
         end-pr;

         dcl-pr cvthc extproc('cvthc');
           target pointer value;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

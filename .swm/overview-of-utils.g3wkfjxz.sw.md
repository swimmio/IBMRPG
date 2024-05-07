---
title: Overview of Utils
---
This document will cover the following aspects of Utils in the IBMRPG repo:

1. The functions provided by Utils
2. How these functions are used in the codebase.

<SwmSnippet path="/QRPGLESRC/UTILS.RPGLE" line="33">

---

# Utils Functions

The `toUppercase` function is a utility function that converts a given string to uppercase. It is defined in the Utils file and can be used throughout the codebase.

```rpgle
       // toUppercase
       //***********************************************************************
       dcl-proc toUppercase export;

         dcl-pi *n varchar(32767);
           string varchar(32767) const;
         end-pi;

         return %xlate(LOWER:UPPER:string);

       end-proc;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/UTILS.RPGLE" line="46">

---

Similarly, the `toLowercase` function converts a given string to lowercase. Like `toUppercase`, it is also defined in the Utils file and can be used in any part of the codebase.

```rpgle
       // toLowercase
       //***********************************************************************
       dcl-proc toLowercase export;

         dcl-pi *n varchar(32767);
           string varchar(32767) const;
         end-pi;

         return %xlate(UPPER:LOWER:string);

       end-proc;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/UTILS.RPGLE" line="59">

---

# Memory Management Functions

The `allocSpace` function is used for memory management. It allocates or reallocates memory space as per the requirement.

```rpgle
       // allocSpace
       //***********************************************************************
       dcl-proc allocSpace export;

         dcl-pi *n;
           ptr pointer;
           bytes uns(10) const;
         end-pi;

         if (ptr = *null);
           ptr = %alloc(bytes);
         else;
           ptr = %realloc(ptr:bytes);
         endif;

       end-proc;
```

---

</SwmSnippet>

<SwmSnippet path="/QRPGLESRC/UTILS.RPGLE" line="77">

---

The `deallocSpace` function is used to deallocate the memory space that was previously allocated. It helps in efficient memory management in the codebase.

```rpgle
       // deallocSpace
       //***********************************************************************
       dcl-proc deallocSpace export;

         dcl-pi *n;
           ptr pointer;
         end-pi;

         if (ptr <> *null);
           dealloc(n) ptr;
         endif;

       end-proc;
```

---

</SwmSnippet>

&nbsp;

*This is an auto-generated document by Swimm AI 🌊 and has not yet been verified by a human*

<SwmMeta version="3.0.0" repo-id="Z2l0aHViJTNBJTNBSUJNUlBHJTNBJTNBc3dpbW1pbw==" repo-name="IBMRPG"><sup>Powered by [Swimm](/)</sup></SwmMeta>

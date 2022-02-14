| Interface | Data Structure |
| - | - |
| Specification | Implementation |
| Dictates what data to store | Dictates how to store the data |
| Specifies the operations supported | Specifies how operations are performed (aka the algorightms) |
| Problems | Solutions |

## 2 Main Interfaces
- set
  - concerned about values
- sequence
  - concerned about positions

## 2 main DS approaches
- arrays
- pointer-based

## Static Sequence Interface

### Assumption

Given a machine with word-length `w` (Word, DWrod, QWord, etc), to store an array of length n, `w` >= `log (n)`

### Problem
- build(x)
- len()
- iter_swq()
- get_at(i)
- set_at(i, x) set i-th value to x.
- get/set_first/last(x)/() - insert first or remove first

### Solution
- static arrays
  - consecutive chunk of memory
  - access is constant time
  - O(1) - get() and set()
  - O(n) - build() and iter()

## Dynamic Sequences

### Problems
- All in static, and
- insert_at(i,x) --> Insert x at position i, while shifting all the data
- delete_at(i) --> Delete position i and shift all data
- insert/delete_first/last(x)/() - insert first or remove first


## Issues with Dynamic Sequence Operation on Static Arrays

| Static Arrays | Linked List |
| - | - |
| insert/delete_at() cost O(n) time | insert/delete at front/last is efficent every other operation is slow |
| shifting | get/set_at need O(i) time |
| allocation of new memory and copying to new place | |

## Amotyization
Operation takes T(n) amortized time if any k-operations take <= k.T(n) time. (ie, averaging an expensive operation over multiple cheaper operations)

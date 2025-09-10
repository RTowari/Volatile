# Volatile - v0.1.0
A modular C++ program that simulates and visualizes RAM behavior at the bit level. It models memory as a structured 3D grid, where each cube represents a single bit within a word. The system tracks allocation and deallocation events, rendering state transitions in real time to expose the underlying architecture of memory usage.


## Core concepts

- ** Bit **
    The smallest unit of memory
    Has a binary state: 'free' or 'used'.

- ** Word **
    A group of 32 bits
    Identified by a unique index
    Serves as the atomic unit of allocation

- ** MemoryModel **
    Contains a fixed number of Words.
    Applies memory events to update Bit states.
    Exposes read/write acces for visualization.

- ** MemoryEvent **
    Represents a change in a memory state.
    Types: 'AllocationEvent', 'FreeEvent', 'ModifyEvent'.
    Operates on a contiguos range of Words.

## Instruction Mapping

- `MOV AX, 0xFF`  
  Allocates Word 0.  
  Sets bits 0–7 to `used`.  
  `0xFF` = `11111111` in binary → 8 bits flipped.

- `FREE AX`  
  Frees Word 0.  
  All 32 bits marked as `free`.

- `FREE AX`  
  Frees Word 0.  
  All 32 bits marked as `free`.

## Visualization Model

The system renders memory as a 3D grid of cubes, where each cube represents a single Bit within a Word. The visual state of each cube reflects the logical state of the corresponding Bit.

- Each Bit is mapped to a unique 3D coordinate.
- Bits are rendered as cubes using OpenGL or equivalent.
- Visual properties reflect memory state:
  - `free` → dim or transparent
  - `used` → bright or colored
  - `modified` → animated or pulsing (optional)
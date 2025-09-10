# Virtual Memory Simulator — Hierarchical Page Tables (C++)

This repository contains my **Operating Systems course project**:  
a fully functional **virtual memory subsystem** implemented in modern C++.  
It simulates hierarchical page tables, recursive address translation, frame allocation,  
and page eviction — all without using STL containers or dynamic allocation.

---

## 🚀 Features
- **Hierarchical page tables** of arbitrary depth (root always in frame 0)
- **Virtual → Physical address translation** with recursive table walk
- **Page fault handling**: swap-in, swap-out, and ancestor table creation
- **Deterministic frame allocation** with priority:  1. Reuse empty table frames  
  2. Allocate next unused frame  
  3. Evict page with maximal cyclic distance
- **No STL / no dynamic allocation** (OS course constraint)
- Modular, well-structured code (clean separation of `VirtualMemory.*`, `PhysicalMemory.*`, `MemoryConstants.h`)

---

## 🛠 Build & Run

### Build
```bash
make
```
Produces `libVirtualMemory.a` — link it with your tests or demo program.

### Example Usage
```cpp
#include "VirtualMemory.h"
#include <iostream>

int main() {
    word_t val = 0;
    VMwrite(0x1234, 42);     // Write to virtual address
    VMread(0x1234, &val);    // Read back
    std::cout << "Value: " << val << std::endl;
    return 0;
}
```

---

## 📂 Project Structure
```
Memory_Management/
├── MemoryConstants.h     # Global constants (page size, frame count, tree depth)
├── PhysicalMemory.h/.cpp # Physical memory simulator (provided)
├── VirtualMemory.h/.cpp  # Implementation: address translation & eviction
├── Makefile              # Builds libVirtualMemory.a
└── README.md
```

---

## 🧪 Testing & Verification
- Verified against multiple `MemoryConstants.h` configurations  
- Stress-tested with page faults, table creation, and repeated eviction cycles  
- Deterministic behavior even under full memory and frequent evictions  
- ✅ Received **100/100** grade in HUJI Operating Systems course

---

## 📌 Notes
- **Repo Visibility:** Kept *private* to comply with academic integrity policy  
- **Language Standard:** C++17  
- **Future Work:** Add unit tests (GTest), CI workflow for automatic builds, and performance benchmarks

---

## 📜 License
MIT License (or keep repository private)


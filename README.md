# Single-Linked List Implementation

## Description
This project provides an implementation of a Single-Linked List in C++. It includes a comprehensive suite of tests to validate the functionality and exception safety of the list operations. The key features of this implementation include element insertion, deletion, and traversal capabilities, along with exception safety guarantees.

## Features
- **PushFront**: Insert an element at the front of the list.
- **PopFront**: Remove the front element of the list.
- **InsertAfter**: Insert an element after a given position.
- **EraseAfter**: Remove an element after a given position.
- **Iterator Support**: Traverse the list using iterators.

## Installation and Usage
To compile and run the tests for the Single-Linked List implementation, follow these steps:

1. **Clone the repository**:
   ```sh
   git clone <repository-url>
   cd <repository-directory>
2. **Compile the program:**
   ```g++ -o test_program test_program.cpp -std=c++17```

3. **Run the tests:**
   ```./test_program```

## System Requirements
- C++ Compiler: GCC 7.3 or later, or any other C++17 compatible compiler.
- Dependencies: No external dependencies are required.

## Future Plans
- Enhanced Iterator Support: Add reverse iterators for backward traversal.
- Additional Utility Functions: Add more utility functions like Find, Reverse, and Sort.
- Performance Optimizations: Optimize memory usage and performance for large lists.
  
## Technology Stack
- Language: C++17
- Compiler: GCC (or any C++17 compatible compiler)
- Build Tools: None required (simple g++ command used for compilation)
  
## License
This project is licensed under the MIT License.

## Contribution
Contributions are welcome! Please submit a pull request or open an issue to discuss any changes.

## Example Test Case Breakdown
```cpp
// Test case for PopFront function
SingleLinkedList<int> numbers{3, 14, 15, 92, 6};
numbers.PopFront();
assert((numbers == SingleLinkedList<int>{14, 15, 92, 6}));

// Test case for exception safety with ThrowOnCopy
bool exception_was_thrown = false;
for (int max_copy_counter = 10; max_copy_counter >= 0; --max_copy_counter) {
    SingleLinkedList<ThrowOnCopy> list{ThrowOnCopy{}, ThrowOnCopy{}, ThrowOnCopy{}};
    try {
        int copy_counter = max_copy_counter;
        list.InsertAfter(list.cbegin(), ThrowOnCopy(copy_counter));
        assert(list.GetSize() == 4u);
    }
    catch (const std::bad_alloc&) {
        exception_was_thrown = true;
        assert(list.GetSize() == 3u);
        break;
    }
}
assert(exception_was_thrown);
```
For more details, please refer to the inline comments and assertions within the Test function in the source code.

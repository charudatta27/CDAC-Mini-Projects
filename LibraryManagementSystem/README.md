# Library Management System — C++
**Course:** PGCP-AC F26

---

## Project Structure
```
LibraryManagementSystem/
├── headers/
│   ├── Exceptions.h     ← Custom exception classes
│   ├── Book.h           ← Book class + enums
│   ├── Person.h         ← Abstract base class
│   ├── Member.h         ← Derived: library member
│   ├── Librarian.h      ← Derived: staff
│   ├── Container.h      ← Template generic container
│   ├── Transaction.h    ← Issue/return tracking
│   └── Library.h        ← Main management class
├── src/
│   ├── Book.cpp
│   ├── Person.cpp
│   ├── Member.cpp
│   ├── Librarian.cpp
│   ├── Transaction.cpp
│   ├── Library.cpp
│   └── main.cpp
├── data/                ← Auto-created save files
└── .vscode/
    ├── tasks.json       ← Build tasks
    └── c_cpp_properties.json
```

---

## How to Compile & Run

### In VS Code
Press **Ctrl + Shift + B** → Select "Build Library System"  
Then run in terminal: `./LibrarySystem` (Linux/Mac) or `LibrarySystem.exe` (Windows)

### From Terminal
```bash
g++ -std=c++17 -Wall src/Book.cpp src/Person.cpp src/Member.cpp \
    src/Librarian.cpp src/Transaction.cpp src/Library.cpp src/main.cpp \
    -o LibrarySystem
./LibrarySystem
```

---

## C++ Concepts Covered
| Concept | Where Used |
|---|---|
| Abstract Class / Pure Virtual | `Person::displayInfo()` |
| Virtual Destructor | `Person::~Person()` |
| Runtime Polymorphism | Menu option 15 demo |
| Deep Copy Constructor | `Member`, `Container` |
| Template Class | `Container<T>` |
| Operator Overloading | `Book` (++, --, ==, <, [], <<, >>) |
| Function Overloading | `Container::find(int)` / `find(string)` |
| Custom Exceptions | 4 exception classes |
| STL vector & map | `Library` transactions & issuedMap |
| File Handling | Save/Load (options 13 & 14) |
| Namespaces | `LibrarySystem::` |
| Static Members | `Transaction::nextTransactionId` |
| Enums | `BookStatus`, `BookGenre` |

---

## Sample Test Flow
1. Option 1 → Add 3 books (ID: 101, 102, 103)
2. Option 5 → Register 2 members (ID: 1, 2)
3. Option 9 → Issue book 101 to member 1
4. Option 9 → Try issuing 101 to member 2 (see BookNotAvailableException)
5. Option 10 → Return book 101 from member 1
6. Option 9 → Issue book 101 to member 2 (succeeds now)
7. Option 13 → Save all data
8. Option 0 → Exit, restart, option 14 → Load data

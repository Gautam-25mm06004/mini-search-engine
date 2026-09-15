# Build and Run

## Requirements

C++17 compiler with filesystem support. Commands below target Linux with GCC 9 or newer.

## Build

```bash
g++ -std=c++17 -Wall -Wextra -pedantic main.cpp -o search
```

## Run

```bash
./search documents
```

The directory argument is required. Only immediate files with a lowercase `.txt` extension are indexed. Restart the application after changing documents.

## Query syntax

```text
cpp
cpp AND threads
cpp OR python
cpp AND NOT threads
python OR cpp AND threads
NOT cpp
:quit
```

Operators must be uppercase and separated from words by spaces. Query words accept only ASCII letters and digits. Precedence is `NOT`, `AND`, then `OR`. Parentheses are unsupported. `:quit` exits the application.

## Sample results

| Query | Expected filenames |
| --- | --- |
| `cpp` | cpp.txt, then threads.txt |
| `cpp AND threads` | threads.txt |
| `cpp AND NOT threads` | cpp.txt |
| `NOT cpp` | python.txt |

NOT-only matches receive zero scores. Invalid queries produce an error and leave the application running.

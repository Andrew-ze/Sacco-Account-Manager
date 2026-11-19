BCS - GROUP COURSEWORK 2
SACCO Member Account Manager

***WHAT IT DOES
A menu-driven C++ program that manages SACCO member accounts. The records are
stored in our own hash table (separate chaining). A std::set (balanced tree) keeps
the account numbers sorted, for the ordered reports.

***FILES
HashTable.h; Member record, Node, and our own hash table (insert, find, remove, destructor)
Sacco.h; The register: add/search/update/delete, deposit, withdraw, transfer,
              interest, ordered reports, load and save
main.cpp; Menu, safe input reading, printing
test.cpp; Automatic boundary tests (20 checks)
members.txt; Sample data, 10 members: accountNo,name,phone,balance

***HOW TO COMPILE AND RUN
    g++ main.cpp -o main
    ./main(Windows PowerShell: .\main)

Tests:
    g++ test.cpp -o test
    ./test

Memory check (Linux / WSL):
    g++ -g -fsanitize=address test.cpp -o test
    ./test

MENU
1 Add
2 Search
3 Update
4 Delete/Remove
5 Deposit
6 Withdraw
7 Transfer
8 Interest
9 Range report
10 Top savers
11 Save
12 List all
13 Show hash buckets
0 Save and exit

INPUT VALIDATION
Numbers must be valid numbers, the phone must be exactly 10 digits, the name cannot
be empty, amounts must be positive, withdrawals cannot exceed the balance, and
accounts must exist (and be unique when adding). Bad input gets a message and the
program keeps running.

NOTES
- members.txt is loaded at start and saved on exit.
- Accounts 1005 and 1106 collide: both go to bucket 96.
- Exit frees all memory: the HashTable destructor deletes every node.
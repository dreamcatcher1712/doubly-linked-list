doubly-linked-list:
contains an extra pointer, typically called the previous pointer, together with the next pointer and data which are there in the singly linked list.
can go in either direction: backward or forward.

representation of a doubly linked list:

struct Node {
    int data;
   
    // Pointer to next node in DLL
    struct Node* next;
   
    // Pointer to previous node in DLL
    struct Node* prev;
};

doubly-linked-list
representation of a doubly linked list:

struct Node {
    int data;
   
    // Pointer to next node in DLL
    struct Node* next;
   
    // Pointer to previous node in DLL
    struct Node* prev;
};

INSERTION:
Insertion of a node at the front:
void push(struct Node** head_ref, int new_data)
{
    /allocate node/
    struct Node* new_node
        = (struct Node*)malloc(sizeof(struct Node));
 
    /put in the data/
    new_node->data = new_data;
 
    /Make next of new node as head and previous as NULL/
    new_node->next = (*head_ref);
    new_node->prev = NULL;
 
    /change prev of head node to new node/
    if ((*head_ref) != NULL)
        (*head_ref)->prev = new_node;
 
    /move the head to point to the new node/
    (*head_ref) = new_node;
} 

Inserting a node in the middle of a node:
void insertAfter(struct Node* prev_node, int new_data)
{
    /check if the given prev_node is NULL/
    if (prev_node == NULL) {
        printf("the given previous node cannot be NULL");
        return;
    }
 
    /allocate new node/
    struct Node* new_node
        = (struct Node*)malloc(sizeof(struct Node));
 
    /put in the data/
    new_node->data = new_data;
 
    /Make next of new node as next of prev_node/
    new_node->next = prev_node->next;
 
    /Make the next of prev_node as new_node/
    prev_node->next = new_node;
 
    /Make prev_node as previous of new_node/
    new_node->prev = prev_node;
 
    /Change previous of new_node's next node/
    if (new_node->next != NULL)
        new_node->next->prev = new_node;
}

Insertion of a node at the end:
void append(struct Node** head_ref, int new_data)
{
    /allocate node/
    struct Node* new_node
        = (struct Node*)malloc(sizeof(struct Node));
 
    struct Node* last = *head_ref; /* used in step 5*/
 
    /put in the data/
    new_node->data = new_data;
 
    /This new node is going to be the last node, so make next of it as NULL/
    new_node->next = NULL;
 
    /If the Linked List is empty, then make the new node as head/
    if (*head_ref == NULL) {
        new_node->prev = NULL;
        *head_ref = new_node;
        return;
    }
 
    /Else traverse till the last node/
    while (last->next != NULL)
        last = last->next;
 
    /Change the next of last node/
    last->next = new_node;
 
    /Make last node as previous of new node/
    new_node->prev = last;
 
    return;
}

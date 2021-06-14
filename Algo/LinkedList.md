# LinkedList
#### Reverse LinkedList In Place Without Recursion
```java
public ListNode rev(ListNode head){
    if(head==null || head.next==null)
        return head;
    ListNode curr = head.next,prev = head,temp;
    prev.next = null;
    
    while(curr!=null){
        temp = curr.next;
        curr.next = prev;
        prev = curr;
        curr = temp;
    }
    return prev;
}
```

#### Remove duplicates
*QuestionPattern* : Hashset  

#### Delete a given node in between, when head node is not given
*QuestionPattern* : Tricky  
> Copy data of next node into current node and delete next node


#### Partition like quicksort
*QuestionPattern* : Tricky  
> Use 2 Linked lists

#### Check if palindrome
*QuestionPattern* : Stack, Tricky, Recursion  
> a) reverse n compare, or  
b) reverse half of the list and compare  
c) insert first half into stack, and check, or  
d) recursively check first and last nodes  
```java
ListNode temp = head;
bool check(ListNode node) {
    if (node == NULL) return true;
    bool isPal = check(node->next) & (temp->val == node->val);
    temp = temp->next; //temp after recursion will contain tail node
    return isPal;
}
```

#### Check for intersection
*QuestionPattern* : Stack, Tricky, Recursion  
> check end nodes same

#### Find interesection node
*QuestionPattern* : Tricky
> Find using length diff.

#### Detect start of loop
*QuestionPattern* : Tricky  
* Proceed to check for loop, i.e. If fast and slow pointers meet, there is a loop.
* Freeze one pointer and increment the other pointer in single steps. When they both meet again, the count will give you the length of the loop (k).
* Reset both pointers to the start of the link list, increment one pointer by k. Increment both pointers in single steps and when they meet again, it will be the start of the loop (this is same as finding the nth element from the end of the link list).

#### Deep Copy of linked list with arbitrary pointer
Each node has two pointers - regular next pointer and arbitrary_pointer to any node in the linked list.
* First pass: Create new first node in between first and second nodes. Repeat similarly for other nodes.
* Second pass: Update FirstNodeCopy.arbit = FirstNode.arbit.next;  //arbit ptrs for copyList are set
* Third Pass: Take two pointers starting at FirstNode and FirstNodeCopy, and update next ptrs as next to next.

# LinkedList

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

#### Check for intersection
*QuestionPattern* : Stack, Tricky, Recursion  
> check end nodes same

#### Find interesection node
*QuestionPattern* : Stack, Tricky
> Find using length diff.

#### Detect start of loop
* Proceed to check for loop, i.e. If fast and slow pointers meet, there is a loop.
* Freeze one pointer and increment the other pointer in single steps. When they both meet again, the count will give you the length of the loop (k).
* Reset both pointers to the start of the link list, increment one pointer by k. Increment both pointers in single steps and when they meet again, it will be the start of the loop (this is same as finding the nth element from the end of the link list).

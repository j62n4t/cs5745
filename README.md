java cIC SCI 46 Fall 2024 Project 4: Finding Balance in Nature
Due at 9:30 AM. You may use late submissions as usual.
Reviewing related material
I encourage you to review your lecture notes for the Binary Search Tree portions of this class,
especially the portions about balancing trees. The data structure we covered this quarter for a
balanced tree is called a Crumple Tree. Supplemental reading is posted on Canvas.
Very important note: it is not enough to implement some type of binary search tree for this
assignment. For the vast majority of the points, your type must be a Crumple Tree. Attempting
to fool the auto-grader is a decidedly bad idea.
Requirements
In this project you will be implementing the Level-balanced tree data structure as a class named
CrumpleTree. The class consists of the following functions which you are responsible for
implementing and have been started for you in CrumpleTree.hpp:
CrumpleTree()
This is the constructor for the class. You should initialize any variables you add to the
class here.
~CrumpleTree()
This is the class destructor. You are responsible for freeing any allocated memory here.
You will most likely be allocating memory to store the nodes within the tree. Since these
allocations need to be dynamic, as we don’t know how large the tree will be, they should
be freed here in the destructor. It’s your job to come up with a traversal algorithm to
accomplish this. Note, if you elect to use shared pointers or unique pointers the compiler
will generate code to deallocate the memory for you if certain conditions are met. You
should only use these features of the standard library if you already understand them or
are willing to put in extra effort. In most industry settings features like these will be used
as opposed to explicitly implemented destructors.
However, be advised that course staff are not expected to know these and might not be
able to help you debug problems with them. If you are unfamiliar with shared or unique
pointers, use traditional (raw) pointers if you are expecting help with debugging.
[[nodiscard]] size_t size() const noexcept
This function returns the number of keys stored in the tree. It returns the count as a
size_t. It is marked const (also known as a constant member function) because it
should not modify any member variables that you’ve added to the class or call any
function functions that are not marked const as well. The advantage of marking this
function as const is that it can be called on constant CrumpleTree instances. It also
allows the compiler to make additional optimizations since it can assume the object this
function is called on is not changed. This is a fairly good StackOverflow answer that
goes into additional detail.
[[nodiscard]] bool empty() const noexcept
This function simply returns whether or not the tree is empty, or in other words, if the tree
contains zero keys. Marked const because it should not change any member data.
Marked noexcept because it should not throw any exceptions.
bool contains(const K  key) const noexcept
Simply checks to see if the key k is stored in the tree. True if so, false if not. Once
again, this function does not modify any member data, so the function is marked const.
Since this is a balanced tree, this function should run in O(log N) time where N is the
number of keys in the tree. This is accomplished through the on-demand balancing
property of Crumple Trees and a consequence of the height of the tree never exceeding
O(log N). IMPORTANT: when comparing keys, you can only assume that the  Level(const K  key) const
This returns the level on which the given key is stored in the tree. If the tree does not
contain this key, return std::nullopt.
IMPORTANT: when comparing keys, you can only assume that the  tree;
const CrumpleTree  treeRef= tree;
treeRef.find(1);
Warning: this function will not be compiled until you explicitly call it on a constant
CrumpleTree as in the example above. If you submit code to GradeScope, and that
system says it does not compile, make sure you've done this. You will end up with a
zero on the assignment if your code does not compile when I pair it with test cases that
call every function. Testing comprehensively is your responsibility!
void insert(const K  key, const V  value)
Adds a (key, value) pair to the tree. If the key already exists in the tree, you may do as
you please (no test cases in the g代 写program、c/c++，Java
代做程序编程语言rading script will deal with this situation). The key k
should be used to identify the location where the pair should be stored, as in a normal
binary search tree insertion. Since this is an level-balanced tree, the tree should be
rebalanced if this insertion results in an unbalanced tree.
Note: this is by far the most difficult part of this project.
void remove(const K  key)
Removes the given key from the tree, fixing the balance if needed. If the parameter does
not exist in the tree, do not modify the tree.
I recommend you work on both insert and remove in parts; do not attempt to do the
entire insert, or entire remove, in one session. Test that you are able to get some cases
to pass before moving onto other types of cases.
[[nodiscard]] std::vector inOrder() const
Returns a vector consisting of the keys in the order they would be explored during an
in-order traversal as mentioned in class. Since the traversal is “in-order”, the keys should
be in ascending order.
IMPORTANT: this function, as well as preOrder() and postOrder(), are easy to forget to
test separately. Be very careful with these three, as their value (in terms of test cases
that rely on them) is disproportionately high. Please be absolutely sure you got these
right.
[[nodiscard]] std::vector preOrder() const
Returns a pre-ordering of the tree. For the purpose of this assignment, the left subtree
should be explored before the right subtree.
[[nodiscard]] std::vector postOrder() const
Returns a post-ordering of the tree. For the purpose of this assignment, the left subtree
should be explored before the right subtree.
Additional Notes
● Your implementation must be templated as provided.
○ Be sure yours works for non-numeric types! char is a numeric type.
○ Review the warnings in the lab manual, the grading policies, and in particular the
warning about templated code in the “Grading Environment” section.
● You do not need to write a copy constructor or an assignment operator on this project,
but knowing how to do so is generally a good thing.
● As stated in the contains() function: for comparing keys, use the “natural” comparison
offered by  library so I can make a lambda function recursive?
Sure, if you think it will help you.
Q3. Can I include parts of the standard library to test my trees?
You can use any library for debugging purposes. The only disallowed functions are for the
final, active submission, submitted to GradeScope.
Q4. Can you use the vectors you got from the in-order, pre-order, or post-order functions in other
functions?
No. You also don't need to. However, you may use std::vector within helper functions of
in/pre/post order traversals.
Q5. Are we allowed to use stacks/queues for the inorder/postorder/preorder functions?
No. You are not allowed to use any standard containers except for in your traversal
implementations where you are allowed only std::vector.
Q6. Are we allowed to use vectors or arrays to store shapes?
No, but I'm sure you could do the same without using an array or vector.
Q7. Are > (greater than) and <= (equal to or greater than) off-limits when comparing keys?
Yes, any other operators other than < (less than) and == (equal to) are off-limits when
comparing keys.
Q8. Can I use recursion to destruct the trees?
You can use recursion for a destructor. However, you should also consider the off chance that
the stack size is exceeded and the destruction fails resulting in unfreed memory.
Q9. What to do if the passed in key does not exist in the remove() function?
You can handle this case as desired; we will not be testing it.
Q10. If the deleted node is not a leaf and has two children, should we replace it with successor or
predecessor?
Both are correct to do, and the grading script will accept either.
Q11. Do we need to have O(log n) time complexity for insert and remove?
That is the target time for balanced binary search trees, including Crumple trees.
Q12. Are we allowed to implement other level-balancing binary search trees on project 4?
No.
Q13. Are we expected to handle very large trees?
Yes, you can assume that the size of the tree will not exceed the maximum uint64_t value.
Q14. Am I permitted to add my new function to the class?
Yes. Also, it doesn’t matter where you make the helper functions as long as you don't change
the public functions and their parameters.

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

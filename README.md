# LeetCodeInCSharp

# List
+ #28 Implement strStr()
+ #66 Plus One
+ #94 Binary tree in-order traversal
+ #100 Same tree
+ #104 Maximum depth of a binary tree
+ #107 Level order binary tree traversal II
+ #116 Populating next right pointers in each node
+ #122 Best Time to Buy and Sell Stock II
+ #136 Single number
+ #141 Linked list cycle
+ #144 Binary tree pre-order traversal
+ #168 ExcelSheetColumnTitle
+ #191 Number of 1 bits
+ #217 Contains duplicate
+ #226 Invert binary tree
+ #235 Lowest Common Ancestor of a Binary Search Tree
+ #237 Delete node in a linked list
+ #258 Add digits
+ #260 Single number III
+ #283 Move Zeroes

# Detail
## #28 Implement strStr()
**Problem description**: 
Returns the index of the first occurrence of needle 
in haystack, or -1 if needle is not part of haystack.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/28_ImplementStrStr.cs)  
**Naive search runtime**: 136ms  
**Rabin-Karp runtime**: 132ms  
**Explanation**:  
There are multi-ways to solve this problem.  
- Naive string search:  
Iterate through the ```haystack``` char by char, if the char matches the first char in ```needle```, iterate through the following chars in the ```haystack``` with the length of ```needle``` to check match. This brute force search has time complexity of O(MN).  
- Rabin-karp algorithm:  
(To be solved!!)Solution passed LeetCode test, but still confusing about the 'base' choice. Has asked on StackOverFlow.  
[[StackOverFlowLink]](http://stackoverflow.com/questions/32576677/issue-with-implementing-rabin-karp-algorithm-to-search-string-in-leetcode-28-im)  
- KMP algorithm:  
(fork if you can implement)
- Boyer- Moore algorithm:  
(fork if you can implement)  

## #66 Plus One
**Problem description**: 
Given a non-negative number represented as an array of digits, plus one to the number. 
The digits are stored such that the most significant digit is at the head of the list.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/66_PlusOne.cs)  
**Rruntime**: 500ms  
**Explanation**:  
- Simple iteration solution:  
Iterate through ```digits```, from ```digits[digits.Length - 1]``` to ```digits[0]```. If current number is not 9, the loop is not worth continueing, thus just add ```1``` to it and break the loop, and return ```digits```; otherwise make current number ```0``` and continue. If nothing's returned after the loop, it means all digits are ```9```, thus create a new int array ```newDigits``` with ```Length = digits.Length + 1```, set ```newDigits[0]``` to ```1```, and return ```newDigits```.

## #94 Binary tree in-order traversal
**Problem description**: 
Given a binary tree, return the inorder traversal of its nodes' values. Note: Recursive solution is trivial, could you do it iteratively?  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/94_BinaryTreeInOrderTraversal.cs)  
**Runtime**: 524ms  
**Explanation**:  
- Recursive way:  
```
method inorder(root){
    inorder(root.left);
    store root;
    inorder(root.right);
}
```
- Stack solution:  
This is an iteration solution via stack. 
```
        root
        /\
       /\
      /\
      subtree1
       /
      /\
      subtree2
       /
      /
```
It treats every right child as a start of a subtree. It stores a subtree in stack, deals with it, and then track back to the latest node with right node, and goes into this subtree and deal with it. Well this is hard to explain clearly :(.
- Morris traversal  
Seems to be the best iteration solution, to be implemented.


## #100 Same tree
**Problem description**: 
Given two binary trees, write a function to check if they are equal or not. 
Two binary trees are considered equal if they are structurally identical and the nodes have the same value.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/100_SameTree.cs)  
**Rruntime**: 160ms  
**Explanation**:  
- Recursive way:  
A very straightforward one line recursive solution. 4 cases:  
both null -> true;  
one is null but the other is not -> false;  
both not null but value not equal -> false;  
else -> check children;  

## #104 Maximum depth of a binary tree
**Problem description**: 
Given a binary tree, find its maximum depth.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/104_MaximumDepthOfABinaryTree.cs)  
**Recursive runtime**: 164ms  
**Explanation**:  
- Recursive way:  
A very straightforward one line recursive solution.

## #107 Level order binary tree traversal II  
**Problem description**: 
Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).  
**Difficulty**: 
Easy  
**code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/107_LevelOrderBinaryTreeTraversalII.cs)  
**Recursive runtime**: 502ms  
**Explanation**:  
- BFS solution:  
Use a queue to do Breadth First Search. The way I did to check the level is creating a class called NodeWithHeight to wrap the TreeNode and a Height property. So every time instead of enqueueing a node into the queue, I wrap it and its height in a NodeWithHeight object, and  enqueue this object to the queue.  

## #116 Populating next right pointers in each node
**Problem description**: 
Given a binary tree:  
```
    struct TreeLinkNode {
        TreeLinkNode *left;
        TreeLinkNode *right;
        TreeLinkNode *next;
    }
```
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL. Initially, all next pointers are set to NULL. Note: You may only use constant extra space; You may assume that it is a perfect binary tree (ie, all leaves are at the same level, and every parent has two children).  
**Difficulty**: 
Medium  
**code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/116_PopulatingNextRightPointersInEachNode.cs)  
**Runtime**: 200ms  
**Explanation**:  
- BFS queue solution and DFS recursive solution:  
Both ways are straight forward. The simple logic they both use are:  
```
if(root.left != null) root.left.next = root.right;
if(root.right != null && root.next != null) root.right.next = root.next.left;
```

## #122 Best time to buy and sell stack II
**Problem description**: 
Say you have an array for which the ith element is the price of a given stock on day i.  
Design an algorithm to find the maximum profit. You may complete as many transactions as you like (ie, buy one and sell one share of the stock multiple times). However, you may not engage in multiple transactions at the same time (ie, you must sell the stock before you buy again).  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/122_BestTimeToBuyAndSellStockII.cs)  
**Runtime**: 148ms  
**Explanation**:  
- Iteration way:  
The problem description is confusing. Actually what it says is to find the maximum profit per share of a stock. Just buy at low price day (compare to day + 1) and sell at (day + 1);

## #136 Single number
**Problem description**: 
Given an array of integers, every element appears 
twice except for one. Find that single one.  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/136_SingleNumber.cs)  
**Runtime**: 156ms  
**Explanation**:  
- Bitwise XOR:  
This solution uses 'bitwise XOR' to quickly solve the problem, each element in the array only needs to be checked once, the time complexity is O(N).  
```^``` is the bitwise XOR in C#. For bitwise XOR: (0 XOR 0 = 0, 0 XOR 1 = 1, 1 XOR 0 = 1, 1 XOR 1 = 0). Thus the ones are not single will offset each other, only the single number will live to the end.

## #141 Linked list cycle
**Problem description**: 
Given a linked list, determine if it has a cycle in it. Follow up: Can you solve it without using extra space?  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/141_LinkedListCycle.cs)  
**Runtime**: 156ms  
**Explanation**:  
- Best way so far I think, refer to [[huxijiuhao's solution]](https://leetcode.com/discuss/54343/simple-and-easy-understanding-java-solution-time-n-space-o-1):  
The key to solve this problem is to find a way to track all visited nodes. Recording them causes extra space, the simpler way is to give all visited nodes an uniform feature. "huxijiuhao"'s solution modify all visited nodes' ```next``` pointer points to the ```head```, so during the traversal once you have node points to any of the nodes you visited, it will point to the ```head```. The time complexity is O(n), and space is O(1). (This solution breaks the linked list, but the question does not have any consideration on this, so this is all good)

## #144 Binary tree pre-order traversal
**Problem description**: 
Given a binary tree, return the preorder traversal of its nodes' values. Note: Recursive solution is trivial, could you do it iteratively?  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/144_BinaryTreePreOrderTraversal.cs)  
**Recursion Runtime**: 508ms  
**Iterating Runtime**: 520ms  
**Explanation**:  
- Recursion way:  
```
method preorder(root){
    store root;
    preorder(root.left);
    preorder(root.right);
}
```
- Stack solution:  
```
method preorder(root){
    stack.push(root);
    while(stack not empty){
        temp = stack.pop;
        list.add(temp);
        stack.push(temp.right);
        stack.push(temp.left);
    }
    return list;
}
```

## #168 Excel sheet column title
**Problem description**: 
Given a positive integer, return its corresponding column title as appear in an Excel sheet.  
```  
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
```  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/168_ExcelSheetColumnTitle.cs)  
**Runtime**: 48ms  
**Explanation**:  
- Modulo solution:  
This problemm is actually converting a ```0``` started 10-scale system to a ```1``` started 26-scale system.  
```number % 26``` gives a remainder to map character. ```'A'``` is #65 in the ASCII table. Thus use ```remainder + 65``` to map character in the ASCII table. 
Because ```26 % 26``` leads to 0 which cannot used to map ```'Z'```, I used '0 - 25' instead of '1 - 26' to map 'A - Z'.
Thus in every execution in the loop, do ```n--;``` at the begining.

## #171 Excel sheet column number
**Problem description**: 
Given a column title as appear in an Excel sheet, return its corresponding column number.
```  
A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
```  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/171_ExcelSheetColumnNumber.cs)  
**Runtime**: 164ms  
**Explanation**:  
- Common way:  
Split string into charArray, iterate through, each item times corresbonding 26's power and add to the sum.



## #191 Number of 1 bits
**Problem description**: 
Write a function that takes an unsigned integer and returns the number of '1' bits it has (also known as the Hamming weight).
For example, the 32-bit integer '11' has binary representation 00000000000000000000000000001011, so the function should return 3.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/191_NumberOf1Bits.cs)  
**Runtime**: 56ms  
**Explanation**:  
- Bitwise shift and modulo:  
do ```n % 2```, will actually return the LSB of n in binary. Add this value to the result, and shift ```n``` 1 bit to the right. Loop until ```n``` equals 0.

## #217 Contains duplicate
**Problem description**: 
Given an array of integers, find if the array contains any duplicates. Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/217_ContainsDuplicate.cs)  
**Runtime**: 176ms  
**Explanation**:  
- Via hashset solution ( time complexity O(N)):  
In C# .NET, 2 features of Hashset<type> are used this problem. 1st, each element in a hashset is unique, duplicate adding will return false; 2nd, the searching time complexity is O(1), thus the adding time complexity is O(1). To solve this problem, declare a ```Hashset<int> hashset```, iterate through the given ```nums``` and add each item to ```hashset```, return true if ```hashset.Add()``` returns false.   

## #226 Invert binary tree
**Problem description**: 
Invert a binary tree.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/226_InvertBinaryTree.cs)  
**Runtime**: 160ms  
**Explanation**:  
- Recursive way:
Feel sorry for Max Howell. I might get nervous too.

## #235 Lowest Common Ancestor of a Binary Search Tree
**Problem description**: 
Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.  
**Difficulty**: Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/235_LowestCommonAncestorOfABinarySearchTree.cs)  
**Runtime**: 188ms  
**Explanation**:  
- traversal solution:  
To find the lowest common ancestor, it is actually looking for the first node that match the conditions that both (<=) than the small node and (>=) than the large node at the same time.

## #237 Delete node in a linked list
**Problem description**: 
Write a function to delete a node (except the tail) 
in a singly linked list, given only access to that node. 
Supposed the linked list is 1 -> 2 -> 3 -> 4 and you 
are given the third node with value 3, the linked list 
should become 1 -> 2 -> 4 after calling your function.  
**Difficulty**: Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/237_DeleteNodeInALinkedList.cs)  
**Runtime**: 172ms  
**Explanation**:  
- 2 line solution:  
The list pointer is not provided, thus you cannot iterate through the list, and you are not given the previous ```next``` pointer. This problem needs an alternative way to delete the node.  
```... ---> currentNodeToBeDeleted(node 0) ---> node1 ---> node2 ---> ...```  
To delete node0, copy the value of node1 to node0, change node0's ```next``` to point to node2.  
Thus node0 now holds the properties of node1, and the node actually being discarded on the memory is node1.

## #258 Add digits
**Problem description**: 
Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.  
For example:  
Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.  
**Difficulty**: 
Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/258_AddDigits.cs)  
**Recursive runtime**: 68ms  
**Explanation**:  
- The best solution with O(1) time complexity:  
[[Wikipedia reference]](https://en.wikipedia.org/wiki/Digital_root)  
In short words, "If a number produces a digital root of exactly 9, then the number is a multiple of 9."  
```result = num - root((num - 1) / 9) * 9;```  
- Recursive way:  
Return the num if num < 10, else just calculate the sum and pass as parameter to itself.  
Notice that you do not have to convert ```num``` to string, there is a simpler way: [[reference]](http://stackoverflow.com/questions/478968/sum-of-digits-in-c-sharp)  
```sum = 0;
while (n != 0) {
    sum += n % 10;
    n /= 10;
}```

## #260 Single number III
**Problem description**: 
Given an array of numbers nums, in which exactly two elements appear only once and all the other elements appear exactly twice. Find the two elements that appear only once. 
For example: Given nums = [1, 2, 1, 3, 2, 5], return [3, 5].  
**Difficulty**: 
Medium  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/260_SingleNumberIII.cs)  
**Recursive runtime**: 564ms  
**Explanation**:  
- Bitwise way:  
    1. Get the bitwise XOR result of the array.  
    For the numbers in pair, the XOR result will be 0. Thus after doing XOR one by one for the whole array, the result will be the XOR of the 2 single numbers, assume it's called ```aXORb```.
    2. Get the last set bit of the ```aXORb```.  
    Because a and b are distinct, ```aXORb``` will have at least 1 bit is set (is 1). We need to find one of the set bit.  
    Why? Because at this specific bit, one of ```a``` and ```b``` would be 1 (let's say ```a```), and the other must be 0 (let's say ```b```), and use this feature we could group up all the numbers in the array into 2 groups.
    One of this group will all have this bit set to 1 (let's say group ```a```), and the other group will all have this bit set to 0 (let's say group ```b```). The number of numbers in each group does not matter, because we will do XOR for each group, and the ones in pairs will all end up to 0, the only one left of group a will be a, and the only one left of group b will be b.  
    How? ```int lastSetBit = aXORb & (-aXORb)``` can be used to find the last set bit. In C# ```int``` uses 2's complment (I suppose so, correct me if wrong) for negative number. For example, ```3``` would be ```0011``` in binary, and ```-3``` would be ```1101```, that ```0011 XOR 1101``` leads to ```0001```, which is the last set bit.
    3. Group numbers into 2 groups.  
    Iterate through the array, check condition ```(number & lastSetBit) == 0``` to group up, and XOR through each group, you will finally get a and b.

## #283 Move Zeroes
**Problem description**: 
Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements. For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].  
**Difficulty**: Easy  
**Code**: [[code]](https://github.com/scottszb1987/LeetCodeInCSharp/blob/master/LeetCodeInCSharp/283_MoveZeroes.cs)  
**Runtime**: 492ms  
**Explanation**:  
- Iteration way, refer to [[fetoyal's solution]](https://leetcode.com/discuss/59355/3-lines-o-1-space-o-n-time-c):  
Iterate through to find none-zero number and move to the front. Thanks to fetoyal's brillient solution.

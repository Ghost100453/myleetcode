# 剑指offer52-两个链表的第一个公共节点

> ghost 2020年7月13日
>
> 难度： ==简单==

## 问题描述

输入两个链表，找出它们的第一个公共节点。

如下面的两个链表**：**

[![img](assets/160_statement.png)](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png)

在节点 c1 开始相交。

示例 1：


```
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Reference of the node with value = 8
输入解释：相交节点的值为 8 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
```

示例 2：

![img](assets/160_example_2.png)
```
输入：intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Reference of the node with value = 2
输入解释：相交节点的值为 2 （注意，如果两个列表相交则不能为 0）。从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
```

注意：

如果两个链表没有交点，返回 null.
在返回结果后，两个链表仍须保持原有的结构。
可假定整个链表结构中没有循环。
程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。
本题与主站 160 题相同：https://leetcode-cn.com/problems/intersection-of-two-linked-lists/

## 解题思路

思考如何解决（X）

记住套路（√）

这个题其实十分简单，假设链表1的长度为M，链表2的长度为N，公共节点在链表1中是位置a，在链表2中是位置b，公共长度为C，也就满足M-a= C，N-b = C，如何找到这个位置呢，

我们将链表1+链表2，那么公共节点的位置分别为a，M+b

我们将链表2+链表1，那么公共节点的位置分别为b，N+a

M+b-N-a = M-a - (N-b) = C - C = 0 

也就是经过同样的步数，他们到达了共同节点（第一个）

所以落实到代码上就非常简单了，

这里使用了leetcode上各位大神的代码，我这边就算一次复习吧

十分简洁，敬佩

```C
struct ListNode *getIntersectionNode(struct ListNode *headA, struct ListNode *headB) {
    struct ListNode *tmp1 = headA;
    struct ListNode *tmp2 = headB;
    while(tmp1 != tmp2){
        tmp1 = tmp1 == NULL ? headB:tmp1->next;
        tmp2 = tmp2 == NULL ? headA:tmp2->next;
    }
    return tmp1;
}
```


### 题目
输入一个链表，输出该链表中倒数第k个节点。为了符合大多数人的习惯，本题从1开始计数，即链表的尾节点是倒数第1个节点。例如，一个链表有6个节点，从头节点开始，它们的值依次是1、2、3、4、5、6。这个链表的倒数第3个节点是值为4的节点。

### 示例
```
示例 1：
给定一个链表: 1->2->3->4->5, 和 k = 2.

返回链表 4->5.
```
### 算法思路
- 依旧是快慢指针
1. 定义快指针、慢指针，均指向头节点head。
2. 让快指针先走k-1步
3. 然后双指针共同移动，当快指针走完时，慢指针指向的位置即倒数k个节点。

### 代码实现
```java
/**
 * LeetCode练习：链表中倒数第k个节点：https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/
 */
public class LeetCodeTest12 {

    public static class ListNode {
        int val;

        ListNode next;

        ListNode(int x, ListNode next) {
            val = x;
            this.next = next;
        }

        @Override
        public String toString() {
            ListNode listNode = this;
            StringBuilder sb = new StringBuilder();
            while (listNode != null) {
                if (sb.length() == 0) {
                    sb.append(listNode.val);
                } else {
                    sb.append("->").append(listNode.val);
                }
                listNode = listNode.next;
            }
            return sb.toString();
        }
    }

    public static void main(String[] args) {
        //数据模拟
        ListNode listNode = new ListNode(1, new ListNode(2, new ListNode(3, new ListNode(4, new ListNode(5, null)))));

        ListNode node = getKthFromEnd(listNode, 2);
        System.out.println(node.toString());

    }

    public static ListNode getKthFromEnd(ListNode head, int k) {
        //快指针
        ListNode quick = head;
        //慢指针
        ListNode slow = head;

        //让快指针先走k-1步
        for (int i = 1; i < k; i++) {
            quick = quick.next;
        }
        //循环，等到快指针走完的时候，慢指针对应的就是倒数k个节点
        while (quick != null) {
            quick = quick.next;
            if (quick != null) {
                slow = slow.next;
            }
        }
        return slow;
    }
}
```


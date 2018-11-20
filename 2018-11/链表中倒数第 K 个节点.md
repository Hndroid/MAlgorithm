####  链表中倒数第k个结点

> 2018年11月14日 10:00:59

##### 题目描述

输入一个链表，输出该链表中倒数第k个结点。

##### 代码实现

	/*
	public class ListNode {
	    int val;
	    ListNode next = null;
	
	    ListNode(int val) {
	        this.val = val;
	    }
	}*/

	public class Solution {
	    public ListNode FindKthToTail(ListNode head,int k) {
			if (head == null || k == 0) {
				return null;
			}
			ListNode temp = head;
			int mask = 0;
			
			while (head != null) {
				head = head.next;
				mask++;
			}
			
			if (k <= mask) {
				int n = mask - k;
				while (n != 0) {
					temp = temp.next;
					n--;
				}
			}else{
	            return null;
	        }
			
			return temp;
	    }
	}

	

##### 思路：

通过一个 mask 标记链表的长度；


##### 时间复杂度：


##### 空间复杂度：
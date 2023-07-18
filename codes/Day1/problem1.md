Leet code problem link: https://leetcode.com/problems/add-two-numbers/description/

```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode result = new ListNode(0);
        ListNode dummy = result;
        int carry = 0;
        int sum = 0;
        while(l1 != null && l2 != null)
        {
            sum = l1.val + l2.val + carry;
            l1 = l1.next;
            l2 = l2.next;
            carry = sum/10;
            sum = sum % 10;
            dummy.next = new ListNode(sum);
            dummy = dummy.next;
        }

       
        if(l1 == null && l2 == null && carry !=0)
        {
            dummy.next = new ListNode(carry);
            return result.next;
        }
        else if(l1 == null && l2 != null)
        {
            while(l2 != null )
            {
                sum = l2.val + carry;
                l2 = l2.next;
                carry = sum/10;
                sum = sum % 10;
                dummy.next = new ListNode(sum);
                dummy = dummy.next;
                if(carry != 0)
                {
                    dummy.next = new ListNode(carry);
                }
            }
            return result.next;
        }
        else if(l1 != null && l2 == null)
        {
            while(l1 != null )
            {
                sum = l1.val + carry;
                l1 = l1.next;
                carry = sum/10;
                sum = sum % 10;
                dummy.next = new ListNode(sum);
                dummy = dummy.next;
                if(carry!=0)
                {
                    dummy.next = new ListNode(carry);
                }
            }
            return result.next;
            
        }
        else
        return result.next;
    }
}
```
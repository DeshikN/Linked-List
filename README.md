# Linked-List
Divide linked list into two
Write a function that takes one list and divides up its nodes to create two smaller lists A and B. The sub lists should be made from alternating elements in the original list.
Nodes should be in the reverse order of which they occurred in the source list.
Print both linked lists in different lines.
Input format :
Line 1 : Linked list elements of length n (separated by space and terminated by -1)
Output format :
Line 1 : Output Linked List 1 elements (separated by space)
Line 2 : Output Linked List 2 elements (separated by space)
Constraints :
1 <= n <= 10^4
Sample Input :
 8 2 5 9 1 4 3 7 -1
Note : -1 at the end of input is just a terminator representing the end of linked list. This -1 is not part of the linked list. Size of given linked list is 8.
Sample Output :
 3 1 5 8
 7 4 9 2



public class solution {

    public static void make2List(ListNode<Integer> head) {
        ListNode<Integer> curr = head;
        ListNode<Integer> aHead = null;
        ListNode<Integer> bHead = null;
        ListNode<Integer> aTail = null;
        ListNode<Integer> bTail = null;
        boolean isA = true;
        while (curr != null) {
            ListNode<Integer> temp = new ListNode<>(curr.data);
            if (isA) {
                if (aHead == null) {
                    aHead = temp;
                    aTail = temp;
                } else {
                    temp.next = aHead;
                    aHead = temp;
                }
            } else {
                if (bHead == null) {
                    bHead = temp;
                    bTail = temp;
                } else {
                    temp.next = bHead;
                    bHead = temp;
                }
            }
            isA = !isA;
            curr = curr.next;
        }
        printList(aHead);
        System.out.println();
        printList(bHead);
    }

    public static void printList(ListNode<Integer> head) {
        ListNode<Integer> temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
    }
}

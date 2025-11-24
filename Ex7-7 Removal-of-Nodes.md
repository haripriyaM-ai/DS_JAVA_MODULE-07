# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE:
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start
2. Create a singly linked list
3. Read the integer value 'val' to be removed from the list
4. Remove matching nodes from the beginning by moving head forward while head.data == val
5. Initialize a pointer current to head
6. Traverse the list while current and current.next are not null:
      a. If current.next.data equals val, bypass the node by linking current.next to current.next.next
      b. Else move current to current.next
7. Return the updated head pointer
8. Display the modified linked list
9. Stop


## Program:
```java
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: HARI PRIYA M
RegisterNumber: 212224240047
*/

import java.util.Scanner;

public class Node {    // main runnable class based on your compiler constraint

    static class ListNode {
        int data;
        ListNode next;

        ListNode(int data) {
            this.data = data;
            this.next = null;
        }
    }

    public static ListNode removeElements(ListNode head, int val) {

        // Remove nodes from the beginning if they match val
        while (head != null && head.data == val) {
            head = head.next;
        }

        ListNode current = head;

        // Traverse and remove matching nodes
        while (current != null && current.next != null) {
            if (current.next.data == val) {
                current.next = current.next.next;  // skip the node
            } else {
                current = current.next;
            }
        }
        return head;
    }

    public static void display(ListNode head) {
        ListNode temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        ListNode head = null, tail = null;

        System.out.println("Enter linked list elements:");
        for (int i = 0; i < n; i++) {
            ListNode newNode = new ListNode(sc.nextInt());
            if (head == null) {
                head = newNode;
                tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

        System.out.print("Enter the value to remove: ");
        int val = sc.nextInt();

        head = removeElements(head, val);

        System.out.println("Linked List after removal:");
        display(head);

        sc.close();
    }
}

```

## Output:
<img width="422" height="307" alt="image" src="https://github.com/user-attachments/assets/3493b660-bc74-4575-ad2b-7df9239c0165" />



## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.

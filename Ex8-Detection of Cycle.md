# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE:
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Start
2. Create a singly linked list
3. Read the index position to connect the tail for cycle creation (-1 meaning no cycle)
4. Use two pointers slow and fast starting from head
5. Move slow by one step and fast by two steps until they meet or fast becomes null
6. If fast becomes null, no cycle exists, return null
7. If slow and fast meet, reset slow to head
8. Move slow and fast one step at a time until they meet again
9. The meeting point is the starting node of the cycle
10. Display the starting node value or print "No cycle detected"
11. Stop

## Program:
```java
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: HARI PRIYA M
RegisterNumber: 212224240047 
*/

import java.util.Scanner;

public class Node {

    static class ListNode {
        int data;
        ListNode next;
        ListNode(int data) {
            this.data = data;
            this.next = null;
        }
    }

    public static ListNode detectCycle(ListNode head) {
        ListNode slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
            if (slow == fast) {
                slow = head;
                while (slow != fast) {
                    slow = slow.next;
                    fast = fast.next;
                }
                return slow;
            }
        }
        return null;
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

        System.out.print("Enter index to connect tail for cycle (-1 for no cycle): ");
        int pos = sc.nextInt();

        if (pos != -1) {
            ListNode temp = head;
            for (int i = 0; i < pos; i++) {
                temp = temp.next;
            }
            tail.next = temp;
        }

        ListNode cycleStart = detectCycle(head);
        if (cycleStart != null) {
            System.out.println("Cycle begins at node with value: " + cycleStart.data);
        } else {
            System.out.println("No cycle detected");
        }

        sc.close();
    }
}
```

## Output:
<img width="641" height="286" alt="image" src="https://github.com/user-attachments/assets/07673260-51a0-4b76-8f62-4dd5f299d7bd" />



## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.

# Ex6 Right Rotation LinkedList
## DATE:
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1. Start
2. Create a singly linked list
3. Read the value of k (number of positions to rotate right)
4. Count the length of the linked list
5. Connect the last node to the head to form a circular list
6. Compute effective rotation: k = k % length
7. Traverse to the (length - k - 1)th node and mark it as the new tail
8. Set new head = newTail.next
9. Break the circular link by setting newTail.next = null
10. Display the rotated linked list
11. Stop


## Program:
```java
/*
Program to  Right Rotation LinkedList
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

    public static ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) {
            return head;
        }

        
        ListNode temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        
        temp.next = head;

        
        k = k % length;

       
        ListNode newTail = head;
        for (int i = 1; i < length - k; i++) {
            newTail = newTail.next;
        }

        head = newTail.next;
        newTail.next = null;

        return head;
    }

    public static void display(ListNode head) {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        ListNode head = null, tail = null;

        System.out.println("Enter the linked list elements:");
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

        System.out.print("Enter k (positions to rotate right): ");
        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.println("Rotated Linked List:");
        display(head);

        sc.close();
    }
}

```

## Output:
<img width="455" height="295" alt="image" src="https://github.com/user-attachments/assets/aa85d5d1-b711-444f-a5fc-ce99ecd3cdcb" />



## Result:
Thus, the java program to perfom right rotation on linked list is implemented successfully.

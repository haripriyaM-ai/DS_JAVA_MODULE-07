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

# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE:
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. Start
2. Read the number of elements n
3. Create an integer array nums of size n
4. Read the permutation array elements
5. Create a boolean array visited of size n initialized to false
6. Initialize maxLen = 0
7. For each index i from 0 to n-1:
      a. Set count = 0 and current = i
      b. While visited[current] is false:
            i. Mark visited[current] as true
            ii. Set current = nums[current]
            iii. Increment count
      c. If count > maxLen then update maxLen
8. Print maxLen as the length of the longest nested set
9. Stop


## Program:
```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: HARI PRIYA M
RegisterNumber: 212224240047
*/

import java.util.Scanner;

public class Node {

    public static int longestNestedSet(int[] nums) {
        boolean[] visited = new boolean[nums.length];
        int maxLen = 0;

        for (int i = 0; i < nums.length; i++) {
            int count = 0;
            int current = i;

            while (!visited[current]) {
                visited[current] = true;
                current = nums[current];
                count++;
            }
            if (count > maxLen) {
                maxLen = count;
            }
        }
        return maxLen;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();

        int[] nums = new int[n];
        System.out.println("Enter elements of permutation array:");
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int result = longestNestedSet(nums);
        System.out.println("Longest length of nested set: " + result);

        sc.close();
    }
}

```

## Output:
<img width="458" height="260" alt="image" src="https://github.com/user-attachments/assets/bc97f1f0-ab94-4bad-bbe3-5761c7d73bfb" />



## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.

# EXP 10 Flattening a Nested List Using an Iterator
## DATE:
## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).
## Algorithm
1. Start
2. Create an interface NestedInteger to represent an integer or a list of NestedInteger objects
3. Implement the NestedInteger structure to hold either a single integer or a list
4. Use a stack of iterators to store nested list traversal states
5. Initialize the stack with the iterator of the top-level nested list
6. For hasNext():
      a. Loop while stack is not empty
      b. If top iterator has no next element, pop it
      c. Else get next element
         i. If it is an integer, store it and return true
         ii. If it is a list, push its iterator onto the stack
7. For next(), return the last stored integer value
8. Print integers sequentially until hasNext() becomes false
9. Stop


## Program:
```java
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: HARI PRIYA M
RegisterNumber: 212224240047
*/

import java.util.*;

public class Node {

    interface NestedInteger {
        boolean isInteger();
        Integer getInteger();
        List<NestedInteger> getList();
    }

    static class NI implements NestedInteger {
        Integer value;
        List<NestedInteger> list;

        NI(Integer value) {
            this.value = value;
            this.list = null;
        }

        NI(List<NestedInteger> list) {
            this.list = list;
            this.value = null;
        }

        public boolean isInteger() {
            return value != null;
        }

        public Integer getInteger() {
            return value;
        }

        public List<NestedInteger> getList() {
            return list;
        }
    }

    static class NestedIterator implements Iterator<Integer> {
        Stack<Iterator<NestedInteger>> stack;
        Integer nextVal;

        NestedIterator(List<NestedInteger> nestedList) {
            stack = new Stack<>();
            stack.push(nestedList.iterator());
        }

        public boolean hasNext() {
            while (!stack.isEmpty()) {
                Iterator<NestedInteger> it = stack.peek();
                if (!it.hasNext()) {
                    stack.pop();
                    continue;
                }
                NestedInteger ni = it.next();
                if (ni.isInteger()) {
                    nextVal = ni.getInteger();
                    return true;
                } else {
                    stack.push(ni.getList().iterator());
                }
            }
            return false;
        }

        public Integer next() {
            return nextVal;
        }
    }

    public static void main(String[] args) {
        List<NestedInteger> nestedList = new ArrayList<>();

        nestedList.add(new NI(1));
        List<NestedInteger> l1 = new ArrayList<>();
        l1.add(new NI(4));
        List<NestedInteger> l2 = new ArrayList<>();
        l2.add(new NI(6));
        l1.add(new NI(l2));
        nestedList.add(new NI(l1));

        NestedIterator i = new NestedIterator(nestedList);
        while (i.hasNext()) {
            System.out.print(i.next() + " ");
        }
    }
}

```

## Output:
<img width="408" height="158" alt="image" src="https://github.com/user-attachments/assets/1a13573e-cb2f-42d0-8208-155639cffb54" />



## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.

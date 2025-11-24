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

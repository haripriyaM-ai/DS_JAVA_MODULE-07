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

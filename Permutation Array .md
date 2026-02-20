# Ex9 Finding the Longest Length of Nested Set in a Permutation Array
## DATE:
## AIM:
To write a program that finds the length of the longest set s[k] defined as s[k] = { nums[k], nums[nums[k]], nums[nums[nums[k]]], … },where the iteration stops before a duplicate element occurs.

The task is to return the maximum size among all such sets.
## Algorithm
1. Start
2. Read number of elements (n)
3. Input the array nums
4. Create a visited array and set all values to false
5. Initialize maxSize = 0
6. For each index i:
7. If not visited, follow nums[i] until a visited element is found
8. Count the length of this sequence
9. Update maxSize if needed
10. Display maxSize
11. Stop

## Program:
```java
/*
Program to find the Longest Length of Nested Set in a Permutation Array
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014
*/
import java.util.Scanner;

public class LongestNestedSet {
    static int arrayNesting(int[] nums) {
        int n = nums.length;
        boolean[] visited = new boolean[n];
        int maxSize = 0;
        for (int i = 0; i < n; i++) {
            if (!visited[i]) {
                int size = 0;
                int current = i;
                while (!visited[current]) {
                    visited[current] = true;
                    current = nums[current];
                    size++;
                }
                if (size > maxSize) maxSize = size;
            }
        }
        return maxSize;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        int[] nums = new int[n];
        System.out.println("Enter the permutation array elements (0-based indices):");
        for (int i = 0; i < n; i++) nums[i] = sc.nextInt();
        int result = arrayNesting(nums);
        System.out.println("Longest length of nested set: " + result);
        sc.close();
    }
}
```

## Output:

<img width="927" height="151" alt="511970896-566b48c5-e998-4d5a-8ecf-8b3f06f7222e" src="https://github.com/user-attachments/assets/8029bc76-0adb-4419-90ad-89f3d947e68d" />


## Result:
The program successfully computes the longest length of the nested set s[k] for the given permutation array.

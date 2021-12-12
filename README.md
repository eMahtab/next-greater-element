# Next greater element
## https://www.hackerrank.com/contests/second/challenges/next-greater-element

Given an array, print the Next Greater Element (NGE) for every element. The Next greater Element for an element x is the first greater element on the right side of x in array. Elements for which no greater element exist, consider next greater element as -1.

For the input array [4, 5, 2, 25], the next greater elements for each element are as follows.
```
Input : [4, 5, 2, 25]
Element --> NGE

4 --> 5

5 --> 25

2 --> 25

25 --> -1
```
For the input array [13, 7, 6, 12], the next greater elements for each element are as follows.
```
Input : [13, 7, 6, 12]
Element --> NGE

13 --> -1

7 --> 12

6 --> 12

12 --> -1
```

## Implementation : O(n) : Stack
```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) throws Exception{
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String line = br.readLine();
        int N = Integer.parseInt(line);
        line = br.readLine();
        String[] numbers = line.split(" ");
        int[] nums = new int[N];
        for(int i = 0; i < N; i++) {
            nums[i] = Integer.parseInt(numbers[i]);
        }
        int[] result = new int[N];
        Stack<Integer> stack = new Stack<Integer>();
        stack.push(nums[N-1]);
        result[N-1] = -1;
        for(int i = N-2; i >= 0; i--) {
            while(!stack.isEmpty() && stack.peek() <= nums[i]) {
                stack.pop();
            }
            if(stack.isEmpty()) {
                result[i] = -1;
            } else {
                result[i] = stack.peek();
            }
            stack.push(nums[i]);
        }
        for(int i = 0; i < nums.length; i++) {
            System.out.println(nums[i] + " " + result[i]);
        }
    }
}
```

## Another way to write it :
```java
import java.io.*;
import java.util.*;

public class Solution {

    public static void main(String[] args) throws Exception{
        /* Enter your code here. Read input from STDIN. Print output to STDOUT. Your class should be named Solution. */
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        String line = br.readLine();
        int N = Integer.parseInt(line);
        line = br.readLine();
        String[] numbers = line.split(" ");
        int[] nums = new int[N];
        for(int i = 0; i < N; i++) {
            nums[i] = Integer.parseInt(numbers[i]);
        }
        int[] result = new int[N];
        Stack<Integer> stack = new Stack<Integer>();
        stack.push(nums[N-1]);
        result[N-1] = -1;
        for(int i = N-2; i >= 0; i--) {
            while(!stack.isEmpty()) {
                if(stack.peek() <= nums[i]) {
                   stack.pop();  
                } else {
                   result[i] = stack.peek();
                   break;
                }
            }
            if(stack.isEmpty()) {
                result[i] = -1;
            }
            stack.push(nums[i]);
        }
        for(int i = 0; i < nums.length; i++) {
            System.out.println(nums[i] + " " + result[i]);
        }
    }
}
```

# References :
 1. https://www.youtube.com/watch?v=rSf9vPtKcmI (Hindi, good one)


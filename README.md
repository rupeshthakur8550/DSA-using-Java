Sure! Here is the updated and more informative README file for your GitHub repository on Data Structures and Algorithms (DSA) in Java:

---

# Data Structures and Algorithms (DSA) in Java

This repository is a comprehensive guide to Data Structures and Algorithms (DSA) using Java. It covers topics from basics to advanced, with detailed explanations and examples. 

## Table of Contents
1. [Arrays and ArrayLists](#arrays-and-arraylists)
   - [Arrays](#arrays)
   - [ArrayLists](#arraylists)
     - Methods: `add`, `remove`, `get`, `contains`, `clear`, `size`, `sort`, `toArray`, etc.
   - [Multi-dimensional Arrays](#multi-dimensional-arrays)
   - [Multi-dimensional ArrayLists](#multi-dimensional-arraylists)
2. [Searching Algorithms](#searching-algorithms)
   - [Linear Search](#linear-search)
   - [Binary Search](#binary-search)
3. [Bit Manipulations](#bit-manipulations)
   - Tables: `AND`, `OR`, `NOT`, `XOR`, `Left Shift Operator (<<)`, `Right Shift Operator (>>)`
4. [String Handling](#string-handling)
   - [String](#string)
   - [StringBuffer](#stringbuffer)
   - [StringBuilder](#stringbuilder)

## Arrays and ArrayLists

### Arrays
An array is a collection of elements of the same type placed in contiguous memory locations. It is a fixed-size data structure.

**Example: Reversing an Array**

```java
import java.util.Arrays;

public class ReverseArray {
    public static void main(String[] args) {
        System.out.println(Arrays.toString(reverse(new int[] { 10, 5, 9, 2, 30, 40 })));
    }

    private static int[] reverse(int[] arr) {
        int i = 0, j = arr.length - 1;
        while (i <= j) {
            int temp = arr[i];
            arr[i++] = arr[j];
            arr[j--] = temp;
        }
        return arr;
    }
}
```

### ArrayLists
ArrayList is a part of the Java Collections Framework. It is resizable and provides methods to manipulate the size of the array.

**Methods and Examples:**

1. `add(E e)`: Appends the specified element to the end of this list.
2. `remove(Object o)`: Removes the first occurrence of the specified element from this list.
3. `get(int index)`: Returns the element at the specified position in this list.
4. `contains(Object o)`: Returns `true` if this list contains the specified element.
5. `clear()`: Removes all of the elements from this list.
6. `size()`: Returns the number of elements in this list.
7. `sort(Comparator<? super E> c)`: Sorts this list according to the order induced by the specified Comparator.
8. `toArray()`: Returns an array containing all of the elements in this list.

**Example: Basic Operations**

```java
import java.util.ArrayList;
import java.util.Collections;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        
        System.out.println(list);  // Output: [Apple, Banana, Cherry]
        
        list.remove("Banana");
        System.out.println(list);  // Output: [Apple, Cherry]
        
        System.out.println(list.get(0));  // Output: Apple
        System.out.println(list.contains("Cherry"));  // Output: true
        
        list.clear();
        System.out.println(list.size());  // Output: 0
        
        list.add("Banana");
        list.add("Apple");
        list.add("Cherry");

        System.out.println(list.sort());  // Output: [Apple, Banana, Cherry]
        System.out.println(Comparator.reverseOrder());  // Output: [Cherry, Banana, Apple]
        
        Object[] arr = list.toArray();
        for (Object obj : arr) {
            System.out.println(obj);
        }
    }
}
```

### Multi-dimensional Arrays
A multi-dimensional array is an array of arrays. It can be used to represent data in a grid or matrix format.

**Example: Multi-dimensional Array**

```java
public class MultiDimensionalArray {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

### Multi-dimensional ArrayLists
A multi-dimensional ArrayList is an ArrayList of ArrayLists. It can be dynamically resized and used similarly to multi-dimensional arrays.

**Example: Multi-dimensional ArrayList**

```java
import java.util.ArrayList;

public class MultiDimensionalArrayList {
    public static void main(String[] args) {
        ArrayList<ArrayList<Integer>> list = new ArrayList<>();

        ArrayList<Integer> row1 = new ArrayList<>();
        row1.add(1);
        row1.add(2);
        row1.add(3);

        ArrayList<Integer> row2 = new ArrayList<>();
        row2.add(4);
        row2.add(5);
        row2.add(6);

        list.add(row1);
        list.add(row2);

        for (ArrayList<Integer> row : list) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

## Searching Algorithms
Here is the updated README file with the correct structure and added question statements:

---

# Data Structures and Algorithms (DSA) Recap

## Searching Algorithms

### Linear Search

Linear search is a simple search algorithm that checks every element until the desired element is found or the list ends.

#### Linear Search in an Array Implementation

```java
public class LinearSearch {
    public static void main(String[] args) {
        int[] arr = { 10, 20, 30, 4, 2, 9, 40 };
        int target = 40;
        int result = search(arr, target);
        
        if (result == -1) {
            System.out.println("Element not found");
        } else {
            System.out.println("Element found at index: " + result);
        }
    }

    private static int search(int[] arr, int val) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == val) {
                return i;
            }
        }
        return -1;
    }
}
```

#### Linear Search in a String Implementation

```java
public class LinearSearchString {
    public static void main(String[] args) {
        String str = "abchksdj";
        char target = 'h';
        
        boolean result = find(str, target);
        System.out.println("Character " + target + " found: " + result);
    }

    private static boolean find(String str, char ch) {
        for (char check : str.toCharArray()) {
            if (check == ch) {
                return true;
            }
        }
        return false;
    }
}
```

#### Counting Even Digits in an Array

```java
public class EvenDigits {
    public static void main(String[] args) {
        int[] arr = { 10, 20, 30, 4, 2, 9, 40, 1000 };
        int count = evendigits(arr);
        
        System.out.println("Number of elements with even digits: " + count);
    }

    private static int evendigits(int[] arr) {
        int count = 0;
        for (int val : arr) {
            if ((int) (Math.log10(val) + 1) % 2 == 0) {
                count++;
            }
        }
        return count;
    }
}
```

### Binary Search

Binary search is a more efficient algorithm that works on sorted arrays. It divides the array into halves to find the target value.

#### Binary Search in an Array Implementation

```java
public class BinarySearch {
    public static void main(String[] args) {
        int[] arr = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
        int target = 6;
        
        boolean result = search(arr, target);
        System.out.println("Element found: " + result);
    }

    private static boolean search(int[] arr, int target) {
        int start = 0, end = arr.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (arr[mid] == target) {
                return true;
            } else if (arr[mid] < target) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return false;
    }
}
```

#### Finding Ceil and Floor Values in an Array

**Ceil Value**

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(ceil(arr, 2));
}

private static int ceil(int[] arr, int target) {
    // Smallest element in greater elements than target
    int s = 0, e = arr.length - 1;
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (arr[m] == target) {
            return arr[m];
        } else if (arr[m] < target) {
            s = m + 1;
        } else {
            e = m - 1;
        }
    }
    return arr[s];
}
```

**Floor Value**

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(floor(arr, 6));
}

private static int floor(int[] arr, int target) {
    int s = 0, e = arr.length - 1;
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (arr[m] == target) {
            return arr[m];
        } else if (arr[m] < target) {
            s = m + 1;
        } else {
            e = m - 1;
        }
    }
    return arr[e];
}
```

#### Finding the Ceil Value in a String

```java
public static void main(String[] args) {
    System.out.println(ceilOfChar("abhijt", 'b'));
}

private static char ceilOfChar(String str, char ch) {
    int s = 0, e = str.length() - 1;
    char result = str.charAt(0);
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (str.charAt(m) > ch) {
            result = str.charAt(m);
            e = m - 1;
        } else {
            s = m + 1;
        }
    }
    return result;
}
```

#### Finding the First and Last Occurrence of an Element in a Sorted Array

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(find(arr, 4, true) + " " + find(arr, 4, false));
}

private static int find(int[] arr, int target, boolean left) {
    int start = 0, end = arr.length - 1;
    int ans = 0;
    while (start <= end) {
        int mid = start + (end - start) / 2;
        if (arr[mid] == target) {
            ans = mid;
            if (left) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        } else if (arr[mid] < target) {
            start = mid + 1;
        } else {
            end = mid - 1;
        }
    }
    return ans;
}
```

#### Finding the Peak Element in a Bitonic (Mountain) Array

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(peak(arr));
}

private static int peak(int[] arr) {
    int start = 0, end = arr.length - 1;
    while (start < end) {
        int mid = start + (end - start) / 2;
        if (arr[mid] < arr[mid + 1]) {
            start = mid + 1;
        } else {
            end = mid;
        }
    }
    return start;
}
```

#### Searching an Element in a Rotated Sorted Array

```java
public static void main(String[] args) {
    System.out.println(searchInRotatedArray(new int[] { 4, 5, 6, 7, 0, 1, 2 }, 0));
}

private static int searchInRotatedArray(int[] arr, int target) {
    if (arr.length == 0) {
        return -1;
    }
    int start = 0, end = arr.length - 1;
    while (start <= end) {
        int mid = start + (end - start) / 2;
        // if rotated array contains duplicates then add below code
        // if (arr[start] == arr[mid] && arr[mid] == arr[end]) {
        // start++;
        // end--;
        // }

        if (arr[mid] == target) {
            return mid;
        } else if (arr[start] <= arr[mid]) {
            if (arr[start] <= target && target < arr[mid]) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        } else {
            if (arr[end] >= target && target > arr[mid]) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
    }
    return -1;
}
```

#### Counting the Number of Rotations in a Rotated Sorted Array

```java
public static void main(String[] args) {
    System.out.println(countOfRotation(new int[] { 4, 5, 6, 7, 0, 1, 2 }));
}

private static int countOfRotation(int[] arr) {
    if (arr.length == 0) {
            return -1;
        }
        int start = 0, end = arr.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (mid > start && arr[mid] < arr[mid - 1]) {
                return mid;
            } else if (mid < end && arr[mid] > arr[mid + 1]) {
                return mid + 1;
            } else if (arr[mid] <= arr[start]) {
                end = mid + 1;
            } else {
                start = mid - 1;
            }
        }
        return -1;
}
```
---

Here is the updated Bit Manipulations section for your GitHub README:

---

## Bit Manipulations

Bit manipulation is the act of algorithmically manipulating bits or binary digits, which are the most basic form of data in computers.

### Bitwise Operations Table

| Operation | Symbol | Description                         |
|-----------|--------|-------------------------------------|
| AND       | `&`    | Sets each bit to 1 if both bits are 1 |
| OR        | `\|`   | Sets each bit to 1 if one of the bits is 1 |
| NOT       | `~`    | Inverts all the bits                |
| XOR       | `^`    | Sets each bit to 1 if only one of the bits is 1 |
| Left Shift  | `<<`   | Shifts bits to the left             |
| Right Shift | `>>`   | Shifts bits to the right            |

**Example: Bitwise AND Operation**

```java
public class BitwiseAnd {
    public static void main(String[] args) {
        int a = 5;  // 0101 in binary
        int b = 3;  // 0011 in binary
        
        int result = a & b;  // 0001 in binary
        
        System.out.println("Bitwise AND: " + result);  // Output: 1
    }
}
```

### Print Even Numbers Using Bitwise AND

```java
public class PrintEven {
    public static void main(String[] args) {
        printEven(new int[] { 1, 10, 2, 20, 40, 200 });
    }

    private static void printEven(int[] arr) {
        for (int val : arr) {
            if ((val & 1) != 1) {
                System.out.println(val);
            }
        }
    }
}
```

### Print Odd Numbers Using Bitwise AND

```java
public class PrintOdd {
    public static void main(String[] args) {
        printOdd(new int[] { 1, 10, 2, 20, 40, 200 });
    }

    private static void printOdd(int[] arr) {
        for (int val : arr) {
            if ((val & 1) == 1) {
                System.out.println(val);
            }
        }
    }
}
```

### Find Non-Duplicate Element Using XOR

```java
public class FindNonDuplicate {
    public static void main(String[] args) {
        findNonDuplicate(new int[] { 1, 1, 4, 4, 5, 6, 6 });
    }

    private static void findNonDuplicate(int[] arr) {
        // Array contains elements double duplicate only one element is single
        int xor = 0;
        for (int val : arr) {
            xor = xor ^ val;
        }
        System.out.println(xor);
    }
}
```

### Power of a Number Using Bitwise Operators

```java
public class Power {
    public static void main(String[] args) {
        System.out.println(power(2, 2));
    }

    private static int power(int val, int power) {
        int ans = 1;
        int base = val;
        while (power > 0) {
            if ((power & 1) == 1) {
                ans *= base;
            }
            base *= base;
            power >>= 1;
        }
        return ans;
    }
}
```

### Convert Decimal to Binary Using Bitwise Operators

```java
public class DecimalToBinary {
    public static void main(String[] args) {
        System.out.println(decimalToBinary(3));
    }

    private static int decimalToBinary(int n) {
        if (n == 0) {
            return 0;
        }

        int base = 1;
        int ans = 0;
        while (n > 0) {
            int bit = n & 1;
            ans += bit * base;
            base *= 10;
            n >>= 1;
        }

        return ans;
    }
}
```

### Convert Binary to Decimal Using Bitwise Operators

```java
public class BinaryToDecimal {
    public static void main(String[] args) {
        System.out.println(binaryToDecimal(1011));
    }

    private static int binaryToDecimal(long n) {
        if (n == 0) {
            return 0;
        }
        int ans = 0;
        int base = 0;

        while (n > 0) {
            int bit = (int) (n % 10);
            ans += bit << base;
            base++;
            n /= 10;
        }

        return ans;
    }
}
```
---

## String Handling

### String
String is a sequence of characters. Java provides the `String` class to create and manipulate strings.

**Example: String Manipulations**

```java
public class StringManipulations {
    public static void main(String[] args) {
        String str = "Hello, World!";
        
        // Basic methods
        System.out.println(str.length());  // Output: 13
        System.out.println(str.charAt(1));  // Output: e
        System.out.println(str.substring(0, 5));  // Output: Hello
        System.out.println(str.toUpperCase());  // Output: HELLO, WORLD!
        System.out.println(str.toLowerCase());  // Output: hello, world!
        System.out.println(str.replace("World", "Java"));  // Output: Hello, Java!
        
        // Additional methods
        System.out.println(str.contains("World"));  // Output: true
        System.out.println(String.join("-", "Hello", "World"));  // Output: Hello-World
        System.out.println(str.isEmpty());  // Output: false
        System.out.println(str.concat(" Welcome!"));  // Output: Hello, World! Welcome!
        String[] parts = str.split(", ");
        for (String part : parts) {
            System.out.println(part);  // Output: Hello\nWorld!
        }
        System.out.println("   Hello   ".trim());  // Output: Hello
        System.out.println(str.replace('o', 'O'));  // Output: HellO, WOrld!
    }
}
```

### StringBuffer
StringBuffer is a thread-safe, mutable sequence of characters. It is used to create modifiable strings.

**Example: StringBuffer Manipulations**

```java
public class StringBufferExample {
    public static void main(String[] args) {
        StringBuffer sb = new StringBuffer("Hello");
        
        sb.append(", World!");
        System.out.println(sb);  // Output: Hello, World!
        
        sb.insert(5, " Java");
        System.out.println(sb);  // Output: Hello Java, World!
        
        sb.replace(5, 10, "Code");
        System.out.println(sb);  // Output: Hello Code, World!
        
        sb.delete(5, 10);
        System.out.println(sb);  // Output: Hello, World!
        
        sb.reverse();
        System.out.println(sb);  // Output: !dlroW ,olleH
        
        // Additional methods
        System.out.println(sb.capacity());  // Output: Current capacity of StringBuffer
        System.out.println(sb.charAt(0));  // Output: !
        System.out.println(sb.substring(0, 5));  // Output: !dlro
        sb.deleteCharAt(0);
        System.out.println(sb);  // Output: dlroW ,olleH
        System.out.println(sb.toString());  // Output: dlroW ,olleH
    }
}
```

### StringBuilder
StringBuilder is similar to StringBuffer but is not synchronized, making it faster for single-threaded applications.

**Example: StringBuilder Manipulations**

```java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");
        
        sb.append(", World!");
        System.out.println(sb);  // Output: Hello, World!
        
        sb.insert(5, " Java");
        System.out.println(sb);  // Output: Hello Java, World!
        
        sb.replace(5, 10, "Code");
        System.out.println(sb);  // Output: Hello Code, World!
        
        sb.delete(5, 10);
        System.out.println(sb);  // Output: Hello, World!
        
        sb.reverse();
        System.out.println(sb);  // Output: !dlroW ,olleH
        
        // Additional methods
        System.out.println(sb.capacity());  // Output: Current capacity of StringBuilder
        System.out.println(sb.charAt(0));  // Output: !
        System.out.println(sb.substring(0, 5));  // Output: !dlro
        sb.deleteCharAt(0);
        System.out.println(sb);  // Output: dlroW ,olleH
        System.out.println(sb.toString());  // Output: dlroW ,olleH
    }
}
```

### Reverse a String

```java
public class ReverseString {
    public static void main(String[] args) {
        System.out.println(reverse("Hello"));  // Output: olleH
    }

    private static String reverse(String str) {
        StringBuilder sb = new StringBuilder(str);
        int i = 0, j = str.length() - 1;
        while (i < j) {
            char ch = sb.charAt(i);
            sb.setCharAt(i++, sb.charAt(j));
            sb.setCharAt(j--, ch);
        }
        return sb.toString();
    }
}
```

### Check if a String is Palindrome

```java
public class PalindromeCheck {
    public static void main(String[] args) {
        System.out.println(isPalindrome("Abba"));  // Output: true
    }

    private static boolean isPalindrome(String str) {
        if (str.isEmpty()) {
            return true;
        }
        int i = 0, j = str.length() - 1;
        while (i <= j) {
            if (str.charAt(i++) != str.charAt(j--))
                return false;
        }
        return true;
    }
}
```

### Skip a Specific Character in a String

```java
public class SkipCharacter {
    public static void main(String[] args) {
        System.out.println(skipChar("Rupesh", 'u'));  // Output: Rpesh
    }

    private static String skipChar(String str, char ch) {
        StringBuilder sb = new StringBuilder(str);
        for (int i = 0; i < sb.length(); i++) {
            if (sb.charAt(i) == ch) {
                sb.deleteCharAt(i);
            }
        }
        return sb.toString();
    }
}
```

### Find All Permutations of a String

```java
import java.util.ArrayList;

public class SubStringPermutations {
    public static void main(String[] args) {
        System.out.println(subString("abc", ""));  // Output: [abc, acb, bac, bca, cab, cba]
    }

    private static ArrayList<String> subString(String p, String up) {
        if (p.isEmpty()) {
            ArrayList<String> list = new ArrayList<>();
            list.add(up);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        for (int i = 0; i < p.length(); i++) {
            char curr = p.charAt(i);
            String temp = p.substring(0, i) + p.substring(i + 1);
            list.addAll(subString(temp, up + curr));
        }
        return list;
    }
}
```

### Find All Subsequences of a String

```java
import java.util.ArrayList;

public class Subsequences {
    public static void main(String[] args) {
        System.out.println(subSeq("", "abc"));  // Output: [abc, ab, ac, a, bc, b, c, ]
    }

    private static ArrayList<String> subSeq(String p, String up) {
        if (up.isEmpty()) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        list.addAll(subSeq(p + up.charAt(0), up.substring(1)));
        list.addAll(subSeq(p, up.substring(1)));
        return list;
    }
}
```

### Permutations of Dice

```java
import java.util.ArrayList;

public class DicePermutations {
    public static void main(String[] args) {
        System.out.println(permutationsOfDice("", 5));  // Output: [1,1,1,1,1, 1,1,1,2, 1,1,2,1, ...]
    }

    private static ArrayList<String> permutationsOfDice(String p, int target) {
        if (target == 0) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        for (int i = 1; i <= 6 && i <= target; i++) {
            list.addAll(permutationsOfDice(p + i + (target - i == 0 ? "" : ","), target - i));
        }
        return list;
    }
}
```

### Find All Paths in a Grid

```java
import java.util.ArrayList;

public class GridPaths {
    public static void main(String[] args) {
        System.out.println(allPaths(3, 3, ""));  // Output: [VV, VDR, VRD, DVR, DDRR, ...]
    }

    private static ArrayList<String> allPaths(int row, int col, String p) {
        if (row == 1 && col == 1) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        if (row > 1 && col > 1) {
            list.addAll(allPaths(row - 1, col - 1, p + 'V'));
        }
        if (row > 1) {
            list.addAll(allPaths(row - 1, col, p + 'D'));
        }
        if (col > 1) {
            list.addAll(allPaths(row, col - 1, p + 'R'));
        }
        return list;
    }
}
```

---

This README file provides a comprehensive guide to the content of your DSA repository, including examples and detailed explanations.

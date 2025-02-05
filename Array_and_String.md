Basic Java Array and String Questions
1. Find All Subarrays of an Array

Problem: Print all possible subarrays of a given array.

Example:
Input: [1, 2, 3]
Output:
[1]
[1, 2]
[1, 2, 3]
[2]
[2, 3]
[3]

Solution:
```java
public class Subarrays {
    public static void printSubarrays(int[] arr) {
        int n = arr.length;
        for (int start = 0; start < n; start++) {
            for (int end = start; end < n; end++) {
                for (int k = start; k <= end; k++) {
                    System.out.print(arr[k] + " ");
                }
                System.out.println();
            }
        }
    }
    public static void main(String[] args) {
        int[] arr = {1, 2, 3};
        printSubarrays(arr);
    }
}
```

2. Count the Number of Words in a String

Problem: Given a string, count the number of words (words are separated by spaces).

Example:
Input: "Hello Java World"
Output: 3

Solution:
```java
public class WordCount {
    public static int countWords(String str) {
        if (str == null || str.isEmpty()) return 0;
        String[] words = str.trim().split("\s+");
        return words.length;
    }
    public static void main(String[] args) {
        String str = "Hello Java World";
        System.out.println("Word Count: " + countWords(str));
    }
}
```

3. Count the Frequency of Characters in a String

Problem: Given a string, count the occurrence of each character.

Example:
Input: "hello"
Output:
h: 1
e: 1
l: 2
o: 1

Solution:
```java
import java.util.HashMap;

public class CharFrequency {
    public static void countFrequency(String str) {
        HashMap<Character, Integer> map = new HashMap<>();
        for (char c : str.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        for (char key : map.keySet()) {
            System.out.println(key + ": " + map.get(key));
        }
    }
    public static void main(String[] args) {
        String str = "hello";
        countFrequency(str);
    }
}
```

4. Reverse a String

Problem: Reverse a given string.

Example:
Input: "Java"
Output: "avaJ"

Solution:
```java
public class ReverseString {
    public static String reverse(String str) {
        return new StringBuilder(str).reverse().toString();
    }
    public static void main(String[] args) {
        String str = "Java";
        System.out.println("Reversed String: " + reverse(str));
    }
}
```

5. Check if a String is a Palindrome

Problem: Check whether a string reads the same forward and backward.

Example:
Input: "madam"
Output: true

Solution:
```java
public class PalindromeCheck {
    public static boolean isPalindrome(String str) {
        int left = 0, right = str.length() - 1;
        while (left < right) {
            if (str.charAt(left) != str.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
    public static void main(String[] args) {
        String str = "madam";
        System.out.println("Is Palindrome: " + isPalindrome(str));
    }
}
```

6. Find the Longest Substring Without Repeating Characters

Problem: Find the length of the longest substring without repeating characters.

Example:
Input: "abcabcbb"
Output: 3  (Substring: "abc")

Solution:
```java
import java.util.HashSet;

public class LongestSubstring {
    public static int lengthOfLongestSubstring(String s) {
        HashSet<Character> set = new HashSet<>();
        int maxLength = 0, left = 0;
        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLength = Math.max(maxLength, right - left + 1);
        }
        return maxLength;
    }
    public static void main(String[] args) {
        String str = "abcabcbb";
        System.out.println("Longest Substring Length: " + lengthOfLongestSubstring(str));
    }
}
```

7. Check if Two Strings are Anagrams

Problem: Given two strings, check if they are anagrams (contain the same characters in a different order).

Example:
Input: "listen", "silent"
Output: true

Solution:
```java
import java.util.Arrays;

public class AnagramCheck {
    public static boolean areAnagrams(String str1, String str2) {
        if (str1.length() != str2.length()) return false;
        char[] arr1 = str1.toCharArray();
        char[] arr2 = str2.toCharArray();
        Arrays.sort(arr1);
        Arrays.sort(arr2);
        return Arrays.equals(arr1, arr2);
    }
    public static void main(String[] args) {
        String str1 = "listen";
        String str2 = "silent";
        System.out.println("Are Anagrams: " + areAnagrams(str1, str2));
    }
}
```

8. Find the First Non-Repeating Character

Problem: Find the first character in a string that does not repeat.

Example:
Input: "swiss"
Output: "w"

Solution:
```java
import java.util.LinkedHashMap;

public class FirstNonRepeating {
    public static char firstUniqueChar(String str) {
        LinkedHashMap<Character, Integer> map = new LinkedHashMap<>();
        for (char c : str.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        for (char key : map.keySet()) {
            if (map.get(key) == 1) {
                return key;
            }
        }
        return '-'; // Return '-' if no unique character is found
    }
    public static void main(String[] args) {
        String str = "swiss";
        System.out.println("First Non-Repeating Character: " + firstUniqueChar(str));
    }
}
```


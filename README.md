# 🧩 LeetCode 10: Regular Expression Matching (C++)

A comprehensive Dynamic Programming solution to implement regular expression matching with support for '.' and '*'.

## 📖 Problem Description
Given an input string `s` and a pattern `p`, implement regular expression matching with support for:
- `.` Matches any single character.​​​​
- `*` Matches zero or more of the preceding element.

The matching should cover the **entire** input string (not partial).

### Example
- **Input:** `s = "aa"`, `p = "a*"`
- **Output:** `true`
- **Explanation:** '*' means zero or more of the preceding element, 'a'. Therefore, by repeating 'a' once, it becomes "aa".

## 🛠️ Technical Approach
This problem is solved using **2D Dynamic Programming**:
1. **State Definition:** `dp[i][j]` represents whether the first `i` characters of `s` match the first `j` characters of `p`.
2. **Base Case:** `dp[0][0] = true` (empty string matches empty pattern).
3. **Pattern Initialization:** Handled patterns like `a*` or `a*b*` which can match an empty string.
4. **Transition Logic:**
   - **Matching Characters (or `.`):** If `p[j-1]` matches `s[i-1]`, we inherit the result from `dp[i-1][j-1]`.
   - **The `*` Wildcard:** 
     - **Case 1 (Zero occurrences):** Look back two steps in the pattern (`dp[i][j-2]`).
     - **Case 2 (One or more occurrences):** If the preceding character in `p` matches `s[i-1]`, we check `dp[i-1][j]`.

## 📊 Complexity Analysis
- **Time Complexity:** $O(m \times n)$ — Where $m$ is the length of the string and $n$ is the length of the pattern.
- **Space Complexity:** $O(m \times n)$ — To store the 2D DP table.

## 💡 Key Edge Cases Handled
- Empty string with a complex pattern (e.g., `s = ""`, `p = "a*b*"`).
- Patterns starting with `*` (though constraints usually prevent this).
- Sequences of `.*` which can match any string.

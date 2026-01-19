### Valid Parentheses

You are given a string s consisting of the following characters: '(', ')', '{', '}', '[' and ']'.

The input string s is valid if and only if:

Every open bracket is closed by the same type of close bracket.
Open brackets are closed in the correct order.  
Every close bracket has a corresponding open bracket of the same type.  

Return true if s is a valid string, and false otherwise.

### Example 1:

Input: s = "[]"

Output: true

### Example 2:

Input: s = "([{}])"

Output: true

### Example 3:

Input: s = "[(])"

Output: false

Explanation: The brackets are not closed in the correct order.

### Constraints:

1 <= s.length <= 1000


### Solution

```python
def isValid(self, s: str) -> bool:
    stack = []
    open_chars = ["(", "{", "["]
    close_chars = [")", "}", "]"]
    for char in s:
        if char in open_chars:
            stack.append(char)
        elif char in close_chars:
            if stack and open_chars.index(stack[-1]) == close_chars.index(char):
                stack = stack[:-1]
            else:
                return False
        
    if not stack: return True
    else: return False
```
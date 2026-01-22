# Evaluate Reverse Polish Notation

You are given an array of strings tokens that represents a valid arithmetic expression in Reverse Polish Notation.

Return the integer that represents the evaluation of the expression.

The operands may be integers or the results of other operations.
The operators include '+', '-', '*', and '/'.
Assume that division between integers always truncates toward zero.

### Example 1:

Input: tokens = ["1","2","+","3","*","4","-"]

Output: 5

Explanation: ((1 + 2) * 3) - 4 = 5

### Constraints:

1 <= tokens.length <= 1000.  
tokens[i] is "+", "-", "*", or "/", or a string representing an integer in the range [-100, 100].

### Solution

```python
def evalRPN(self, tokens: List[str]) -> int:
    stack = []
    for token in tokens:
        if token == "+":
            stack.append(stack.pop() + stack.pop())
        elif token == "-":
            val_b = stack.pop()
            val_a = stack.pop()
            stack.append(val_a - val_b)
        elif token == "*":
            stack.append(stack.pop() * stack.pop())
        elif token == "/":
            val_b = stack.pop()
            val_a = stack.pop()
            stack.append(int(val_a / val_b))
        else:
            stack.append(int(token))
    return stack[-1]
```
                        
        
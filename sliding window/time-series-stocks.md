# Best Time to Buy and Sell Stock

You are given an integer array prices where prices[i] is the price of DogeCoin on the ith day.

You may choose a single day to buy one DogeCoin and choose a different day in the future to sell it.

Return the maximum profit you can achieve. You may choose to not make any transactions, in which case the profit would be 0.

### Example 1:

Input: prices = [10,1,5,6,7,1]

Output: 6
Explanation: Buy prices[1] and sell prices[4], profit = 7 - 1 = 6.

### Example 2:

Input: prices = [10,8,7,5,2]

Output: 0
Explanation: No profitable transactions can be made, thus the max profit is 0.

### Constraints:

1 <= prices.length <= 100
0 <= prices[i] <= 100


### Solution:


```python
def maxProfit(self, prices: List[int]) -> int:
    maxp = []
    for i in range(len(prices)):
        diff = []
        for j in range(i, len(prices)):
            if prices[j] - prices[i]:
                diff.append(prices[j] - prices[i])
        print(diff)
        if diff: maxp.append(max(diff))
    if maxp and max(maxp) > 0: return max(maxp)
    else: return 0
```
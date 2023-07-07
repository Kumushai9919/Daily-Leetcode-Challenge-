# Day 8
## 121. Best Time to Buy and Sell Stock





###### Easy  | <a href="https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/">leetcode link </a> |Dynalic Programming Array  



#### 1. Introduction:

The problem is to maximize the profit by buying and selling a stock represented by its prices on different days. We need to find the maximum profit that can be achieved by choosing a day to buy the stock and a different day in the future to sell it.

##### Example 1:
````
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

````

#### 2. Approach:
The approach to solve the Best Time to Buy and Sell Stock problem is to use the two-pointer technique. We initialize two pointers, l and r, representing the left and right indices of the array. The l pointer points to the day we buy the stock, and the r pointer points to the day we sell the stock. We iterate through the array and update the maximum profit if a higher profit is obtained.
#### 3. Explanation:

1. Initialize variables: We initialize the maximum profit, max, to 0. The l pointer is set to 0, representing the first day, and the r pointer is set to 1, representing the second day.

2. Calculate the profit: In each iteration, we compare the prices at indices l and r. If the price at l is less than the price at r, it means a profit can be obtained. We calculate the profit as prices[r] - prices[l] and update the maximum profit, max, if the current profit is higher.

3. Update the pointers: If the price at l is greater than or equal to the price at r, it means the current l day is not a good day to buy the stock. In this case, we update the l pointer to the r index, and move the r pointer to the next day.

4. Repeat until reaching the end of the array: We continue the above steps until the r pointer reaches the end of the array.

5. Return the maximum profit: After the loop ends, we return the maximum profit, max, as the result.
By following this approach, we can find the maximum profit that can be achieved by buying and selling the stock. The two-pointer technique allows us to efficiently iterate through the array and update the maximum profit in a single pass, resulting in a time complexity of O(n), where n is the length of the input array.

### Java Solution:
````
 class Solution {
    public int maxProfit(int[] prices) {

        int max = 0;

        int l = 0;
        int r = 1;

        while(r < prices.length){

            if(prices[l] < prices[r]){
                int profit = prices[r] - prices[l];
                max = Math.max(profit, max);
            }
            else{
                l = r;
            }
            r++;

        } 

        return max;
        
    }
}
````

### 1480. RUNNING SUM OF 1D ARRAY
---
Given an array `nums`. We define a running sum of an array as 
`runningSum[i] = sum(nums[0]…nums[i])`.
**Return** **the running sum of `nums`.**

`**Input:** nums = [1,2,3,4]
**Output:** [1,3,6,10]
**Explanation:** Running sum is obtained as follows: [1, 1+2, 1+2+3, 1+2+3+4].`

----
#### Loops
`nums[] = [1, 2, 3, 4]` 
`i = 1`
`nums[] = [1, 3, 3, 4]`
`i = 2`
`nums[] = [1, 3, 6, 4]`
`i = 3`
`nums[] = [1, 3, 6, 10]`

	 nums[ i ]  += nums[ i - 1 ]; 
	 nums[ i ]  += prevSum;

---
---


### 724. FIND PIVOT INDEX
---
Given an array of integers `nums`, calculate the **pivot index** of this array.

The **pivot index** is the index where the sum of all the numbers **strictly** to the left of the index is equal to the sum of all the numbers **strictly** to the index's right.

If the index is on the left edge of the array, then the left sum is `0` because there are no elements to the left. This also applies to the right edge of the array.

Return _the **leftmost pivot index**_. If no such index exists, return `-1`.

**Input:** nums = [1,7,3,6,5,6]
**Output:** 3
**Explanation:**
The pivot index is 3.
Left sum = nums[0] + nums[1] + nums[2] = 1 + 7 + 3 = 11
Right sum = nums[4] + nums[5] = 5 + 6 = 11

----
#### Loops
`nums[] = [1,7,3,6,5,6]` 
`i = 0`
`totalSum = 28`
`leftSum = 1 = nums[0]`
`rightSum = 7 + 3 + 6 + 5 + 6 =  = totalSum - leftSum`

`leftSum` runs from 0 -> current pointer
`rightSum` runs from last -> current pointer + 1 or `= totalSum - leftSum`
Solution
Approach #1 Brute Force [Time Limit Exceeded]
Algorithm

The brute force approach is really simple. We consider every possible subarray within the given array and count the number of zeros and ones in each subarray. Then, we find out the maximum size subarray with equal no. of zeros and ones out of them.
Implementation
Complexity Analysis

    Time complexity : O(n2). We consider every possible subarray by traversing over the complete array for every start point possible.

    Space complexity : O(1). Only two variables zeroes and ones are required.

Approach #2 Using Extra Array [Accepted]
Algorithm

In this approach, we make use of a count variable, which is used to store the relative number of ones and zeros encountered so far while traversing the array. The count variable is incremented by one for every 1 encountered and the same is decremented by one for every 0 encountered.

We start traversing the array from the beginning. If at any moment, the count becomes zero, it implies that we've encountered an equal number of zeros and ones from the beginning till the current index of the array(i). Not only this, another point to be noted is that if we encounter the same count twice while traversing the array, it means that the number of zeros and ones are equal between the indices corresponding to the equal count values. The following figure illustrates the observation for the sequence [0 0 1 0 0 0 1 1]:

Contiguous_Array

In the above figure, the subarrays between (A,B), (B,C), and (A,C) (lying between indices corresponding to count=−2) have an equal number of zeros and ones.

Another point to be noted is that the largest subarray is the one between the points (A, C). Thus, if we keep a track of the indices corresponding to the same count values that lie farthest apart, we can determine the size of the largest subarray with equal no. of zeros and ones easily.

Now, the count values can range between -n to +n, with the extreme points corresponding to the complete array being filled with all 0's and all 1's respectively. Thus, we make use of an array arr(of size 2n+1to keep track of the various count's encountered so far. We make an entry containing the current element's index (i) in the arr for a new count encountered everytime. Whenever we come across the same count value later while traversing the array, we determine the length of the subarray lying between the indices corresponding to the same count values.
Implementation
Complexity Analysis

    Time complexity : O(n). The complete array is traversed only once.

    Space complexity : O(n). arr array of size 2n+1 is used.

Approach #3 Using HashMap [Accepted]
Algorithm

This approach relies on the same premise as the previous approach. But, we need not use an array of size 2n+1, since it isn't necessary that we'll encounter all the count values possible. Thus, we make use of a HashMap map to store the entries in the form of (index,count). We make an entry for a count in the map whenever the count is encountered first, and later on use the corresponding index to find the length of the largest subarray with equal no. of zeros and ones when the same count is encountered again.

The following animation depicts the process:

Current
Implementation
Complexity Analysis

    Time complexity : O(n). The entire array is traversed only once.

    Space complexity : O(n). Maximum size of the HashMap map will be n, if all the elements are either 1 or 0.

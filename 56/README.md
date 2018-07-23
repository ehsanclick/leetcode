## Merge Intervals

[Description](https://leetcode.com/problems/merge-intervals/description/)

Given a collection of intervals, merge all overlapping intervals.

Example 1:
```
Input: [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
```
Example 2:
```
Input: [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considerred overlapping.
```
[Solution]()
```c++
/**
 * Definition for an interval.
 * struct Interval {
 *     int start;
 *     int end;
 *     Interval() : start(0), end(0) {}
 *     Interval(int s, int e) : start(s), end(e) {}
 * };
 */
class Solution {
public:
    vector<Interval> merge(vector<Interval>& intervals) {
        if (intervals.size() <= 1) return intervals;
        sort(intervals.begin(), intervals.end(), [](Interval a, Interval b){return a.start < b.start;});
        vector<Interval> res;
        res.push_back(intervals[0]);
        for (auto a: intervals){
            if (res.back().end >= a.start)
                res.back().end = max(a.end, res.back().end);
            else
                res.push_back(a);
        }
        return res;
    }
};
```

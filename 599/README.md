## Minimum Index Sum of Two Lists

[Description](https://leetcode.com/problems/minimum-index-sum-of-two-lists/description/)

Suppose Andy and Doris want to choose a restaurant for dinner, and they both have a list of favorite restaurants represented by strings.

You need to help them find out their common interest with the least list index sum. If there is a choice tie between answers, output all of them with no order requirement. You could assume there always exists an answer.

**Example 1:**
```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["Piatti", "The Grill at Torrey Pines", "Hungry Hunter Steakhouse", "Shogun"]
Output: ["Shogun"]
Explanation: The only restaurant they both like is "Shogun".
```

**Example 2:**
```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["KFC", "Shogun", "Burger King"]
Output: ["Shogun"]
Explanation: The restaurant they both like and have the least index sum is "Shogun" with index sum 1 (0+1).
```

[Solution] https://leetcode.com/problems/minimum-index-sum-of-two-lists/solution/

### HashMap
### Without Using HashMap

### Without Using HashMap

[See video](https://leetcode.com/problems/minimum-index-sum-of-two-lists/solution/#approach-2-without-using-hashmap-accepted)

```c++
vector<string> findRestaurant(vector<string>& list1, vector<string>& list2) {
    vector<string> res;
    int sumInd = list1.size() + list2.size();
    //cout << sumInd << '\t';
    for (int i = 0; i < list1.size(); i++){
        //cout << i << ',' << sumInd << ' ';
        if (i > sumInd) break;
        for (int j = 0; j < list2.size(); j++){
            if (i + j > sumInd) break;
            if (list1[i] == list2[j]){
                //cout << list1[i] << ' ';
                if (i+j < sumInd)
                    res.clear();
                res.push_back(list1[i]);
                sumInd = i + j;
            }
        }
    }
    return res;
}
```
### HashMap

```c++
vector<string> findRestaurant2(vector<string>& list1, vector<string>& list2) {
    unordered_map<string, int> hash;
    vector<string> * shList = (list1.size() <= list2.size()) ? &list1 : &list2;
    vector<string> * longList = (list1.size() > list2.size()) ? &list1 : &list2;
    for (int i = 0; i < longList->size(); i++){
        hash[longList->at(i)] = i;
    }
    int sumInd = INT_MAX;
    vector<string> res;
    unordered_map<string, int>::const_iterator it;
    for (int j = 0; j < shList->size(); j++){
        it = hash.find(shList->at(j));
        if (it != hash.end() and it->second + j <= sumInd){
            if (it->second + j < sumInd)
                res.clear();
            res.push_back(shList->at(j));
            sumInd =it->second + j;
        }
    }
    return res;
}
```


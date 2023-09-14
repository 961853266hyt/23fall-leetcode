# Day35 错题()

### 860

```c++
/*time: O(n) space: O(1) */
class Solution {
public:
    bool lemonadeChange(vector<int>& bills) {
        int five = 0;
        int ten = 0;
        int twt = 0;
        for(int bill:bills) {
            if (bill == 5) {
                five++;
            } else if (bill == 10) {
                if (five == 0) {
                    return false;
                }
                ten++;
                five--;
            } else {
                twt++;
                if (five >= 1 && ten >= 1) {
                    five -= 1;
                    ten -= 1;
                } else if (five >= 3) {
                    five -= 3;
                } else {
                    return false;
                }
            }
        }
        return true;
    }
};
```

### 406

```c++
/*time: O(nlogn + n ^ 2) space: O(n) */
bool cmp(vector<int>& a, vector<int>& b) {
    if (a[0] == b[0])
        return a[1] < b[1];
    return a[0] > b[0];
}

class Solution {
public:
    vector<vector<int>> reconstructQueue(vector<vector<int>>& people) {
        vector<vector<int>> ans;
        sort(people.begin(), people.end(), cmp);
        for (int i = 0; i < people.size(); i++) {
            int h = people[i][0];
            int k = people[i][1];
            if (k == i) {
                ans.push_back(people[i]);
            }
            if (k < i) {
                ans.insert(ans.begin() + k, people[i]);
            } 
        }
        return ans;
    }
};
```

### 452

```c++
/*time: O(nlogn) space: O(logn) */
bool cmp(vector<int>& a, vector<int>& b) {
        return  a[0] < b[0];
}
class Solution {
public:
    int findMinArrowShots(vector<vector<int>>& points) {
        sort(points.begin(), points.end(), cmp);
        int curx1 = points[0][0], curx2 = points[0][1];
        int arrow = 1;
        for (int i = 0; i < points.size(); i++) {
            int x1 = points[i][0];
            int x2 = points[i][1];
            if (x1 <= curx2) {
                curx1 = x1;
                curx2 = min(curx2, x2);
            } else {
                arrow++;
                curx1 = x1;
                curx2 = x2;
            }
        }
        return arrow;
    }
};
```


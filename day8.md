# Day8 错题(替换空格)

### 344

```c++
/*time: O(n) space:O(1) */
class Solution {
public:
    void reverseString(vector<char>& s) {
        for(int i = 0, j = s.size() - 1; i < j; i++,j--) {
            swap(s[i],s[j]);
        }
    }   
};
```

### 541

```c++
/*time: O(n) space:O(1) */
class Solution {
public:
    string reverseStr(string s, int k) {
        int n = s.size();
        for(int i = 0; i < n; i += 2 * k) {
            reverse(s.begin() + i, s.begin() + i + min(k,n - i));
        }
        return s;
    }
};
```

### 剑指offer 05 替换空格

```c++
/*time: O(n) space:O(1) */
class Solution {
public:
    string replaceSpace(string s) {
        int count = 0,len = s.size();
        for(char c:s) {
            if (c == ' ') {
                count++;
            }
        }
        int newsize = len + 2 * count;
        s.resize(newsize);
        for(int i = len - 1, j = newsize - 1;i>=0 && j>=0;i--){
            if(s[i] == ' ') {
                s[j] = '0';
                s[j - 1] = '2';
                s[j - 2] = '%';
                j = j - 3;
            }
            else {
                s[j--] = s[i];
            }
        }
        return s;
    }
};
```

### 151

```c++
/*time: O(n^3) space:O(logn) */

```

  ### 剑指Offer58-II.左旋转字符串

```c++
/*time: O(n) space:O(1) */
class Solution {
public:
    string reverseLeftWords(string s, int n) {
        reverse(s.begin(),s.begin() + n);
        reverse(s.begin() + n, s.end());
        reverse(s.begin(),s.end());
        return s;
    }
};
```




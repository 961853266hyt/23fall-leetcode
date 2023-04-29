# Day9 错题(28)

### 28

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

### 459

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
/*time: O(n) space:O(1) */
class Solution {
public:
    void removeExtraSpaces(string& s) {
        int slow = 0;   
        for (int i = 0; i < s.size(); i++) { 
            if (s[i] != ' ') {                        //遇到非空格就处理，即删除所有空格。
                if (slow != 0) s[slow++] = ' ';       //手动控制空格，给单词之间添加空格。slow != 0说明不是第一个单词，需要在单词前添加空格。
                while (i < s.size() && s[i] != ' ') { //补上该单词，遇到空格说明单词结束。
                    s[slow++] = s[i++];
                }
            }
        }
        s.resize(slow); 
    }

    string reverseWords(string s) {
        removeExtraSpaces(s); 
        reverse(s.begin(), s.end());
        int start = 0; //单词的开始下标start
        for (int i = 0; i <= s.size(); i++) {
            if (i == s.size() || s[i] == ' ') { //到达空格或者串尾，说明一个单词结束
                reverse(s.begin() + start,s.begin() + i);
                start = i + 1; 
            }
        }
        return s;
    }
};
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




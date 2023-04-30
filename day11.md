# Day11 错题(1047, 150)

### 20

```c++
/*time: O(n) space:O(n) */
class Solution {
public:
    bool isValid(string s) {
        unordered_map<char,char> mp= {{'(',')'},{'{','}'},{'[',']'}};
        stack<char> stk;
        for(char c:s) {
            if (mp.count(c)){
                stk.push(c);
            }
            else {
                if (stk.empty()){
                    return false;
                }
                char tmp = stk.top();
                stk.pop();
                if (mp.count(tmp) && c == mp[tmp]) {
                    continue;
                }
                else {
                    return false;
                }
            }
        }
        return stk.empty();  
    }
};
```

### 1047

```c++
/*time: O(n) space:O(n) */
class Solution {
public:
    string removeDuplicates(string s) {
        string stk = "";
        for(char c:s) {
            if (stk.empty() || c != stk.back()) {
                stk.push_back(c);
            }
            else {
                stk.pop_back();
            }
        }
        return stk;
    }
};
```

### 150

```c++
/*time: O(n) space:O(1) */
class Solution {
public:
    int evalRPN(vector<string>& tokens) {
        stack<long> stk;
        set<string> op = {"+","-","*","/"}; 
        int sum = 0;
        for(auto str:tokens){
             auto iter = op.find(str);
            if (iter != op.end()) {
                auto b = stk.top();
                stk.pop();
                auto a = stk.top();
                stk.pop();
                if (*iter == "+") {
                    stk.push(a + b);
                }
                if (*iter == "-") {
                    stk.push(a - b);
                }
                if (*iter == "*") {
                    stk.push(a * b);
                }
                if (*iter == "/") {
                    stk.push(a / b);
                }
            }
            else {
                stk.push(stoi(str));
            }
        }
        return stk.top();
    }
};
```






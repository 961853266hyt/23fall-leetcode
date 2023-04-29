# Day10 错题()

### 232

```c++
class MyQueue {
public:
    stack<int> s_in;
    stack<int> s_out;
    MyQueue() {
        
    }

    void push(int x) {
        s_in.push(x);
    }
    
    int pop() {
        int res;
        if(!s_out.empty()){
            res = s_out.top();
            s_out.pop();
            return res;
        }
        while(!s_in.empty()) {
            int tmp = s_in.top();
            s_in.pop();
            s_out.push(tmp);
        }
        res = s_out.top();
        s_out.pop();
        return res;
    }
    
    int peek() {
        int res;
        if(!s_out.empty()){
            res = s_out.top();;
            return res;
        }
        while(!s_in.empty()) {
            int tmp = s_in.top();
            s_in.pop();
            s_out.push(tmp);
        }
        res = s_out.top();
        return res;
    }
    
    bool empty() {
        return s_in.empty() && s_out.empty();
    }
};

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue* obj = new MyQueue();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->peek();
 * bool param_4 = obj->empty();
 */
```

### 225

```c++
class MyStack {
public:
    deque<int> deq;
    MyStack() {

    }
    
    void push(int x) {
        deq.push_back(x);
    }
    
    int pop() {
        int tmp = deq.back();
        deq.pop_back();
        return tmp;
    }
    
    int top() {
        return deq.back();
    }
    
    bool empty() {
        return deq.empty();
    }
};

/**
 * Your MyStack object will be instantiated and called as such:
 * MyStack* obj = new MyStack();
 * obj->push(x);
 * int param_2 = obj->pop();
 * int param_3 = obj->top();
 * bool param_4 = obj->empty();
 */
```


# TCS DSA Interview Preparation - Standard C++ Solutions

## 1. Check if a number is prime
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0)
            return false;
    }
    return true;
}
```

## 2. Print all prime numbers up to N
```cpp
#include <bits/stdc++.h>
using namespace std;

void printPrimes(int n) {
    vector<bool> prime(n + 1, true);
    prime[0] = prime[1] = false;
    
    for (int i = 2; i * i <= n; i++) {
        if (prime[i]) {
            for (int j = i * i; j <= n; j += i)
                prime[j] = false;
        }
    }
    
    for (int i = 2; i <= n; i++) {
        if (prime[i]) cout << i << " ";
    }
}
```

## 3. Check if a string/number is palindrome
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isPalindrome(string s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s[left] != s[right]) return false;
        left++;
        right--;
    }
    return true;
}

bool isPalindromeNum(int n) {
    int original = n, reversed = 0;
    while (n > 0) {
        reversed = reversed * 10 + n % 10;
        n /= 10;
    }
    return original == reversed;
}
```

## 4. Count digits / separate even and odd digits of a number
```cpp
#include <bits/stdc++.h>
using namespace std;

int countDigits(int n) {
    if (n == 0) return 1;
    int count = 0;
    while (n > 0) {
        count++;
        n /= 10;
    }
    return count;
}

void separateEvenOdd(int n) {
    vector<int> even, odd;
    while (n > 0) {
        int digit = n % 10;
        if (digit % 2 == 0) even.push_back(digit);
        else odd.push_back(digit);
        n /= 10;
    }
    
    cout << "Even: ";
    for (int x : even) cout << x << " ";
    cout << "\nOdd: ";
    for (int x : odd) cout << x << " ";
}
```

## 5. Check if a number is Armstrong
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isArmstrong(int n) {
    int original = n, sum = 0, digits = 0;
    
    // Count digits
    int temp = n;
    while (temp > 0) {
        digits++;
        temp /= 10;
    }
    
    // Calculate sum of powers
    temp = n;
    while (temp > 0) {
        sum += pow(temp % 10, digits);
        temp /= 10;
    }
    
    return sum == original;
}
```

## 6. Calculate average of array elements
```cpp
#include <bits/stdc++.h>
using namespace std;

double calculateAverage(vector<int>& arr) {
    if (arr.empty()) return 0;
    
    long long sum = 0;
    for (int x : arr) sum += x;
    
    return (double)sum / arr.size();
}
```

## 7. Fibonacci sequence up to N
```cpp
#include <bits/stdc++.h>
using namespace std;

void fibonacci(int n) {
    if (n >= 1) cout << "0 ";
    if (n >= 2) cout << "1 ";
    
    int a = 0, b = 1;
    for (int i = 3; i <= n; i++) {
        int c = a + b;
        cout << c << " ";
        a = b;
        b = c;
    }
}
```

## 8. Sum of digits of a number
```cpp
#include <bits/stdc++.h>
using namespace std;

int sumOfDigits(int n) {
    int sum = 0;
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    return sum;
}
```

## 9. Count frequency of characters in a string
```cpp
#include <bits/stdc++.h>
using namespace std;

void countFrequency(string s) {
    unordered_map<char, int> freq;
    for (char c : s) freq[c]++;
    
    for (auto& p : freq) {
        cout << p.first << ": " << p.second << "\n";
    }
}
```

## 10. Reverse a string
```cpp
#include <bits/stdc++.h>
using namespace std;

string reverseString(string s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        swap(s[left], s[right]);
        left++;
        right--;
    }
    return s;
}
```

## 11. Reverse words in a sentence
```cpp
#include <bits/stdc++.h>
using namespace std;

string reverseWords(string s) {
    stringstream ss(s);
    string word, result;
    vector<string> words;
    
    while (ss >> word) words.push_back(word);
    
    for (int i = words.size() - 1; i >= 0; i--) {
        result += words[i];
        if (i > 0) result += " ";
    }
    return result;
}
```

## 12. Remove duplicates from array
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> removeDuplicates(vector<int>& arr) {
    unordered_set<int> seen;
    vector<int> result;
    
    for (int x : arr) {
        if (seen.find(x) == seen.end()) {
            seen.insert(x);
            result.push_back(x);
        }
    }
    return result;
}
```

## 13. Remove duplicates from string
```cpp
#include <bits/stdc++.h>
using namespace std;

string removeDuplicates(string s) {
    unordered_set<char> seen;
    string result;
    
    for (char c : s) {
        if (seen.find(c) == seen.end()) {
            seen.insert(c);
            result += c;
        }
    }
    return result;
}
```

## 14. Find first non-repeating character in a string
```cpp
#include <bits/stdc++.h>
using namespace std;

char firstNonRepeating(string s) {
    unordered_map<char, int> freq;
    for (char c : s) freq[c]++;
    
    for (char c : s) {
        if (freq[c] == 1) return c;
    }
    return '\0';
}
```

## 15. Pair sum in array (two-sum)
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> twoSum(vector<int>& arr, int target) {
    unordered_map<int, int> mp;
    
    for (int i = 0; i < arr.size(); i++) {
        int complement = target - arr[i];
        if (mp.find(complement) != mp.end()) {
            return {mp[complement], i};
        }
        mp[arr[i]] = i;
    }
    return {};
}
```

## 16. Largest and second largest element in array
```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int, int> findLargestSecondLargest(vector<int>& arr) {
    if (arr.size() < 2) return {-1, -1};
    
    int largest = INT_MIN, secondLargest = INT_MIN;
    
    for (int x : arr) {
        if (x > largest) {
            secondLargest = largest;
            largest = x;
        } else if (x > secondLargest && x != largest) {
            secondLargest = x;
        }
    }
    
    return {largest, secondLargest};
}
```

## 17. Find kth largest element in array
```cpp
#include <bits/stdc++.h>
using namespace std;

int findKthLargest(vector<int>& arr, int k) {
    priority_queue<int, vector<int>, greater<int>> minHeap;
    
    for (int x : arr) {
        minHeap.push(x);
        if (minHeap.size() > k) {
            minHeap.pop();
        }
    }
    
    return minHeap.top();
}
```

## 18. Sort an array (bubble sort)
```cpp
#include <bits/stdc++.h>
using namespace std;

void bubbleSort(vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
```

## 19. Check if two strings are anagrams
```cpp
#include <bits/stdc++.h>
using namespace std;

bool areAnagrams(string s1, string s2) {
    if (s1.length() != s2.length()) return false;
    
    sort(s1.begin(), s1.end());
    sort(s2.begin(), s2.end());
    
    return s1 == s2;
}
```

## 20. Maximum subarray sum (Kadane's algorithm)
```cpp
#include <bits/stdc++.h>
using namespace std;

int maxSubarraySum(vector<int>& arr) {
    int maxSum = arr[0], currentSum = arr[0];
    
    for (int i = 1; i < arr.size(); i++) {
        currentSum = max(arr[i], currentSum + arr[i]);
        maxSum = max(maxSum, currentSum);
    }
    
    return maxSum;
}
```

## 21. Matrix transpose
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> transpose(vector<vector<int>>& matrix) {
    int rows = matrix.size(), cols = matrix[0].size();
    vector<vector<int>> result(cols, vector<int>(rows));
    
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            result[j][i] = matrix[i][j];
        }
    }
    
    return result;
}
```

## 22. Matrix spiral print
```cpp
#include <bits/stdc++.h>
using namespace std;

void spiralPrint(vector<vector<int>>& matrix) {
    int top = 0, bottom = matrix.size() - 1;
    int left = 0, right = matrix[0].size() - 1;
    
    while (top <= bottom && left <= right) {
        // Print top row
        for (int i = left; i <= right; i++)
            cout << matrix[top][i] << " ";
        top++;
        
        // Print right column
        for (int i = top; i <= bottom; i++)
            cout << matrix[i][right] << " ";
        right--;
        
        // Print bottom row
        if (top <= bottom) {
            for (int i = right; i >= left; i--)
                cout << matrix[bottom][i] << " ";
            bottom--;
        }
        
        // Print left column
        if (left <= right) {
            for (int i = bottom; i >= top; i--)
                cout << matrix[i][left] << " ";
            left++;
        }
    }
}
```

## 23. Row sum / column sum in a matrix
```cpp
#include <bits/stdc++.h>
using namespace std;

void printRowColumnSums(vector<vector<int>>& matrix) {
    int rows = matrix.size(), cols = matrix[0].size();
    
    // Row sums
    cout << "Row sums: ";
    for (int i = 0; i < rows; i++) {
        int sum = 0;
        for (int j = 0; j < cols; j++) {
            sum += matrix[i][j];
        }
        cout << sum << " ";
    }
    
    // Column sums
    cout << "\nColumn sums: ";
    for (int j = 0; j < cols; j++) {
        int sum = 0;
        for (int i = 0; i < rows; i++) {
            sum += matrix[i][j];
        }
        cout << sum << " ";
    }
}
```

## 24. Pattern printing (common number/character patterns)
```cpp
#include <bits/stdc++.h>
using namespace std;

void printNumberTriangle(int n) {
    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            cout << j << " ";
        }
        cout << "\n";
    }
}
```

## 25. Segregate 0s and 1s in array
```cpp
#include <bits/stdc++.h>
using namespace std;

void segregate01(vector<int>& arr) {
    int left = 0, right = arr.size() - 1;
    
    while (left < right) {
        if (arr[left] == 0) left++;
        else if (arr[right] == 1) right--;
        else {
            swap(arr[left], arr[right]);
            left++;
            right--;
        }
    }
}
```

## 26. Count connected components in matrix
```cpp
#include <bits/stdc++.h>
using namespace std;

void dfs(vector<vector<int>>& matrix, int i, int j, vector<vector<bool>>& visited) {
    int rows = matrix.size(), cols = matrix[0].size();
    if (i < 0 || i >= rows || j < 0 || j >= cols || visited[i][j] || matrix[i][j] == 0)
        return;
    
    visited[i][j] = true;
    dfs(matrix, i+1, j, visited);
    dfs(matrix, i-1, j, visited);
    dfs(matrix, i, j+1, visited);
    dfs(matrix, i, j-1, visited);
}

int countComponents(vector<vector<int>>& matrix) {
    int rows = matrix.size(), cols = matrix[0].size();
    vector<vector<bool>> visited(rows, vector<bool>(cols, false));
    int count = 0;
    
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            if (matrix[i][j] == 1 && !visited[i][j]) {
                dfs(matrix, i, j, visited);
                count++;
            }
        }
    }
    return count;
}
```

## 27. Binary search on a sorted array
```cpp
#include <bits/stdc++.h>
using namespace std;

int binarySearch(vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    
    return -1;
}
```

## 28. Merge intervals
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> mergeIntervals(vector<vector<int>>& intervals) {
    if (intervals.empty()) return {};
    
    sort(intervals.begin(), intervals.end());
    vector<vector<int>> result;
    result.push_back(intervals[0]);
    
    for (int i = 1; i < intervals.size(); i++) {
        if (intervals[i][0] <= result.back()[1]) {
            result.back()[1] = max(result.back()[1], intervals[i][1]);
        } else {
            result.push_back(intervals[i]);
        }
    }
    
    return result;
}
```

## 29. Find intersection/union of two arrays
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> intersection(vector<int>& arr1, vector<int>& arr2) {
    unordered_set<int> set1(arr1.begin(), arr1.end());
    unordered_set<int> result;
    
    for (int x : arr2) {
        if (set1.count(x)) {
            result.insert(x);
        }
    }
    
    return vector<int>(result.begin(), result.end());
}
```

## 30. Balanced parentheses check
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isBalanced(string s) {
    stack<char> st;
    
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        } else {
            if (st.empty()) return false;
            
            char top = st.top();
            st.pop();
            
            if ((c == ')' && top != '(') ||
                (c == ']' && top != '[') ||
                (c == '}' && top != '{')) {
                return false;
            }
        }
    }
    
    return st.empty();
}
```

## 31. Linked list basics (reverse linked list)
```cpp
#include <bits/stdc++.h>
using namespace std;

struct ListNode {
    int val;
    ListNode* next;
    ListNode(int x) : val(x), next(nullptr) {}
};

ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* current = head;
    
    while (current) {
        ListNode* next = current->next;
        current->next = prev;
        prev = current;
        current = next;
    }
    
    return prev;
}
```

## 32. Merge two sorted linked lists
```cpp
#include <bits/stdc++.h>
using namespace std;

ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* current = &dummy;
    
    while (l1 && l2) {
        if (l1->val <= l2->val) {
            current->next = l1;
            l1 = l1->next;
        } else {
            current->next = l2;
            l2 = l2->next;
        }
        current = current->next;
    }
    
    current->next = l1 ? l1 : l2;
    return dummy.next;
}
```

## 33. Find loop in linked list
```cpp
#include <bits/stdc++.h>
using namespace std;

bool hasLoop(ListNode* head) {
    if (!head || !head->next) return false;
    
    ListNode* slow = head;
    ListNode* fast = head;
    
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        
        if (slow == fast) return true;
    }
    
    return false;
}
```

## 34. Simple tree traversal (inorder/preorder)
```cpp
#include <bits/stdc++.h>
using namespace std;

struct TreeNode {
    int val;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void inorderTraversal(TreeNode* root) {
    if (!root) return;
    
    inorderTraversal(root->left);
    cout << root->val << " ";
    inorderTraversal(root->right);
}
```

## 35. Find height of binary tree
```cpp
#include <bits/stdc++.h>
using namespace std;

int maxDepth(TreeNode* root) {
    if (!root) return 0;
    
    int leftHeight = maxDepth(root->left);
    int rightHeight = maxDepth(root->right);
    
    return 1 + max(leftHeight, rightHeight);
}
```

## 36. BFS/DFS on graph
```cpp
#include <bits/stdc++.h>
using namespace std;

void bfs(vector<vector<int>>& graph, int start) {
    vector<bool> visited(graph.size(), false);
    queue<int> q;
    
    visited[start] = true;
    q.push(start);
    
    while (!q.empty()) {
        int node = q.front();
        q.pop();
        cout << node << " ";
        
        for (int neighbor : graph[node]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}
```

## 37. String shift / rotate string
```cpp
#include <bits/stdc++.h>
using namespace std;

bool isRotation(string s1, string s2) {
    if (s1.length() != s2.length()) return false;
    
    string concatenated = s1 + s1;
    return concatenated.find(s2) != string::npos;
}
```

## 38. Subset generation / power set
```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> generateSubsets(vector<int>& nums) {
    vector<vector<int>> result;
    int n = nums.size();
    
    for (int i = 0; i < (1 << n); i++) {
        vector<int> subset;
        for (int j = 0; j < n; j++) {
            if (i & (1 << j)) {
                subset.push_back(nums[j]);
            }
        }
        result.push_back(subset);
    }
    
    return result;
}
```

## 39. Longest common prefix
```cpp
#include <bits/stdc++.h>
using namespace std;

string longestCommonPrefix(vector<string>& strs) {
    if (strs.empty()) return "";
    
    string prefix = strs[0];
    
    for (int i = 1; i < strs.size(); i++) {
        while (strs[i].find(prefix) != 0) {
            prefix = prefix.substr(0, prefix.length() - 1);
            if (prefix.empty()) return "";
        }
    }
    
    return prefix;
}
```

## 40. Longest substring without repeating chars
```cpp
#include <bits/stdc++.h>
using namespace std;

int lengthOfLongestSubstring(string s) {
    unordered_set<char> seen;
    int left = 0, maxLen = 0;
    
    for (int right = 0; right < s.length(); right++) {
        while (seen.count(s[right])) {
            seen.erase(s[left]);
            left++;
        }
        seen.insert(s[right]);
        maxLen = max(maxLen, right - left + 1);
    }
    
    return maxLen;
}
```
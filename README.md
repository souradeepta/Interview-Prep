# Interview Prep

> This repo is to help you with popular coding interview questions.

## Usage

Click on the links below to view the questions and their answers.

**Table of Contents**


   * [C++](#C++)
      * [1 Strings](##-1-Strings)\
            - [1.1 Parenthesis Checker](###-1.1-Parenthesis-Checker)\
            - [1.2 Longest Palindrome](###-1.2-Longest-Palindrome)   
      * [2 Linked Lists](#2-cpp-lists)
      * [3 Trees](#3-cpp-trees)

    * [Python](#Python)
        * [1 Strings](##-1-Strings-py)\
            - [1.1 Parenthesis Checker](###-1.1-Parenthesis-Checker-py)\
            - [1.2 Longest Palindrome](###-1.2-Longest-Palindrome-py)   
      * [2 Linked Lists](#2-lists-py)
      * [3 Trees](#3-trees-py)
    


# C++

## 1 Strings

We shall look at string manipulation questions here.

***	
### 1.1 Parenthesis Checker 
Given an expression string **exp**. Examine whether the pairs and the orders of “{“,”}”,”(“,”)”,”[“,”]” are correct in exp.
For example, the program should print 'balanced' for exp = “[()]{}{[()()]()}” and 'not balanced' for exp = “[(])”

**Input:**
The first line of input contains an integer T denoting the number of test cases.  Each test case consists of a string of expression, in a separate line.

**Output:**
Print 'balanced' without quotes if the pair of parenthesis is balanced else print 'not balanced' in a separate line.

**Constraints:**\
1 ≤ T ≤ 100\
1 ≤ |s| ≤ 105

**Example:**\
**Input:**
```code
3
{([])}
()
([]
```

**Output:**
```code
balanced
balanced
not balanced
```
**Solution:**
```cpp
#include<bits/stdc++.h>
using namespace std;
int check(char c[])
{
    stack<char>s;
    for(int i=0;c[i]!='\0';i++)
    {
        if(c[i]=='(' || c[i]=='{' || c[i]=='[')
            s.push(c[i]);
        if(c[i]==')' || c[i]=='}' || c[i]==']')
        {
            if(s.empty()==true)
                return 0;
        else if(c[i]==')' && s.top()=='(')
            s.pop();
        else if(c[i]=='}' && s.top()=='{')
            s.pop();
        else if(c[i]==']' && s.top()=='[')
            s.pop();
        else
            return 0;
    }
}
}
int main()
{
    int t;
    char c[101];
    cin>>t;
    while(t--)
    {
        cin>>c;
        if(check(c))
            cout<<"balanced"<<endl;
        else
            cout<<"not balanced"<<endl;
    }
}
```
***	
### 1.2 Longest Palindrome
Given a string S, find the longest palindromic substring in S. **Substring of string S:** S[ i . . . . j ] where 0 ≤ i ≤ j < len(S). **Palindrome string:** A string which reads the same backwards. More formally, S is palindrome if reverse(S) = S. **Incase of conflict**, return the substring which occurs first ( with the least starting index ).

**NOTE:** Required Time Complexity **O(n<sup>2</sup>).**

**Input:**\
The first line of input consists number of the testcases. The following **T** lines consist of a string each.

**Output:**\
In each separate line print the longest palindrome of the string given in the respective test case.

**Constraints:**\
1 ≤ T ≤ 100
1 ≤ Str Length ≤ 104

**Example:**\
**Input:**
```code
1
aaaabbaa
```
**Output:**
```code
aabbaa
```
**Solution:**
```cpp
```

***
<!-- Python  segment begins here-->
# Python

## 1 Strings

We shall look at string manipulation questions here.

***	
### 1.1 Parenthesis Checker 
Given an expression string **exp**. Examine whether the pairs and the orders of “{“,”}”,”(“,”)”,”[“,”]” are correct in exp.
For example, the program should print 'balanced' for exp = “[()]{}{[()()]()}” and 'not balanced' for exp = “[(])”

**Input:**
The first line of input contains an integer T denoting the number of test cases.  Each test case consists of a string of expression, in a separate line.

**Output:**
Print 'balanced' without quotes if the pair of parenthesis is balanced else print 'not balanced' in a separate line.

**Constraints:**\
1 ≤ T ≤ 100\
1 ≤ |s| ≤ 105

**Example:**\
**Input:**
```code
3
{([])}
()
([]
```

**Output:**
```code
balanced
balanced
not balanced
```
**Solution:**
```python
open_list = ["[","{","("] 
close_list = ["]","}",")"] 
  
# Function to check parentheses 
def check(myStr): 
    stack = [] 
    for i in myStr: 
        if i in open_list: 
            stack.append(i) 
        elif i in close_list: 
            pos = close_list.index(i) 
            if ((len(stack) > 0) and
                (open_list[pos] == stack[len(stack)-1])): 
                stack.pop() 
            else: 
                return "Unbalanced"
    if len(stack) == 0: 
        return "Balanced"
  
# Driver code 
string = "{[]{()}}"
print(string,"-", check(string)) 
  
string = "[{}{})(]"
print(string,"-", check(string)) 
```
***	
### 1.2 Longest Palindrome
Given a string S, find the longest palindromic substring in S. **Substring of string S:** S[ i . . . . j ] where 0 ≤ i ≤ j < len(S). **Palindrome string:** A string which reads the same backwards. More formally, S is palindrome if reverse(S) = S. **Incase of conflict**, return the substring which occurs first ( with the least starting index ).

**NOTE:** Required Time Complexity **O(n<sup>2</sup>).**

**Input:**\
The first line of input consists number of the testcases. The following **T** lines consist of a string each.

**Output:**\
In each separate line print the longest palindrome of the string given in the respective test case.

**Constraints:**\
1 ≤ T ≤ 100
1 ≤ Str Length ≤ 104

**Example:**\
**Input:**
```code
1
aaaabbaa
```
**Output:**
```code
aabbaa
```
**Solution:**
```cpp
```

***
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
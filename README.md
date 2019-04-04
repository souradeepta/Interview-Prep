# Interview Prep

> This repo is to help you with popular coding interview questions.

## Usage

Click on the links below to view the questions and their answers.

**Table of Contents**


   * [C++](#C++)
      * [1 Strings](##-1-Strings)\
            - [1.1 Parenthesis Checker](###-1.1-Parenthesis-Checker)\
            - [1.2 Longest Palindrome](###-1.2-Longest-Palindrome)   
            - [1.3 Longest Common Substring](###-1.3-Longest-Common-Substring)  
      * [2 Linked Lists](#2-cpp-lists)
      * [3 Trees](#3-cpp-trees)

    * [Python](#Python)
        * [1 Strings](##-1-Strings-py)
            - [1.1 Parenthesis Checker](###-1.1-Parenthesis-Checker-py)
            - [1.2 Longest Palindrome](###-1.2-Longest-Palindrome-py)   
            - [1.3 Longest Common Substring](###-1.3-Longest-Common-Substring-py) 
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
include <stdio.h> 
#include <string.h> 
  
// A utility function to print a substring str[low..high] 
void printSubStr( char* str, int low, int high ) 
{ 
    for( int i = low; i <= high; ++i ) 
        printf("%c", str[i]); 
} 
  
// This function prints the longest palindrome substring 
// of str[]. 
// It also returns the length of the longest palindrome 
int longestPalSubstr( char *str ) 
{ 
    int n = strlen( str ); // get length of input string 
  
    // table[i][j] will be false if substring str[i..j] 
    // is not palindrome. 
    // Else table[i][j] will be true 
    bool table[n][n]; 
    memset(table, 0, sizeof(table)); 
  
    // All substrings of length 1 are palindromes 
    int maxLength = 1; 
    for (int i = 0; i < n; ++i) 
        table[i][i] = true; 
  
    // check for sub-string of length 2. 
    int start = 0; 
    for (int i = 0; i < n-1; ++i) 
    { 
        if (str[i] == str[i+1]) 
        { 
            table[i][i+1] = true; 
            start = i; 
            maxLength = 2; 
        } 
    } 
  
    // Check for lengths greater than 2. k is length 
    // of substring 
    for (int k = 3; k <= n; ++k) 
    { 
        // Fix the starting index 
        for (int i = 0; i < n-k+1 ; ++i) 
        { 
            // Get the ending index of substring from 
            // starting index i and length k 
            int j = i + k - 1; 
  
            // checking for sub-string from ith index to 
            // jth index iff str[i+1] to str[j-1] is a 
            // palindrome 
            if (table[i+1][j-1] && str[i] == str[j]) 
            { 
                table[i][j] = true; 
  
                if (k > maxLength) 
                { 
                    start = i; 
                    maxLength = k; 
                } 
            } 
        } 
    } 
  
    printf("Longest palindrome substring is: "); 
    printSubStr( str, start, start + maxLength - 1 ); 
  
    return maxLength; // return length of LPS 
} 
  
// Driver program to test above functions 
int main() 
{ 
    char str[] = "bestabbaband"; 
    printf("\nLength is: %d\n", longestPalSubstr( str ) ); 
    return 0; 
}
```

***
<!-- Python  segment begins here-->
### 1.3 Longest Common Substring
Given two strings ‘X’ and ‘Y’, find the length of the longest common substring.

**Example:**\
**Input:**
```code
X = "Men4Men", y = "Mentor"
```
**Output:**
```code
3
The longest common substring is "Men" and is of
length 3
```
**Solution:**
```cpp
/* Dynamic Programming solution to find length of the  
   longest common substring */
#include<iostream> 
#include<string.h> 
using namespace std; 
  
// A utility function to find maximum of two integers 
int max(int a, int b) 
{   return (a > b)? a : b; } 
  
/* Returns length of longest common substring of X[0..m-1]  
   and Y[0..n-1] */
int LCSubStr(char *X, char *Y, int m, int n) 
{ 
    // Create a table to store lengths of longest common suffixes of 
    // substrings.   Notethat LCSuff[i][j] contains length of longest 
    // common suffix of X[0..i-1] and Y[0..j-1]. The first row and 
    // first column entries have no logical meaning, they are used only 
    // for simplicity of program 
    int LCSuff[m+1][n+1]; 
    int result = 0;  // To store length of the longest common substring 
  
    /* Following steps build LCSuff[m+1][n+1] in bottom up fashion. */
    for (int i=0; i<=m; i++) 
    { 
        for (int j=0; j<=n; j++) 
        { 
            if (i == 0 || j == 0) 
                LCSuff[i][j] = 0; 
  
            else if (X[i-1] == Y[j-1]) 
            { 
                LCSuff[i][j] = LCSuff[i-1][j-1] + 1; 
                result = max(result, LCSuff[i][j]); 
            } 
            else LCSuff[i][j] = 0; 
        } 
    } 
    return result; 
} 
  
/* Driver program to test above function */
int main() 
{ 
    char X[] = "OldSite:google.co.in"; 
    char Y[] = "NewSite:google.com"; 
  
    int m = strlen(X); 
    int n = strlen(Y); 
  
    cout << "Length of Longest Common Substring is " 
         << LCSubStr(X, Y, m, n); 
    return 0; 
} 
```

***
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
```python
# A O(n^2) time and O(1) space program to find the  
#longest palindromic substring 
  
# This function prints the longest palindrome substring (LPS) 
# of str[]. It also returns the length of the longest palindrome 
def longestPalSubstr(string): 
    maxLength = 1
  
    start = 0
    length = len(string) 
  
    low = 0
    high = 0
  
    # One by one consider every character as center point of  
    # even and length palindromes 
    for i in xrange(1, length): 
        # Find the longest even length palindrome with center 
    # points as i-1 and i. 
        low = i - 1
        high = i 
        while low >= 0 and high < length and string[low] == string[high]: 
            if high - low + 1 > maxLength: 
                start = low 
                maxLength = high - low + 1
            low -= 1
            high += 1
  
        # Find the longest odd length palindrome with center  
        # point as i 
        low = i - 1
        high = i + 1
        while low >= 0 and high < length and string[low] == string[high]: 
            if high - low + 1 > maxLength: 
                start = low 
                maxLength = high - low + 1
            low -= 1
            high += 1
  
    print "Longest palindrome substring is:", 
    print string[start:start + maxLength] 
  
    return maxLength 
  
# Driver program to test above functions 
string = "forgeeksskeegfor"
print "Length is: " + str(longestPalSubstr(string)) 

```

***
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
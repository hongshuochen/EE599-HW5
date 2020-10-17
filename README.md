
# HW5 EE599 - Computing Principles for Electrical Engineers

- Please clone the repository, edit [README.md](README.md) to answer the questions, and fill up functions to finish the hw.
- For non-coding quesitions, you will find **Answer** below each question. Please write your answer there.
- For coding questions, please make sure that your code can run ```bazel run/test```. In this homework, you will need to fill up [cpplib.cc](src/lib/cpplib.cc) and tests in [tests](tests).
- For submission, please push your answers to Github before the deadline.
- Deadline: Monday, September 21st by 23:59 pm
- Total: 130 points. 100 points is considered full credit.

## Question 1 (50 Points. Medium)

Please implement the following class for MaxHeap:
- Provide Gtest for methods that are marked with "GT".
```c++
class MaxHeap {
 public:
  MaxHeap(); // default constructor

  int getParentIndex(int i); //GT
  int getLeftIndex(int i); //GT
  int getRightIndex(int i); //GT
  int getLargestChildIndex(int i); //GT

  int getLeft(int i);
  int getRight(int i);
  int getParent(int i);

  int top(); //GT
  void push(int v); //GT
  void pop(); //GT
  void TrickleUp(int i);
  void TrickleDown(int i);

 private:
  vector<int> data_;
};
```

Write several tests using GTest for your function in [tests/q1_student_test.cc](tests/q1_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q1_student_test
```

## Question 2 (15 Points. Easy)

Write a function ```void heapSort(vector<int> &input)``` that uses heap-sort to sort a vector of integers.
- You should use std::priority_queue to implement your funciton.
- Provide time complexity for the function.

Example :
input: [5, 9, 3, 1, 7]
After calling the method, input changes to [1, 3, 5, 7, 9]

Write several tests using GTest for your function in [tests/q2_student_test.cc](tests/q2_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q2_student_test
```

## Question 3 (15 Points. Easy)

Write a function ```int findKthLargest(const vector<int> &input, int k)``` that finds the kth largest element in an unsorted vector and returns that value.
- You should do this without sorting the vector
- You can assume the input vector does not have duplicate values
- Provide time complexity for the function.

Example:
input: [0, 2, 1, 5, 6, 3] and k = 2
output: 5

Write several tests using GTest for your function in [tests/q3student_test.cc](tests/q3_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q3_student_test
```

## Question 5 (15 Points. Easy)

- Write a function that takes a string as an input and **reverses** its value. The function has no output. It changes the value of the input parameter. Write a simple function ```void CPPLib::ReverseString(std::string &input)``` in [cpplib.cc](src/lib/cpplib.cc). *You are welcomed to call existing STL functions*.

  - Example: Input: “EE599”, Output: “995EE”, string is stricted to be alphanumeric.
  - You cannot use any new local variable of type *string or vector or array*, but you can create extra O(1) space, such as *int*. The reverse should happen **in place** (i.e. on the input string).

- Write a function that takes a vector as an input and **reverses** its value. Write a simple function ```std::vector<int> CPPLib::ReverseVector_1(std::vector<int> input)``` in [cpplib.cc](src/lib/cpplib.cc)

  - Example: Input: {1,2,3,4}, Output: {4,3,2,1}. 
  - Use of [stack](https://en.cppreference.com/w/cpp/container/stack) is needed.

- Write a function that converts a string to lower case. Write a simple function ```void CPPLib::ToLower(std::string& )``` in [cpplib.cc](src/lib/cpplib.cc). The input string is strictly alphanumeric.
  - Example: input: “EE599”, output: “ee599”
  - Use of [transform](http://www.cplusplus.com/reference/algorithm/transform/) is recommended but not a must.

For all of the three questions, write a test using GTest for your finction in [tests/q5_student_test.cc](tests/q5_student_test.cc).
```
bazel test tests:q5_student_test
```

## Question 6 (25 Points. Medium)

A palindrome is a word, phrase, or other sequences of characters that reads the same backward as forward, such as **madam**, **racecar**, or the number **10801**.

 Write a function ```bool canBePalindrome(const std::string &str)``` in [cpplib.cc](src/lib/cpplib.cc) that returns true if the permutation of the input could form a palindrome. and false if it is not.


Example:\
Input: str = "code".\
Output: false.\
Input: str = "aab".\
Output: true.

Write several tests using GTest for your function in [tests/q6_student_test.cc](tests/q6_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q6_student_test
```

## Question 7 (20 Points. Medium)

Write a function ```std::map<char, char> CPPLib::Mappable(const std::string& from, const std::string& to)``` in [cpplib.cc](src/lib/cpplib.cc).
Write a function that takes two strings from and to and determines if they are mappable.

- Two strings are mappable if the characters in from can be replaced to get to.
- You can assume characters are strictly lower cases.  
- Each character can only map to itself.
- The output should be a map:
  - Empty map if the mapping is not possible
  - The actual map if the mapping was possible

Example 1:
Input: from = "add", to = "egg”
Output: {(a->e), (d->g)}

Example 2:
Input: from = "extreme", to = "egg”
Output: { }

Example 3:
Input: from = "harder", to = "waiter”
Output: { }, because you cannot map 'r' to 'i' and 'r' at the same time!

Example 4:
Input: from = "aabbrr", to = "ddeekk”
Output: {(a->d),(b->e), (r->k)}

Further, write several tests using GTest for your function in [tests/q7_student_test.cc](tests/q7_student_test.cc) and compute the time complexity of your implementation.

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q7_student_test
```

## Question 8 (20 Points. Medium)

 Write a function ```void kthPeek(std::vector<int> &input, int k);``` in [cpplib.cc](src/lib/cpplib.cc) that

- Finds the kth smallest value of the vector, called target(the vector is not sorted)
- It then rearranges the vector in such a way that it will have all the values lower than the target on the left side in ascending order and all the greater than the target value on the right side in descending order.

Example:\
Input: {637, 231, 123, 69, 43, 900, 10, 7, 21, 99, 0, 500}, k = 6.\
Output: Output:{0, 7, 10, 21, 43, 69, 900, 637, 500, 231, 123, 99 }. (target = 69)

Write several tests using GTest for your function in [tests/q8_student_test.cc](tests/q8_student_test.cc).

Please create your test cases and run the following command to verify the functionality of your program.
```
bazel test tests:q8_student_test
```

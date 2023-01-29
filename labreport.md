# Part 1
* used the template Web Server code from week 2 lab and made some adjustments to fit the functionality for StringServer
* StringServer code:
<img width="572" alt="Screenshot_20230129_023559" src="https://user-images.githubusercontent.com/122491210/215359876-64da7444-ec38-441d-8f24-e8464a8dc450.png">

* examples of using `/add-message`:
1) StringServer after using the query '/add-message?s=Hello'
<img width="306" alt="Screenshot_20230129_023445" src="https://user-images.githubusercontent.com/122491210/215360089-0f5e501d-146e-4cad-8ed2-439784ce9a4d.png">

* calls the `handleRequest` method with the url as the parameter
* changes the value of `output` from `""` to `Hello`

2) StringServer after using the query '/add-message?s=How are you'
<img width="373" alt="Screenshot_20230129_023502" src="https://user-images.githubusercontent.com/122491210/215360118-cfd37591-bc84-4cf3-838a-1616b29053a8.png">

* calls the `handleRequest` method with the url as the parameter
* changes the value of `output` from `Hello` to `Hello\nHow are you`

# Part 2
* a failing JUnit test for `testReverseInPlace()` is:
```
int[] input2 = {1, 2, 3, 4, 5};
ArrayExamples.reverseInPlace(input2);
assertArrayEquals(new int[]{5, 4, 3, 2, 1}, input2);
```
* a successful JUnit test for `testReverseInPlace()` is:
```
int[] input1 = { 3 };
ArrayExamples.reverseInPlace(input1);
assertArrayEquals(new int[]{ 3 }, input1);
```
* running the JUnit tests results in:
<img width="653" alt="image" src="https://user-images.githubusercontent.com/122491210/215360886-c8fbe010-bb36-44d1-ac8f-7a19f64a74a6.png">

* the symptom is that the array is not reversed as expected
* the buggy code:
<img width="271" alt="image" src="https://user-images.githubusercontent.com/122491210/215360932-7a54c973-2c4f-44b0-9264-084147038097.png">

* the bug is that the loop condition `arr.length` made it so that each element in the array was swapped twice instead of just once
* to fix this issue, change the loop condition to `arr.length/2` so that each element in the array is swapped only once
* the fixed code:
<img width="296" alt="image" src="https://user-images.githubusercontent.com/122491210/215360972-5c1aa374-fdca-42db-9c67-41793133efb7.png">

# Part 3
Before the labs in week 2 and 3, I did not know how to create a web server using Java.
I was unfamiliar with using GitHub Desktop to upload and download code.
I also gained more experience using JUnit tests.

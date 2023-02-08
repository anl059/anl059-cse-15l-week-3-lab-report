# Part 1
* used the template Web Server code from week 2 lab and made some adjustments to fit the functionality for StringServer
* StringServer code:

```
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String output = "";

    public String handleRequest(URI url) {
        if(url.getPath().contains("/add-message")){
            String[] parameters = url.getQuery().split("=");
            output += "\n" + parameters[1];
        }
        return output;
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

* examples of using `/add-message`:
1) StringServer after using the query `/add-message?s=Hello`

<img width="306" alt="Screenshot_20230129_023445" src="https://user-images.githubusercontent.com/122491210/215360089-0f5e501d-146e-4cad-8ed2-439784ce9a4d.png">

* calls the `handleRequest` method with the url as the parameter
* calls the `getPath` method which gets the url as a String
* calls the `getQuery` method which gets the query part of the path as a String
* changes the value of `output` from `""` to `Hello`

2) StringServer after using the query  `/add-message?s=How are you`

<img width="373" alt="Screenshot_20230129_023502" src="https://user-images.githubusercontent.com/122491210/215360118-cfd37591-bc84-4cf3-838a-1616b29053a8.png">

* calls the `handleRequest` method with the url as the parameter
* calls the `getPath` method which gets the url as a String
* calls the `getQuery` method which gets the query part of the path as a String
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
1) successful test case:

<img width="317" alt="image" src="https://user-images.githubusercontent.com/122491210/217403156-d6de8253-e92c-423c-a141-602458fded23.png">

2) unsuccessful test case:

<img width="486" alt="image" src="https://user-images.githubusercontent.com/122491210/217403098-ea5e3c59-ba75-4966-931c-392e54cb7b1c.png">

* the symptom is that the array is not reversed as expected
* the buggy code:

```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
 ```

* the bug is that the loop condition `arr.length` made it so that each element in the array was visited twice, so the elements are swapped twice, which reverses twice, instead of only swapping once, which reverses once
* to fix this issue, change the loop condition to `arr.length/2` so that each element in the array is only visited once
* the fixed code:

```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length / 2; i += 1) {
      int temp = arr[i];
      arr[i] = arr[arr.length - i - 1];
      arr[arr.length - i - 1] = temp;
    }
  }
 ```

# Part 3
Before the labs in week 2 and 3, I did not know how to create a web server using Java.
I was unfamiliar with using GitHub Desktop to upload and download code.
I also gained more experience using JUnit tests.

# Lab Report 2 Writeup
## Part 1
Here's the code for my StringServer:
![Addcode](https://user-images.githubusercontent.com/70412955/215634533-c8d5b1d0-487f-4d11-a589-4090b6cc4fec.PNG)

As you can see, I repurposed the code from the wavelet code we forked from week 2 because it had everything I needed to make the server

Here's two examples of me adding words to the server:
![add1](https://user-images.githubusercontent.com/70412955/215634833-016db908-9ff3-4fbc-9893-943c821ddc31.PNG)

![add2](https://user-images.githubusercontent.com/70412955/215634843-1c770ac6-356e-4f4c-a8c7-b4c612848226.PNG)

There are no extra methods being called, just the handler everytime the page is loaded. The code looks through the arguments in the url and looks for `/add-message`
It then checks to see if parameter 0 is = s, and then adds the string in paramter 1 to an arraylist called "words." 
Wether a word is added or not, the handler then creates a string and concatenates every string inside "words" to that string in order to return everything it has so far.

Essentially, everytime a word is added and the page is loaded, the String "complete" changes from being an empty string to being everything inside the arraylist "words." the String "complete" also has to be reinitialized everytime the page is loaded so that the entirety of words isn't repeated in the complete string

## Part 2
A failure inducing input for the ArrayTests was
```
@Test
  public void testBugReverseInPlace() {
    int[] input1 = {3,5,4,8};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{8,4,5,3}, input1);
  }
```
Where the expected output was [8,4,5,3] but ended up giving [8,4,4,8] 

A test that did not produce a failure would be anything that happened to be a palindrome, like [3,4,4,3]
```
@Test
  public void testNoFailure() {
    int[] input1 = {5,6,6,5};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5,6,6,5}, input1);
  }
```
Here are the two outcomes of those tests:
![arrayTestNoFailure](https://user-images.githubusercontent.com/70412955/215639863-9f96e7c7-c488-4e7d-b48a-34cbd1af40dc.PNG)
![arrayTestFail](https://user-images.githubusercontent.com/70412955/215639878-a9ec44aa-1a24-4c62-adb2-cd06d2ccd854.PNG)

As you can see, the palindrome suceeds but the other input doesn't

The a solution to this is as follows (although this solution is pretty bad)

Before:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```

After:
```
static void reverseInPlace(int[] arr) {
  int[] arr2 = new int[arr.length];
  for(int i = 0; i < arr.length; i += 1) {
    arr2[i] = arr[i];
  }
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr2[arr2.length - i - 1];
  }
}
```


## Part 3
So far, weeks 2 and 3 have taught me a lot about servers. Its honestly really cool that I can just run one from my own computer. While testing for failure and making multiple tests with different values wasn't anything new, I learned how to use the console commands better, and I now have a better grasp over how to operate the terminal. This class is honestly pretty fun.

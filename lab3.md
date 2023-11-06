# Lab Report 3: Bugs and Commands

## Part 1: Bugs

Failure-inducing input:  
Associated code:  
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
JUnit Test:  
```
@Test
public void testReverseInPlaceFail() {
  int[] input1 = { 3, 0};
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 0, 3 }, input1);
}
```

Passing input:
Associated code:  
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
JUnit Test:  
```
@Test
public void testReverseInPlace() {
  int[] input1 = { 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[]{ 3 }, input1);
}
```

Symptom of bug:
![Image](./report3/symptom.png)  

Fixing the bug:  
Bug before:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length; i += 1) {
    arr[i] = arr[arr.length - i - 1];
  }
}
```
Bug after:
```
static void reverseInPlace(int[] arr) {
  for(int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];
    arr[i] = arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```

In order to fix this bug, we only need to traverse through half the array, since we're essentially starting from the left and right edges and working inwards. By the time the  
index reaches the middle of the array, we would've reversed the entire array. Additionally, we need a temporary variable to the value at the index. After we update  
the value at the left index, we can update the right index with this temporary variable.

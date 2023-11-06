
Lab report 3.


Bug before code change: it reverses the order of items in the array until after the halfway point where it begins reversing everything back to the original order.
```
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length; i += 1) {
    int temp = arr[i];
    arr[i]= arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```



Failure-inducing input in the buggy program:
```
public void testReverseInPlace() {
int[] input1 = {1,2,3,4,5};
ArrayExamples.reverseInPlace(input1);
assertArrayEquals(new int[]{5,4,3,2,1}, input1);
}
```




Input that does not induce a failure as a JUnit test:
```
@Test
public void testReverseInPlace() {
int[] input1 = {1,2,3,4,5}
ArrayExamples.reverseInPlace(input1);
assertArrayEquals(new int[]{5,4,3,2,1}, input1);
}
```

Symptom as the output of running the tests:

![image](https://github.com/Malakelis/cse15l-lab-reports/assets/63074465/9bdaf18a-81ad-449e-97d2-6eb557bf9e8e)

Code after bug fix: This fixes the code because instead of iterating through all of the elements and reversing the array twice and changing it back to the original array, it will now stop after about the halfway point where it has already reversed the array because if it goes further it will start reversing back to the original order.
```
static void reverseInPlace(int[] arr) {
  for (int i = 0; i < arr.length/2; i += 1) {
    int temp = arr[i];j
    arr[i]= arr[arr.length - i - 1];
    arr[arr.length - i - 1] = temp;
  }
}
```


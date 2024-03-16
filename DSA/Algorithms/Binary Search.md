Search algorithm that finds the position of a target value within a sorted array.
Half of the array is eliminated during each step.

the runtime complexity is O(log n).

```java
private static int binarySearch(int[] array, int target) {

int low = 0;

int high = array.length - 1;

while(low <= high) {

int middle = low + (high - low) / 2;

int value = array[middle];

System.out.println("Middle: " + middle);

if(value < target) low = middle + 1;

else if(value > target) high = middle -1;

else return middle;

}

return -1;

}
```
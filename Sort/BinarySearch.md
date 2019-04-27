```java
public class BinarySearch {
	public static void main(String[] args) {
		int[] a = {1, 3, 4, 5, 8, 9, 10};
		int index = binarySearch(a, 3);
		System.out.printf("The index of the given number is %d", index);
	}

	public static int binarySearch(int[] a, int val) {
		int left = 0;
		int right = a.length - 1;

		while (left <= right) {
			int mid = (left + right) >> 1;

			if (a[mid] < val) {
				left = mid + 1;
			}else if (a[mid] > val) {
				right = mid - 1;
			}else return mid;
		}

		return -1;

	}
}
```

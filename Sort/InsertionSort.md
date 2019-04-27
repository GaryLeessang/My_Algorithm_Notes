```java
import java.util.*;

public class InsertionSort{
	public static void main(String[] args) {
		int[] a = {1, 3, 2, 7, 4};
		System.out.println("排序前的数组: " + Arrays.toString(a));
	
		insertionSort2(a);
		// insertionSort2(a);
		// Arrays.sort(a);
		//Collection.sort is for List.
		// Collections.sort(a);

		System.out.println("排序后的数组: " + Arrays.toString(a));
	}

	public static void insertionSort1(int[] a) {
		for (int i = 1; i < a.length; i++) {
			for (int j = i; j > 0 && a[j] < a[j-1]; j--) {
					int temp = a[j];
					a[j] = a[j-1];
					a[j-1] = temp;
			}
		}
	}

	// improved version of insertion sort
	public static void insertionSort2(int[] a) {
		for (int i = 1; i < a.length; i++) {
			int temp = a[i];
			int j = i;

			while (j > 0 && temp < a[j-1]) {
				a[j] = a[j-1];
				j--;
			}

			a[j] = temp;
		}
	}
}
```

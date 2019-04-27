```java
import java.util.Arrays;

public class MergeSort{
	public static void main(String[] args) {
		// int[] a = {1, 4, 7, 8, 3, 6, 9};
		int[] a = {5, 3, 6, 8, 1, 7, 9, 4, 2, 10};
		mergeSort(a, 0, a.length - 1);
		System.out.println(Arrays.toString(a));
	}

	public static void mergeSort(int[] a, int left, int right) {
		if (left >= right) return;
		int mid = left + ((right - left) >> 1);
		mergeSort(a, left, mid);
		mergeSort(a, mid + 1, right);
		merge(a, left, mid + 1, right);
	}

	public static void merge(int[] a, int leftPtr, int rightPtr, int rightBound) {
		int mid = rightPtr - 1;
		int[] temp = new int[rightBound - leftPtr + 1];
		int i = leftPtr;
		int j = rightPtr;
		int k = 0;

		while (i <= mid && j <= rightBound) {
			temp[k++] = a[i] <= a[j] ? a[i++] : a[j++];
		} 

		while (i <= mid) temp[k++] = a[i++];
		while (j <= rightBound) temp[k++] = a[j++];

		System.arraycopy(temp, 0, a, leftPtr, temp.length);

		} 
}
```

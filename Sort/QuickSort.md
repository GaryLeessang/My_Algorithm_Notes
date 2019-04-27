```java
import java.util.Arrays;

public class QuickSort{
	public static void main(String[] args) {
		int[] a = {7, 3, 2, 6, 8, 1, 9, 5, 4, 10};
		// int[] a = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
		long start1 = System.currentTimeMillis();
		quickSort(a, 0, a.length - 1);
		System.out.println(Arrays.toString(a));
		long end1 = System.currentTimeMillis();
		System.out.println("The original version costs: " + (end1 - start1) + " ms");

		long start2 = System.currentTimeMillis();
		improvedQuickSort(a, 0, a.length - 1);
		System.out.println(Arrays.toString(a));
		long end2 = System.currentTimeMillis();
		System.out.println("The improved version costs: " + (end2 - start2) + " ms");
	}

	public static void quickSort(int[] a, int lowBound, int highBound) {
		if (lowBound >= highBound) return;
		int pivotPos = partition(a, lowBound, highBound);
		quickSort(a, lowBound, pivotPos - 1);
		quickSort(a, pivotPos + 1, highBound);
	}

	public static int partition(int[] a, int lowBound, int highBound) {
		int left = lowBound;
		int right = highBound - 1;
		int pivot = a[highBound];

		while (left <= right) {
			while (left <= right && a[left] <= pivot) left++;
			while (left <= right && a[right] > pivot) right--;

			if (left < right) {
				swap(a, left, right);
			}
		}

		swap(a, left, highBound);

		return left;
	}

	// improved quick sort
	public static void improvedQuickSort(int[] a, int lowBound, int highBound) {
		if (lowBound >= highBound) return;
		int pivotPos = improvedPartition(a, lowBound, highBound);
		improvedQuickSort(a, lowBound, pivotPos - 1);
		improvedQuickSort(a, pivotPos + 1, highBound);
	}
	
	public static int improvedPartition(int[] a, int lowBound, int highBound) {
		int left = lowBound;
		int right = highBound - 2;
		int pivot = medianOf3(a, lowBound, highBound);

		while (left <= right) {
			while (left <= right && a[left] <= pivot) left++;
			while (left <= right && a[right] > pivot) right--;

			if (left < right) {
				swap(a, left, right);
			}
		}

		swap(a, left, highBound-1);

		return left;
	}
 
 	public static int medianOf3(int[] a, int low, int high) {
 		int mid = (low + high) / 2;

 		if (a[low] > a[high]) swap(a, low, high);
 		if (a[low] > a[mid]) swap(a, low, mid);
 		if (a[mid] > a[high]) swap(a, mid, high);

 		swap(a, mid, high-1);
 		return a[high-1];
 	}

 	public static void swap(int[] a, int i, int j) {
 		int temp = a[i];
 		a[i] = a[j];
 		a[j] = temp;
 	}
}
```

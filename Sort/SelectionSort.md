```java
import java.util.Arrays;

public class SelectionSort{
	public static void main(String[] args) {
		int[] arr = {3, 5, 1, 9, 6, 2, 7};
		selectionSort(arr);
		System.out.println(Arrays.toString(arr));
	}

	public static void selectionSort(int[] arr){
		for(int i=0; i<arr.length-1; i++){
			int minPos = i;

			for(int j=i+1; j<arr.length; j++){

				if(arr[minPos] > arr[j]){
					minPos = j;
				}
			}

			int temp = arr[i];
			arr[i] = arr[minPos];
			arr[minPos] = temp;
			
			// swap(arr, i, minPos);
			// System.out.printf("经过第 %d 次排序的数组：", i);
			// for(int n : arr){
			// 	System.out.print(n + " ");
			// }
		}
	}

	// static void swap(int[] a, int i, int j){
	// 	int temp = a[i];
	// 	a[i] = a[j];
	// 	a[j] = temp;
	// }
}
```

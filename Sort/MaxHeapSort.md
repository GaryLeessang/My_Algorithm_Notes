```java
import java.util.Arrays;

public class MaxHeapSort {
    public static void main(String[] args) {
        int[] test = {8, 6, 4, 5, 3, 7, 1};
        sort(test);
        System.out.println(Arrays.toString(test));
    }

    // Use the max heap to sort the array in ascending order
    public static void sort(int[] arr) {
        for (int i = (arr.length >> 1) - 1; i >= 0; i--) {
            adjustHeap(arr, i, arr.length);
        }

        for (int i = arr.length - 1; i > 0; i--) {
            swap(arr, 0, i);
            adjustHeap(arr, 0, i);
        }
    }

    //这里传入length参数很重要，否则在sort函数中length将为固定值，无法完成排序任务
    public static void adjustHeap(int[] arr, int i, int length) {
        int temp = arr[i];
        for (int k = 2 * i + 1; k < length; k = 2 * k + 1) {
            if (k < length - 1 && arr[k] < arr[k + 1]) k++;
            if (temp < arr[k]) {
                arr[i] = arr[k];
                i = k;
            } else break;
        }
        arr[i] = temp;
    }

    public static void swap(int[] a, int i, int j) {
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }
}
```

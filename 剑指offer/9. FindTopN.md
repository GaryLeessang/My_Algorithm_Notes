## 10亿个文件，寻找前N大的数据
### 思路：
> 1. 使用快排分类思想，随机取轴后看分类后的数据是否为N。

  缺点：计算机若有内存限制，可能无法装下大文件

> 2. 鉴于1，尝试将数据写入两个文件分别读取。

缺点：增加了IO次数

> 3. 使用分布式思想，将数据进行切分，利用多台计算机同时并行计算前N大数据，然后将结果进行汇总分析

**如果只有一台计算机呢？**
> 此时可能利用堆排序，维护一个大小为N的小顶堆，后续数据比堆顶元素大则加入堆，否则跳过。  
  Time Complexity: O(N)

### 答案以及堆排序模版：
#### 答案：
```Java
public class FindTopN {
    public static void main(String[] args) {
        int[] arr = {3, 4, 2, 8, 10, 5};
        int n = 3;
        findTopN(arr, n);
        System.out.println(Arrays.toString(arr));
        System.out.println(Arrays.toString(Arrays.copyOf(arr, n)));

    }

    public static void minHeap(int[] arr, int k) {
        for (int i = (k >> 1) - 1; i >=0; i--) {
            adjustHeap(arr, i, k);
        }
    }

    public static void adjustHeap(int[] arr, int i, int length) {
        int temp = arr[i];
        for (int k = 2 * i + 1; k < length; k = 2 * k + 1) {
            if (k < length - 1 && arr[k] > arr[k + 1]) k++;
            if (temp > arr[k]) {
                arr[i] = arr[k];
                i = k;
            } else break;
        }
        arr[i] = temp;
    }

    public static void findTopN(int[] arr, int n) {
        minHeap(arr, n);
        for (int j = n; j < arr.length; j++) {
            if (arr[j] > arr[0]) {
                swap(arr, 0, j);
                adjustHeap(arr, 0, n);
            }
        }
    }

    public  static void swap(int[] a, int i, int j) {
        int temp = a[i];
        a[i] = a[j];
        a[j] = temp;
    }

}
```

#### 堆排序模版：
```java
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

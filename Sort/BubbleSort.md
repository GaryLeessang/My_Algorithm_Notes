```java
import java.util.Arrays;

public class BubbleSort{
	public static void main(String[] args) {
		int[] a = {1, 6, 5, 4, 7};
		// int[] a = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
		System.out.println("排序前的数组：" + Arrays.toString(a));

		bubbleSort(a);
		System.out.println("排序后的数组：" + Arrays.toString(a));
	}


	// 优化：引入flag变量检测第一遍扫描是否发生了交换，若没有则证明已经有序，直接返回.
	public static void bubbleSort(int[] a) {
		boolean flag = true;

		for (int i = a.length - 1; i > 0; i--) {
			for (int j = 0; j < i; j++) {
				// 这里不能把a[j] > a[j+1]提到for循环里，否则每次都固定比a[0]>a[1]导致
				// 循环永远不会开始，而插入排序中可以的原因是j是动态的.
				if (a[j] > a[j+1]) {
					int temp = a[j];
					a[j] = a[j+1];
					a[j+1] = temp;
					flag = false;
				}
			}
		}

		if (flag) return;
	}
}

```

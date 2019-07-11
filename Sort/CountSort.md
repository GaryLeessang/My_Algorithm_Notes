```java
import java.util.Arrays;


public class CountSort{

	// 计数排序适用于数量大但范围小的场景
	public static void main(String[] args) {
		int[] a = {100, 134, 123, 123, 146, 134, 125, 145, 123};
		int[] b = {1 ,2, 5, 2, 1, 2, 5, 6, 7, 2, 6, 8, 1, 9};
		int[] result = countSort(a);
		int[] improvedResult = improvedCountSort(b);
		System.out.println(Arrays.toString(result));
		System.out.println(Arrays.toString(improvedResult));
	}

	// 算法思想：先new出两个数组，一个大小为原数组取值范围长度--用来计数；
	// 一个为原数组的长度，用来最后依次从count数组中读取数值
	public static int[] countSort(int[] a) {
		int[] res = new int[a.length];
		int[] count = new int[50];

		for (int i = 0; i < a.length; i++) {
			// 这里减去100解决了index100以下空间浪费的问题
			count[a[i] - 100]++;
		}

		for (int i = 0, j = 0; i < count.length; i++) {
			while (count[i]-- > 0) res[j++] = i + 100;
		}

		return res;
 	}

 	// 改进：原算法缺点是不稳定，因此需要改进为累加数组来保持元素的相对位置
 	public static int[] improvedCountSort(int[] b) {
 		int[] res = new int[b.length];
 		int[] count = new int[10];

 		for (int i = 0; i < b.length; i++) {
 			count[b[i]]++;
 		}

 		for (int i = 1; i < count.length; i++) {
 			count[i] = count[i] + count[i-1];
 		}

 		for (int i = b.length - 1; i >= 0; i--) {
 			res[--count[b[i]]] = b[i];
 		}

 		return res;
 	}
}









```

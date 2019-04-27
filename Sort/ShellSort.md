```java
import java.util.Arrays;

public class ShellSort{
	public static void main(String[] args) {
		int[] a = {9, 6, 11, 3, 5, 12, 8, 7, 10, 15, 14, 4, 1, 13, 2};
		shellSort(a);
		System.out.println(Arrays.toString(a));
		int b = 8;
		System.out.println((b << 2) + " " + (b >> 3));
	}

	public static void shellSort(int[] a) {

		// Knuth algorithm to generate h;
		// h = 3 * h + 1
		int h = knuthH();
		for (int gap = h; gap > 0; gap = (gap - 1) / 3) {
			for (int i = gap; i < a.length; i++) {
				int j = i;
				int temp = a[i];

				while (j > gap - 1 && temp < a[j-gap]) {
					a[j] = a[j-gap];
					j -= gap;
				}

				a[j] = temp;
			}
		}
	}

	public static int knuthH() {
		int h = 1;
		while (h <= 20) {
			h = h*3 + 1;
		}

		return h;
	}
}
```

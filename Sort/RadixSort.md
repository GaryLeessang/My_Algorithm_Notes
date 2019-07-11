```java
import java.util.Arrays;

public class RadixSort{
	public static void main(String[] args) {
		int[] a = {421, 240, 115, 532, 305, 430, 124};
		int[] result = radixSort(a);
		System.out.println(Arrays.toString(result));
	}

	public static int[] radixSort(int[] a) {
		int[] result = new int[a.length];
		int[] count = new int[10];

		for (int m=0; m<3; m++) {
			int temp = (int) Math.pow(10, m);

			for (int j=0; j<a.length; j++) {
				int num = a[j] / temp % 10;
				count[num]++;
			} 

			for (int i=1; i<count.length; i++) {
				count[i] = count[i] + count[i-1];
			}

			for (int i=a.length - 1; i>=0; i--) {
				int num = a[i] / temp % 10;
				result[--count[num]] = a[i];
			}

			System.arraycopy(result, 0, a, 0, a.length);
			Arrays.fill(count, 0);
		}

		return result;
	}
}
```

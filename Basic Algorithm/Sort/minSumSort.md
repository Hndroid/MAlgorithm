### 求最小和

> 2018年10月31日 15:43:58

##### 題目描述

例如：1，2，4，5的最小和：1 + (1+2) + (1+2+4) = 11

##### 代码实现

	public static int mergeSort(int[] array, int L, int R) {
		if (L == R) {
			return 0;
		}

		int mid = L + ((R - L) >> 1);

		return mergeSort(array, L, mid) + mergeSort(array, mid + 1, R) + merge(array, L, mid, R);
	}

	private static int merge(int[] array, int L, int mid, int R) {
		int Ls = L;
		int Rs = mid + 1;
		int i = 0;
		int sum = 0;
		int[] help = new int[R - L + 1];
		while (Ls <= mid && Rs <= R) {
			sum += array[Ls] < array[Rs] ? (R - Rs + 1) * array[Ls] : 0;
			help[i++] = array[Ls] < array[Rs] ? array[Ls++] : array[Rs++];
		}

		while (Ls <= mid) {
			help[i++] = array[Ls++];
		}

		while (Rs <= R) {
			help[i++] = array[Rs++];
		}

		for (int j = 0; j < help.length; j++) {
			array[L + j] = help[j];
		}
		return sum;
	}
	
##### 时间复杂度

T(n) = O(n*logn)

##### 额外空间复杂度

S(n) = O(n)
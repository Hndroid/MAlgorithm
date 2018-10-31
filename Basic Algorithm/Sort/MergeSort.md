### 归并排序

> 2018年10月31日 15:43:58


	public static void mergeSort(int[] array, int L, int R) {
		if (L == R) {
			return;
		}

		int mid = L + ((R - L) >> 1);

		mergeSort(array, L, mid);
		mergeSort(array, mid + 1, R);
		merge(array, L, mid, R);
	}

	private static void merge(int[] array, int l, int mid, int r) {
		int Ls = l;
		int Rs = mid + 1;
		int i = 0;
		int[] help = new int[r - l + 1];

		while (Ls <= mid && Rs <= r) {
			help[i++] = array[Ls] <= array[Rs] ? array[Ls++] : array[Rs++];
		}

		while (Ls <= mid) {
			help[i++] = array[Ls++];
		}

		while (Rs <= r) {
			help[i++] = array[Rs++];
		}

		for (int j = 0; j < help.length; j++) {
			array[l + j] = help[j];
		}
	}

##### 时间复杂度

T(n) = O(n*logn)

##### 额外空间复杂度

S(n) = O(n)
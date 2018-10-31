### 插入排序

> 2018年10月31日 15:43:58

	public static void insertSort(int[] array) {

		for (int i = 0; i < array.length; i++) {
			for (int j = i - 1; j >= 0 && array[j] > array[j + 1]; j--) {

				array[j] = array[j] ^ array[j+1];
				array[j+1] = array[j] ^ array[j+1];
				array[j] = array[j] ^ array[j+1];
			}
		}
	}
	

##### 时间复杂度

T(n) = O(n^2)

##### 额外空间复杂度

S(n) = O(1)
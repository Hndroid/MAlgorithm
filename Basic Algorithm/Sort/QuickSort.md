### 经典快速排序

> 2018年11月 1日 22:06:13

##### 題目描述

	public static void quickSort(int[] array, int left, int right) {
			
		if (left >= right) {
			return;
		}
		
		int Ls = left;
		int Rs = right;
		int temp = array[left];
		
		while (Ls < Rs) {
			
			while (Ls < Rs && array[Rs] >= temp) {
				Rs--;
			}
			
			while (Ls < Rs && array[Ls] <= temp) {
				Ls++;
			}
			
			if (Ls < Rs) {
				array[Ls] = array[Ls] ^ array[Rs];
				array[Rs] = array[Ls] ^ array[Rs];
				array[Ls] = array[Ls] ^ array[Rs];
			}
		}
		
		array[left] = array[Ls];
		array[Ls] = temp;
		
		quickSort(array, left, Ls - 1);
		quickSort(array, Ls + 1, right);
	}

##### 代码实现

	
	
##### 时间复杂度



##### 额外空间复杂度

---

### 随机快速排序

> 2018年11月 2日 22:06:13

##### 題目描述

	

##### 代码实现

	public static void quickSort(int[] array, int left, int right) {
		if (left < right) {
			swap(array, left + ((int) (Math.random() * (right - left + 1))), right);
			int[] help = partition(array, left, right);
			quickSort(array, left, help[0]);
			quickSort(array, help[1] + 1, right);
		}
	}

	private static int[] partition(int[] array, int left, int right) {
		int Ls = left - 1;
		int Rs = right;
		while (left < Rs) {
			if (array[left] < array[right]) {
				swap(array, ++Ls, left++);
			} else if (array[left] > array[right]) {
				swap(array, --Rs, left);
			} else {
				left++;
			}
		}
		swap(array, Rs, right);
		return new int[] { Ls, Rs };
	}

	private static void swap(int[] array, int i, int j) {
		int temp = array[i];
		array[i] = array[j];
		array[j] = temp;
	}
	
##### 时间复杂度

数学期望时间复杂度 T(n) = T(n*logn)

##### 额外空间复杂度


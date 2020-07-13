# Algorithm 정리
---
## 1. 기본 알고리즘
* [정렬](#정렬)
>- [Bubble Sort](#bubble-sort)
>- [Counting Sort](#counting-sort)
>- [Insertion Sort](#insertion-sort)
>- [Selection Sort](#selection-sort)
>- [Merge Sort](#merge-sort)

* 정리를
---
## 2. JAVA 자료구조(알고리즘용)
* [Binary Search](#binary-search)
* [Disjoint-Set](#disjoint-set)
* 정리를
---
## 3. PYTHON 자료구조(알고리즘용)
* [뭐했더라?](#1day1commit)
* 일단은
* 정리를
---


### 정렬

>#### Bubble Sort
>서로 인접한 두 원소를 검사하여 정렬하는 알고리즘
```java
private static void sort(int[] number) {
		int size = number.length,temp=0;
		for(int i=size-1; i>0; --i) {
			boolean isSwap = false;
			for(int j=0; j<i; ++j) {
				if(number[j]>number[j+1]) {
					temp = number[j];
					number[j] = number[j+1];
					number[j+1] = temp;
					isSwap = true;
				}
			}
			System.out.println("sort : "+Arrays.toString(number));
			if(!isSwap) break;
		}
	}
```
>#### Counting Sort
>
```java
```

>#### Insertion Sort
>
```java
```

>#### Selection Sort
>
```java
```

>#### Merge Sort
>
```java
```

### Binary Search
> Arrays.binarySearch(배열, 값)을 사용한다.
> 찾는 값의 index를 반환하며 없는 경우 예상되는 위치의 -값을 반환한다.<반드시 정렬된 상태로 사용할 것!>
```java
	int[] values = {3,11,15,20,21,29};
	Arrays.sort(values);
	System.out.println(Arrays.toString(values));
	System.out.println(Arrays.binarySearch(values, 15));	//2반환
	System.out.println(Arrays.binarySearch(values, 20));	//3반환
	System.out.println(Arrays.binarySearch(values, 17));	//-4반환
```
		
### DisJoint-Set
```java
	private static int parents[];
	
	static void make() { // make set : 모든 원소를 개별적인 집합으로 생성
		Arrays.fill(parents, -1);
	}

	static int find(int a) {
		if(parents[a]<0) return a; // 자신이 루트이면 자신 리턴
		return parents[a] = find(parents[a]);
	}

	static boolean union(int a,int b) {
		int aRoot = find(a);
		int bRoot = find(b);
		if(aRoot == bRoot) return false;
		parents[bRoot] = aRoot;
		return true;
	}
```
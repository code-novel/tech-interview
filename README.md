# Algorithm 정리

---
## 1. 기본 알고리즘
* [정렬](#정렬)
	* [Bubble Sort](#bubble-sort)
	* [Counting Sort](#counting-sort)
	* [Insertion Sort](#insertion-sort)
	* [Selection Sort](#selection-sort)
	* [Merge Sort](#merge-sort)
	* [Quick Sort](#quick-sort)
* [재귀(Reculsive)](#재귀)
* [순열(Permutation)/조합(Combination)](#순열-조합)
	* [순열(Permutation)](#순열)
	* [조합(Combination)](#조합)
* [부분집합(SubSet)](#부분집합)
* [Memorization](#Memorization)
* [DP(Dynamic Programming)](#DP)
* [탐색](#탐색)
	* [이분탐색(Binary Search)](#이분탐색)
	* [DFS(깊이 우선 탐색)](#DFS)
	* [BFS(너비 우선 탐색)](#BFS)
* [욕심쟁이 알고리즘(Greedy)](#욕심쟁이-알고리즘)
* [백트래킹(Back Tracking)](#백트래킹)
* [서로소 집합(Disjoint-Set)](#서로소-집합)
* [그래프(Graph)](#그래프)
	* [최소신장트리(MST)](#MST)
		* [프림 알고리즘(Prim Algorithm)](#Prim)
		* [크루스칼 알고리즘(kruskal Algorithm)](#kruskal)
	* [다익스트라 알고리즘(Dijkstra Algorithm)](#Dijkstra)
* [문자열(String)](#문자열)
	* [KMP 알고리즘](#KMP-Algorithm)
	* [보이어-무어 알고리즘(Boyer-Moore Algorithm)](#Boyer-Moore-Algorithm)

---

## 2. 자료 구조
* [#스택(STACK)](#스택)
* [#큐(QUEUE)](#큐)
* [#리스트(LIST)](#리스트)
* [#트리(TREE)](#트리)

---

### 정렬

> #### Bubble Sort
> 서로 인접한 두 원소를 검사하여 정렬하는 알고리즘
> ```java
> private static void sort(int[] number) {
> 		int size = number.length,temp=0;
> 		for(int i=size-1; i>0; --i) {
> 			boolean isSwap = false;
> 			for(int j=0; j<i; ++j) {
> 				if(number[j]>number[j+1]) {
> 					temp = number[j];
> 					number[j] = number[j+1];
> 					number[j+1] = temp;
> 					isSwap = true;
> 				}
> 			}
> 			System.out.println("sort : "+Arrays.toString(number));
> 			if(!isSwap) break;
> 		}
> 	}
> ```

> #### Counting Sort
> 숫자가 나온 횟수를 구한 뒤, 그 숫자의 등장횟수의 누적 합을 구한다.  
> 그 뒤 원래 배열의 뒤에서 부터 순회하면서 누적 합을 이용해 그 숫자의 자리를 찾아 넣는다.  
> 단, Couting Sort의 경우에는 각 숫자의 등장횟수를 기록하기 때문에 그 숫자의 범위가 한정적이지 않을 경우(ex. 1 10 100000000 3 2 5와 같은 배열) 메모리 공간을 낭비하게 되는 경우가 발생할 수 있다.
> ```java
> import java.util.Arrays;
> import java.util.Scanner;
> 
> public class CountingSort {
> 
> 	public static void main(String[] args) {
> 
> 		Scanner sc = new Scanner(System.in);
> 		int N = sc.nextInt();
> 		int[] number = new int[N];
> 		int[] result = new int[N];
> 		int[] count = new int[10];
> 		
> 		//1.count 세기
> 		for(int i=0; i<N; ++i) {
> 			number[i] = sc.nextInt();
> 			count[number[i]]++;
> 		}
> 		
> 		//2.누적 count로 변경
> 		for(int i=1;i<10; ++i) {
> 			count[i] = count[i-1]+count[i];
> 		}
> 		//3. 입력받은 원소들 누적 count이용해서 자기자리 찾아 넣기
> 		for(int i=N-1; i>=0; --i) {
> 			result[count[number[i]]-1] = number[i];
> 			count[number[i]]--;
> 		}
> 		System.out.println(Arrays.toString(number));
> 		System.out.println(Arrays.toString(result));
> 	}
> 
> }
> ```

> #### Insertion Sort
> 현재 위치에서, 그 이하의 배열들을 비교하여 자신이 들어갈 위치를 찾아, 그 위치에 삽입하는 알고리즘
> ```java
> public static void insertionSort(int list[]) {
> 	final int SIZE = list.length;
> 	for (int i = 1; i < SIZE; ++i) { // 정렬되지 않은 집합 
> 		int temp = list[i]; // 정렬되야하는 원소
> 		for (int j = 0; j < i; ++j) { // 정렬된 집합
> 			if(temp<list[j]) { //삽입지점을 찾았다면
> 				for (int k = i-1; k >= j; --k) { // 정렬된 집합의 맨 뒤부터 삽입지점까지 뒤로 민다.
> 					list[k+1] = list[k];
> 				}
> 				list[j] = temp; // 삽입지점에 원소 넣기
> 				break;
> 			}
> 		}	
> 	}	
> }
> ```

> #### Selection Sort
> 현재 위치에 들어갈 값을 찾아 정렬하는 알고리즘
> ```java
> public void selectionSort(int[] data){
>     int size = data.length;
>     int min; //최소값을 가진 데이터의 인덱스 저장 변수
>     int temp;
>     for(int i=0; i<size-1; i++){ // size-1 : 마지막 요소는 자연스럽게 정렬됨
>         min = i;
>         for(int j=i+1; j<size; j++){
>             if(data[min] > data[j]){
>                 min = j;
>             }
>         }
>         temp = data[min];
>         data[min] = data[i];
>         data[i] = temp;
>     }
> }
> ```

> #### Merge Sort
> 하나의 원소 집합을 두 개의 균등한 크기로 분할하고 분할된 부분 집합을 정렬한 다음, 두 개의 정렬된 부분 집합을 합하여 전체가 정렬된 리스트로 합쳐서 정렬하는 알고리즘
> ```java
> // 병합을 하기 위한 method
> private static void merge(int[] list, int start, int middle, int end) {
> 	int left=start , right=middle+1;
> 	int i=0; // 새롭게 채워질 배열의 인덱스
> 	int[] newArr = new int[end-start+1];
> 	do {
> 		if (list[left] < list[right]) {
> 			newArr[i++] = list[left++];
> 		} else {
> 			newArr[i++] = list[right++];
> 		} 
> 	} while (left<=middle && right<=end);
> 	// 오른쪽집합이 다 처리된경우:남은 왼쪽집합 처리
> 	while(left<=middle) newArr[i++] = list[left++]; 
> 	// 왼쪽집합이 다 처리된경우:남은 오른쪽집합 처리
> 	while(right<=end) newArr[i++] = list[right++]; 
> 	System.arraycopy(newArr, 0, list, start, newArr.length);
> }
> //Merge Sort Code
> public static void mergeSort(int list[], int start, int end) {
> 	if(start == end) return; // 집합의 크기가 1이므로 분할불가(이미 정렬완료)
> 	int middle = (start+end)/2;
> 	mergeSort(list, start, middle); // 중간위치값 왼쪽집합에 포함
> 	mergeSort(list, middle+1, end); 
> 	merge(list,start,middle,end);
> }
> ```

> #### Quick Sort
> pivot과 two pointer를 활용하여 pivot을 기준으로 작은 값은 왼쪽으로 큰 값은 오른쪽으로 보내 정렬하는 방식.
> ```java
> public static void quickSort(int[] list,int begin,int end) {
> // 분류하여 피봇위치 확정(피봇의 자기자기 찾기)
> 	if(begin<end) { // 집합의 크기가 2이상
> 		int p = fixPivot(list,begin,end);
> 		// 확정된 피봇의 왼쪽집합 정렬
> 		quickSort(list, begin, p-1);
> 		// 확정된 피봇의 오른쪽집합 정렬
> 		quickSort(list, p+1, end);
> 	}
> }
> private static int fixPivot(int[] list, int begin, int end) {
> 	int pivot,left,right,temp;
> 	left = begin+1;
> 	right = end;
> 	pivot = begin;
> 
> 	do {
> 		while (left < end && list[left] < list[pivot]) left++;
> 		while (right > begin && list[right] >= list[pivot]) right--;
> 		if (left < right) {
> 			temp = list[left];
> 			list[left] = list[right];
> 			list[right] = temp;
> 		} 
> 	} while (left<right);
> 	
> 	temp = list[pivot];
> 	list[pivot] = list[right];
> 	list[right] = temp;
> 	
> 	return right;
> }
> ```

---
### 재귀
#### 재귀란?
> 자기 자신을 재참조하는 방법
#### 재귀 호출(Reculsive Call)
> 함수 내부에서 함수가 자기 자신을 또 다시 호출하는 행위  
> 대표적인 예로 피보나치 수, 하노이 탑이 있다.
> * 피보나치 수
> 	```Java
> 	public class Fibonacci {
> 		public static void main(String[] args) {
> 			int input = 8;
> 			for (int i = 1; i <= input; i++) {
> 				System.out.println(fibo(i));
> 			}
> 		}
> 	
> 		public static int fibo(int n) {
> 			if (n <= 1)
> 				return n;
> 			else 
> 	            return fibo(n-2) + fibo(n-1);
> 		}
> 	}
> 	```
> * 하노이의 탑
> 	```Java
> 	public class Hanoi {
> 	    public static void main (String [] args) {      
> 	            hanoi(3, 'A', 'B', 'C');
> 	    }
> 	
> 	    public static void hanoi(int i, char from, char mid, char to){
> 	        if(i==1){
> 	            System.out.println(i + "를 " + from + "에서 " + to + "로 옮깁니다.");
> 	        }else{
> 	            hanoi(i-1, from, to, mid);
> 	            System.out.println(i + "를 " + from + "에서 " + to + "로 옮깁니다.");
> 	            hanoi(i-1, mid, from, to);
> 	        }
> 		}
> 	}
> 	```
---

### 순열 조합
#### 순열
> N개 중에 R개를 뽑는 경우의 수(순서 있음)를 구하는 것  
> 중복을 허용하는 경우와 중복을 허용하지 않는 경우로 나눌 수 있다.  
> * Permutation 예제 코드 01
> 	```java
> 	// 1,2,3
> 	// 3자리수 순열
> 	// 3P3 = 3! = 6가지경우
> 	public static void main(String[] args) {
> 		int n = 3;
> 		for (int i = 1; i <= n; ++i) {// 첫째수 : 1,2,3 시도
> 			for (int j = 1; j <= n; ++j) { // 둘째수 : 1,2,3 시도
> 				if(i != j) { // 첫째 수와 둘째 수가 다르면
> 					for (int k = 1; k <= n; ++k) {// 세째수 : 1,2,3 시도
> 						if(i!=k && j!=k) System.out.println(i+" "+j+" "+k);
> 					}
> 				}
> 			}
> 		}
> 	}
> 	```
> 3개의 숫자 중 3개를 선택하는 경우 반복문이 3중으로 작성되게 된다.
> 이 과정을 줄이기 위해 재귀함수를 사용할 수 있다.  
> * Permutation 예제 코드 02
> 	```java
> 	private static void permutation(int index) {
> 		if(index == R) {
> 			totalCount++;
> 			System.out.println(Arrays.toString(numbers));
> 			return;
> 		}
> 		
> 		for (int i = 1; i <=N ; ++i) {
> 			if(!isSelected[i]) { // 해당수가 선택되지 않았다면
> 				numbers[index] = i;
> 				isSelected[i] = true; // 현재 선택한수 사용한 플래그 처리
> 				permutation(index+1);
> 				isSelected[i]= false;
> 			}
> 		}		
> 	}
> 	```
> 선택 여부를 비트 마스크(BitMask) 연산을 통해 체크할 수도 있다.  
> * Permutation 예제 코드 03
>	```java
>	private static void permutation(int index,int selected) {
>		if(index == R) {
>			totalCount++;
>			System.out.println(Arrays.toString	(numbers));
>			return;
>		}
>		for (int i = 1; i <=N ; ++i) {
>			if((selected & 1<<i)==0) { // 해당수가 	선택되지 않았다면
>				numbers[index] = i;				 
>				permutation(index+1,selected | 1<<i);/	/ 현재 선택한수 사용한 플래그 처리
>			}
>		}
>	}
>	```

#### 조합
> N개 중에 R개를 순서 없이 뽑는 경우의 수를 구하는 것  
> 배열을 처음부터 돌면서 현재 index를 선택한 경우와 선택하지 않은 경우로 나눠서 완전 탐색으로 구현하면 된다.
> 	```java
> 	private static void combination(int index,int count) {
> 		if(count==R) {
> 			System.out.println(Arrays.toString(numbers));
> 			return;
> 		}
> 		if(index<=N) {
> 			numbers[count] = index;
> 			combination(index+1,count+1); // 선택
> 			combination(index+1,count);	// 비선택
> 		}
> 	}
> 	```
---

### 부분집합
> 조합(Combination)과 유사함.  
> 부분집합(Subset)을 구하는 방법으로 index의 선택 여부를 기록하면서 재귀를 통해 구현.  
> ```java
> static boolean[] selected;
> private static void makeSubSet(int index) {
> 	if(index == N) {
> 		for (int s = 0; s < selected.length; s++) {
> 			System.out.print((selected[s]?numbers[s]:"X")+"\t");
> 		}
> 		System.out.println();
> 		return;
> 	}
> 	
> 	selected[index]=true;
> 	makeSubSet(index+1);
> 	selected[index]=false;
> 	makeSubSet(index+1);
> }
> ```
---

### Memorization
> Memory에 특정 정보를 기록해두고 필요할 때 마다 정보를 가져와서 활용하는 기법.  
> 이미 했던 연산을 반복할 필요가 없어서 시간을 줄일 수 있다.  
> Dynamic Programming([동적 계획법](#DP))의 핵심이 되는 기술이다.  
```java
```
---
### DP
---
### 탐색
#### 이분탐색
> Arrays.binarySearch(배열, 값)을 사용한다.
> 찾는 값의 index를 반환하며 없는 경우 예상되는 위치의 -값을 반환한다.<반드시 정렬된 상태로 사용할 것!>
> ```java
> 	int[] values = {3,11,15,20,21,29};
> 	Arrays.sort(values);
> 	System.out.println(Arrays.toString(values));
> 	System.out.println(Arrays.binarySearch(values, 15));	//2반환
> 	System.out.println(Arrays.binarySearch(values, 20));	//3반환
> 	System.out.println(Arrays.binarySearch(values, 17));	//-4반환
> ```
#### DFS
#### BFS
---
### 욕심쟁이 알고리즘
---
### 백트래킹
---
### 서로소 집합
> ```java
> 	private static int parents[];
> 	
> 	static void make() { // make set : 모든 원소를 개별적인 집합으로 생성
> 		Arrays.fill(parents, -1);
> 	}
> 
> 	static int find(int a) {
> 		if(parents[a]<0) return a; // 자신이 루트이면 자신 리턴
> 		return parents[a] = find(parents[a]);
> 	}
> 
> 	static boolean union(int a,int b) {
> 		int aRoot = find(a);
> 		int bRoot = find(b);
> 		if(aRoot == bRoot) return false;
> 		parents[bRoot] = aRoot;
> 		return true;
> 	}
> ```
---
### 그래프
#### MST
##### Prim
##### Kruskal
#### Dijkstra
---
### 문자열
#### KMP Algorithm
#### Boyer Moore Algorithm
---
# Algorithm 정리

---
## 1. 기본 알고리즘
* [정렬](#정렬)
>- [Bubble Sort](#bubble-sort)
>- [Counting Sort](#counting-sort)
>- [Insertion Sort](#insertion-sort)
>- [Selection Sort](#selection-sort)
>- [Merge Sort](#merge-sort)
>- [Quick Sort](#quick-sort)
* [재귀(Reculsive)](#재귀)
* [순열(Permutation)/조합(Combination)](#순열-조합)
>- [순열(Permutation)](#순열)
>- [조합(Combination)](#조합)
* [부분집합(SubSet)](#부분집합)
* [Memorization](#Memorization)
* [DP(Dynamic Programming)](#DP)
* [탐색](#탐색)
>- [이분탐색(Binary Search)](#이분탐색)
>- [DFS(깊이 우선 탐색)](#DFS)
>- [BFS(너비 우선 탐색)](#BFS)
* [욕심쟁이 알고리즘(Greedy)](#욕심쟁이-알고리즘)
* [백트래킹(Back Tracking)](#백트래킹)
* [서로소 집합(Disjoint-Set)](#서로소-집합)
* [그래프(Graph)](#그래프)
>- [프림 알고리즘(Prim Algorithm)](#Prim)
>- [다익스트라 알고리즘(Dijkstra Algorithm)](#Dijkstra)
>- [크루스칼 알고리즘(kruskal Algorithm)](#kruskal)
* [문자열(String)](#문자열)
>- [KMP 알고리즘](#KMP-Algorithm)
>- [보이어-무어 알고리즘(Boyer-Moore Algorithm)](#Boyer-Moore Algorithm)

---

## 2. 자료 구조
* [#스택(STACK)](#스택)
* [#큐(QUEUE)](#큐)
* [#리스트(LIST)](#리스트)
* [#트리(TREE)](#트리)

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

> #### Bubble Sort
> 서로 인접한 두 원소를 검사하여 정렬하는 알고리즘
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

> #### Counting Sort
>
```java
```

> #### Insertion Sort
> 현재 위치에서, 그 이하의 배열들을 비교하여 자신이 들어갈 위치를 찾아, 그 위치에 삽입하는 알고리즘
```java
```

> #### Selection Sort
> 현재 위치에 들어갈 값을 찾아 정렬하는 알고리즘
```java
```

> #### Merge Sort
> 하나의 원소 집합을 두 개의 균등한 크기로 분할하고 분할된 부분 집합을 정렬한 다음, 두 개의 정렬된 부분 집합을 합하여 전체가 정렬된 리스트로 합쳐서 정렬하는 알고리즘
```java
```

> #### Quick Sort
> QuickSort
```java
```

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

---

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
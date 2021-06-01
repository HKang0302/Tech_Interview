# Algorithm
수업 내용과 구글링 정보를 참고하여 작성하였습니다. 삽입한 그림은 현재는 모두 다른 웹사이트에서 불러왔으며 출처는 적지 않았으나 추후에 출처를 기입하거나 직접 그림을 올릴 예정입니다.

<details>
<summary>예상 문제 접기/펼치기</summary>
<div markdown="1">
1. Sort 설명<br>
&nbsp; &nbsp;1-1. 시간 복잡도<br>
&nbsp; &nbsp;1-2. 손코딩<br>
2. 다익스트라 설명<br>
&nbsp; &nbsp;1-1. 시간 복잡도<br>
&nbsp; &nbsp;1-2. 손코딩<br>
</div>
</details>
</br><br>

## 목차
[기본 알고리즘](#기본-알고리즘)<br>
[정렬](#정렬)<br>
[Shortest Path](#Shortest-Path)<br>
[Others](#Others)
</br><br>

## 기본 알고리즘
### Dynamic Programmin(DP)
복잡한 문제를 여러가지로 나누어 풀이 - 이미 했던 계산을 반복하여 풀이(Memoization)<br>
*같은 문제는 항상 정답이 같음*

### Greedy Algorithm
다음 단계를 고려하지 않고 현재 단계에서의 최상의 선택을 하는 것

## 정렬
### Selection Sort
array를 돌아 최소값을 맨 앞에 위치시키고 그 다음 최소값을 그 다음에 위치시키는 것을 반복하여 정렬
* 시간 복잡도: O(n^2)
* space complexity: O(1)

### Insertion Sort
해당 원소를 알맞은 위치에 삽입하기 위해 이미 정렬된 원소들과 swap하다가 적절한 위치에 도달 시 stop하고 이를 모든 원소가 정렬될 때까지 반복
* 시간 복잡도: best=`O(n)`, worst=`O(n^2)`
* space complexity: `O(1)`

### Bubble Sort
두 원소를 비교하고 조건에 해당되면 유지, 아니면 swap하는 것을 반복하여 마지막 원소 획득. 이를 원소의 개수만큼 반복하여 정렬
* 시간 복잡도: `O(n^2)`
* Space Complexity: `O(1)`

### Quick Sort
Divide and Conqure, Unstable sort 알고리즘 사용
* 시간 복잡도: best&avg=`O(log n)`, worst=`O(n^2)` (이미 오름차순/내림차순으로 정렬되어있는 경우)
* Space Complexity: `O(n)`
* **과정**
  1. random element(pivot) 선택
  2. 피벗 앞에는 작은 수의 집단, 뒤에는 큰 수의 집단 배열
  3. 피벗을 기준으로 둘로 나누고 피벗을 그 자리에 고정
  4. 분할된 배열에 대해 이 과정을 반복하고 둘로 나누었을 때 나누어진 집단의 크기가 모두 1이면 종료
    ```
    quickSort(arr[], low, high){
        if(low<high){
            pivot = random element in the array
            i=low+1
            for(l=low; l<high; l++){
                if(arr[l]<pivot){
                    i++
                    swap(&arr[i], &arr[l])
                }
            }
            swap(&arr[high],&arr[i+1])
            quickSort(arr, low, i)
            quickSort(arr, i+1, high)
        }
    }
    ```

### Merge Sort
Divide and Conqure, Stable 알고리즘 사용
* 시간 복잡도: `O(n log n)`
* Space Complexity: `O(n)`
* 과정
  1. array를 두 subset으로 divide하고 divide된 subset을 또 divide하는 것을 모든 분할된 array의 크기가 1일 때까지 반복
  2. 두개의 분할된 array를 merge시키면서 동시에 정렬
  3. 하나의 array로 merge가 되면 종료
    ```
    MergeSort(arr[], low, high){
        if(low<high){
            mid = low + (high-low)/2
            MergeSort(arr, low, mid)
            MergeSort(arr, mid+1, high)
    
            // Merging
            L = copy of left subset, R = copy of right subset
            l=r=0
            ind = left-1
            while(l<L.size() && r<R.size()){
                ind++
                if(L[l]<R[l]{
                    arr[ind] = L[l]
                    l++
                }
                else{
                    arr[ind] = R[r]
                    r++
                }
            }
            while(l<L.size()){
                ind++
                arr[ind] = L[l]
                l++
            }
            while(r<R.size()){
                ind++
                arr[ind] = R[r]
                r++
            }
        }
    }
    ```

### Heap Sort
Heapify를 통한 정렬
* 시간 복잡도: `O(n log n)`
* Space Complexity: `O(1)`
* 과정
  1. 주어진 array의 max heap 구성
  2. 루트 노드에 있는 값이 최대값이므로 위치될 곳과 array의 마지막 element와 swap
  3. n--
  4. Heapify를 통해 재정렬 후 반복하여 완성하기
    ```
    Heapify(arr[], n, i) {
	    largest = i, l = 2i + 1, r = 2i + 2
	    if(l<n && arr[largest]<arr[l]) largest = l
	    if(r<n && arr[largest]<arr[r]) largest = r
	    if(largest != i)
		    swap(arr[i], arr[largest])
		    Heapify(arr, n, largest)
    }

    HeapSort(arr[], n) {
	    Heapify the array(arr, n, i)
	    for (i = n / 2 - 1; i >= 0; i--) {
		    swap(arr[0], arr[n-1])
		    Heapify the array(arr, i, 0)
	    }
    }
    ```
[위로](#목차)
<br></br>

## Shortest Path
### DFS vs. BFS
* **DFS:** Stack을 사용하여 모든 경로를 탐색할 때 사용
* **BFS:** Queue를 사용하여 최단 거리 경로를 탐색할 때 사용

### Dijkstra Algorithm
*Similar to Prim Algorithm*<br>
노드와 각 노드로의 거리가 주어진 graph에서 사용. 특정 노드에서 시작하여 최단 거리 찾을 때 사용

* **Priority Queue** 사용
* 시간복잡도: `O(|E|log|V|)`
* Algorithm
    ```
    Dijkstra(Graph):
	    for each vertex v:
		    let Kv be false
		    let Pv be unknown
		    let Dv be INFINITY
	    let pq be an empty priority queue
	    pq.enqueue(start vertex)
	    while(pq is not empty):
		    vertex v = dequeue from pq
		    if Kv is false:
			    Kv = true
			    for each vertex w:v->w:
				    if(Dw>Dv+D(v,w)):
					    Dw = Dv + D(v,w)
					    Pw = v
				    enqueue w into pq with Dw
    ```
[위로](#목차)
<br></br>

## Others
[위로](#목차)
<br></br>
# Algorithm
���� ����� ���۸� ������ �����Ͽ� �ۼ��Ͽ����ϴ�. ������ �׸��� ����� ��� �ٸ� ������Ʈ���� �ҷ������� ��ó�� ���� �ʾ����� ���Ŀ� ��ó�� �����ϰų� ���� �׸��� �ø� �����Դϴ�.

<details>
<summary>���� ���� ����/��ġ��</summary>
<div markdown="1">
1. Sort ����<br>
&nbsp; &nbsp;1-1. �ð� ���⵵<br>
&nbsp; &nbsp;1-2. ���ڵ�<br>
2. ���ͽ�Ʈ�� ����<br>
&nbsp; &nbsp;1-1. �ð� ���⵵<br>
&nbsp; &nbsp;1-2. ���ڵ�<br>
</div>
</details>
</br><br>

## ����
[�⺻ �˰���](#�⺻-�˰���)<br>
[����](#����)<br>
[Shortest Path](#Shortest-Path)<br>
[Others](#Others)
</br><br>

## �⺻ �˰���
### Dynamic Programmin(DP)
������ ������ ���������� ������ Ǯ�� - �̹� �ߴ� ����� �ݺ��Ͽ� Ǯ��(Memoization)<br>
*���� ������ �׻� ������ ����*

### Greedy Algorithm
���� �ܰ踦 ������� �ʰ� ���� �ܰ迡���� �ֻ��� ������ �ϴ� ��

## ����
### Selection Sort
array�� ���� �ּҰ��� �� �տ� ��ġ��Ű�� �� ���� �ּҰ��� �� ������ ��ġ��Ű�� ���� �ݺ��Ͽ� ����
* �ð� ���⵵: O(n^2)
* space complexity: O(1)

### Insertion Sort
�ش� ���Ҹ� �˸��� ��ġ�� �����ϱ� ���� �̹� ���ĵ� ���ҵ�� swap�ϴٰ� ������ ��ġ�� ���� �� stop�ϰ� �̸� ��� ���Ұ� ���ĵ� ������ �ݺ�
* �ð� ���⵵: best=`O(n)`, worst=`O(n^2)`
* space complexity: `O(1)`

### Bubble Sort
�� ���Ҹ� ���ϰ� ���ǿ� �ش�Ǹ� ����, �ƴϸ� swap�ϴ� ���� �ݺ��Ͽ� ������ ���� ȹ��. �̸� ������ ������ŭ �ݺ��Ͽ� ����
* �ð� ���⵵: `O(n^2)`
* Space Complexity: `O(1)`

### Quick Sort
Divide and Conqure, Unstable sort �˰��� ���
* �ð� ���⵵: best&avg=`O(log n)`, worst=`O(n^2)` (�̹� ��������/������������ ���ĵǾ��ִ� ���)
* Space Complexity: `O(n)`
* **����**
  1. random element(pivot) ����
  2. �ǹ� �տ��� ���� ���� ����, �ڿ��� ū ���� ���� �迭
  3. �ǹ��� �������� �ѷ� ������ �ǹ��� �� �ڸ��� ����
  4. ���ҵ� �迭�� ���� �� ������ �ݺ��ϰ� �ѷ� �������� �� �������� ������ ũ�Ⱑ ��� 1�̸� ����
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
Divide and Conqure, Stable �˰��� ���
* �ð� ���⵵: `O(n log n)`
* Space Complexity: `O(n)`
* ����
  1. array�� �� subset���� divide�ϰ� divide�� subset�� �� divide�ϴ� ���� ��� ���ҵ� array�� ũ�Ⱑ 1�� ������ �ݺ�
  2. �ΰ��� ���ҵ� array�� merge��Ű�鼭 ���ÿ� ����
  3. �ϳ��� array�� merge�� �Ǹ� ����
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
Heapify�� ���� ����
* �ð� ���⵵: `O(n log n)`
* Space Complexity: `O(1)`
* ����
  1. �־��� array�� max heap ����
  2. ��Ʈ ��忡 �ִ� ���� �ִ밪�̹Ƿ� ��ġ�� ���� array�� ������ element�� swap
  3. n--
  4. Heapify�� ���� ������ �� �ݺ��Ͽ� �ϼ��ϱ�
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
[����](#����)
<br></br>

## Shortest Path
### DFS vs. BFS
* **DFS:** Stack�� ����Ͽ� ��� ��θ� Ž���� �� ���
* **BFS:** Queue�� ����Ͽ� �ִ� �Ÿ� ��θ� Ž���� �� ���

### Dijkstra Algorithm
*Similar to Prim Algorithm*<br>
���� �� ������ �Ÿ��� �־��� graph���� ���. Ư�� ��忡�� �����Ͽ� �ִ� �Ÿ� ã�� �� ���

* **Priority Queue** ���
* �ð����⵵: `O(|E|log|V|)`
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
[����](#����)
<br></br>

## Others
[����](#����)
<br></br>
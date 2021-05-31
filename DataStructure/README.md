# Data Structure
수업 내용과 구글링 정보를 참고하여 작성하였습니다. 삽입한 그림은 현재는 모두 다른 웹사이트에서 불러왔으며 출처는 적지 않았으나 추후에 출처를 기입하거나 직접 그림을 올릴 예정입니다.

<details>
<summary>예상 문제 접기/펼치기</summary>
<div markdown="1">
1. Array와 Linked List의 차이<br>
&nbsp; &nbsp;1-1. 각각의 장단점<br>
&nbsp; &nbsp;1-2. Array와 Linked List의 시간복잡도 차이<br>
&nbsp; &nbsp;1-3. 어디에서 사용되는가<br>
2. 스택과 큐의 차이<br>
&nbsp; &nbsp;2-1. 어느 메모리에 저장되는가<br>
&nbsp; &nbsp;2-2. 어디에서 사용되는가<br>
3. 트리<br>
4. 힙<br>
5. List, Set, Map의 차이<br>
&nbsp; &nbsp;3-1. 각각의 장단점
</div>
</details>

*HashTable vs. HashMap vs. TreeMap, List vs. Set*
</br><br>
## 목차
[자료구조란?](#자료구조란?)<br>
[Array, LinkedList, ArrayList](#Array,-LinkedList,-ArrayList)<br>
[스택, 큐](#스택,-큐)<br>
[List, Set, Map](#List,-Set,-Map)<br>
[Tree](#Tree)<br>
[Graph](#Graph)<br>
</br><br>

## 자료구조란?
*자료구조 각각의 효율성 및 장단점 파악하고 구현할 줄 아는 것이 중요*

데이터의 접근과 생성/수정/삭제를 용이하게 하는 데이터 저장 방식 및 조작 방법
![Data Structure](../img/data_structure.jpg)<br>
## Array, LinkedList, ArrayList
### Array
논리적 저장 순서와 물리적 저장 순서가 일치하는 데이터 나열 자료구조
* 선언할 때 Array 크기도 함께 선언해야함
* index를 통해 데이터 접근이 가능하여 `O(1)`의 시간복잡도를 가짐
* 삽입과 삭제에는 취약함 (중간에 삽입하거나 삭제되면 이후에 오는 모든 데이터의 위치를 변경해야함) - 시간복잡도: worst = `O(n)`
* Stack 메모리 섹션에 할당

### Array List
Array와 같이 물리적 주소와 논리적 주소가 일치하지만 크기 변경이 가능함
* index를 통해 데이터 접근이 가능하여 `O(1)`의 시간복잡도를 가짐
* 삽입과 삭제에는 취약함 (중간에 삽입하거나 삭제되면 이후에 오는 모든 데이터의 위치를 변경해야함) - 시간복잡도: worst = `O(n)`

### Linked List
원소들끼리 서로 연결되어 데이터를 나열한 자료구조
* 논리적 순서에 따라 데이터를 입력하지만 물리적인 주소는 순차적이지 않음
* 각 원소마다 자신의 이전 위치나 다음 위치 혹은 둘 다 기억함
* 한번에 데이터 접근이 불가능해서 연결을 따라 처음부터 탐색하는 방법밖에 없음 (시간복잡도: worst=`O(n)`)
* 삭제하거나 중간에 삽입하는 것은 배열보다 훨씬 간단함 (시간복잡도: `O(1)`)
* Tree 구조에서 자주 사용됨
* Heap 메모리 섹션에 할당

[위로](#목차)
<br></br>

## 스택, 큐
### Stack
* **LIFO(Last-In First-Out)** 의 자료구조로 마지막에 삽입한 자료를 가장 먼저 꺼냄
* **stack underflow:** 자료가 stack에 없을 때 `pop()`하면 생기는 오류<br> **stack overflow:** stack 크기 이상의 데이터를 삽입하려고 할 때 생기는 오류
* index를 늘리고 줄이는 과정만 있으면 되므로 Array를 사용해서 구현하는 것이 좋음
* `MAX_SIZE`가 존재해서 메모리가 가득 차면 더 큰 크기의 구역에 복제시켜 크기를 늘림
* DFS나 재귀 구현할 때 사용

### Queue
* **FIFO(First-In First-Out** 의 자료구조로 처음에 삽입한 자료를 가장 먼저 꺼냄
* LinkedList로 구현하는 것이 삭제와 삽입에 용이함(한 쪽 끝에서는 삽입, 다른 한 쪽에서는 삭제)
* BFS나 캐시 구현할 때 사용
<br></br>

## List, Set, Map
### List
저장공간이 필요에 의해 자동으로 늘어나는 순서가 있는 저장공간
* 순서가 있고 중복 허용 (배열과 유사)
* 장점: 배열이 자동으로 늘어남<br>단점: 원하는 데이터가 뒤쪽에 위치하는 경우 탐색 속도에 문제가 있음

### Set
집합으로 순서가 없고 중복이 허용되지 않음
* 장점: **Hash Table** 을 사용하여 해쉬값을 기반으로 데이터를 해당 공간(Bucket)에 저장하기 때문에 특정 값을 확인하는 데에 속도가 빠름
* 단점: 단순 집합의 개념으로 정렬하려면 별도의 처리 필요
* 사용 상황
  * 중복 값을 골라내야할 때
  * 특정 값이 있는지 빠르게 확인해야할 때

### Map
키와 데이터를 같이 저장해서 키를 이용하여 데이터 탐색. 키는 중복될 수 없음
* 장점: 빠른 속도
* 단점: Key의 검색 속도가 전체 속도를 좌우함

**Hash Table:** (Key,Value)로 데이터 저장<br>
![Hash Table](../img/HashTable.png)<br>
* 데이터의 key에 Hash Function을 적용해서 고유 index를 만들어내고 내부적으로 배열(Bucket)을 사용하여 데이터 저장
* 평균 시간복잡도: `O(1)`
* `Null`값을 허용하지 않음
* 병렬로 진행 (동기화 필요)
* Hash 값이 충돌하는 경우
  * **Seperate Chaining:** 버킷 내에 여러 데이터를 연결하여 저장
  * **Open Addressing:** 특정 규칙을 사용하여 해당 버킷이 아닌 다른 버킷에 데이터 저장

**Hash Map:** 동기화가 진행되지 않는 Hash Table
* Hash Table과 거의 동일
* 병렬 처리를 하지 않음 (동기화 필요 없음)
* `Null`값을 허용함

[위로](#목차)
<br></br>

## Tree
노드로 이루어져있으며 루트 노드에서 시작해서 자식 노드를 만들어내며 뻗어나가는 계층 구조의 자료 구조
* Loop이 존재하지 않음
* Traversals *(구현해보기)*
  * Inorder: Left-Root-Right
  * Preorder: Root-Left-Right
  * Postorder: Left-Right-Root

### Binary Tree
루트 노드를 기준으로 2개의 subtree로 나누어지며, subtree 모두 binary임 (부모노드는 최대 2개의 자식 노드를 가짐)
* Array로 표현 시 인덱스 `i`관련 노드:
  * 부모노드: `i/2`
  * 왼쪽 자식 노드: `2i`
  * 오른쪽 자식 노드: `2i+1`
  <br>
* 종류
  * **Perfect Binary Tree:** 모든 노드가 꽉 찬 이진 트리
  * **Complete Binary Tree:** 왼쪽에서부터 오른쪽으로 채워진 이진 트리
  * **Full Binary Tree:** 모든 부모 노드가 0개 혹은 2개의 자식노드를 가진 이진 트리
  * **Balanced Binary Tree:** 모든 왼쪽 노드의 높이와 오른쪽 노드의 높이 차이가 1이 넘지 않는 트리 (트리의 높이가 `O(log n)`)
    * e.g. AVL 트리, Red-Black 트리, B 트리

### Binary Search Tree(BST)
이진탐색 장점(탐색 시간이 `O(log n)`)과 Linked List의 장점(삽입과 삭제가 `O(1)`)을 모은 트리 구조
* 시간복잡도: `O(h)`이지만 높이 균형이 맞지 않으면 worst도 가능
* 각 부모 노드는 left child보다 크고 right child보다 작음
* 중복 노드 없음

**AVL Tree:** Balanced Binary Search Tree

**B Tree:** DB나 파일시스템에서 사용되는 자료구조이며 이진트리를 확장하여 더 많은 자식 보유
* 특징
  * 루트노드가 leaf 노드인 경우를 제외하고 항상 최소 2개의 children 보유
  * 모든 leaf 노드의 레벨 동일
  * 새로운 값은 leaf에 삽입 후 재정렬
  * 오름차순 노드 정렬
  * leaf node는 최소 M/2-1개의 key를 가져야함

### Heap
*Heapify 손코딩 구현*

Complete Binary Tree의 일종이며 최대값이나 최소값을 찾을 때 용이
* 중복 값 허용
* 우선순위 queue를 이용하여 implement
* 힙 종류: Max Heap, Min Haep
* 힙 구조를 유지(**Heapify**)하려면 `O(log n)`의 시간이 걸림

**Priority Queue**<br>
* Array, Linked List, Heap으로 구현 가능하지만 Array와 Linked List의 단점으로 인해 주로 Heap으로 구현함

[위로](#목차)
<br></br>

## Graph
### 그래프 탐색
**DFS:** 한 정점에서 시작하여 더이상 나아갈 수 없는 정점까지 이동하면서 search (Stack 사용)<br>
**BFS:** 한 정점에서 연결되어있는 모든 정점으로 나아가면서 최단 경로를 찾아냄 (Queue 사용)

### Minimum Spanning Tree
edge의 가중치의 합을 최소로 하는 spanning tree
*Spanning Tree:* 그래프의 모든 vertex가 Cycle 없이 연결된 형태의 graph<br>

**Algorithm**
* **Kruskal Algorithm**
  * Greedy Method를 이용하여 graph의 모든 정점을 최소 비용으로 연결
  * 무조건 최소 비용의 edge만 선택
  * Sparse Graph에 적합
  * 시간복잡도: `O(E log E)`
  * 과정:
    1. edge cost를 사용하여 오름차순으로 edge 정렬
    2. edge list 중에서 cycle을 형성하지 않는 edge를 순서대로 선택
    3. graph 집합에 추가
    4. 모든 vertex가 연결되었다면 종료
* **Prim Algorithm**
  * 정점에서 시작해서 점진적으로 그래프를 확대시켜나가는 알고리즘
  * Dense Graph에 적합
  * 시간복잡도: `O(n^2)`
  * 과정
    1. 초기에 최초 정점 하나만 graph에 추가
    2. 형성된 그래프에서 cost가 낮은 edge로 연결될 수 있는 정점과 edge 추가
    3. 총 edge 수가 n-1개가 되면 종료

[위로](#목차)
<br></br>
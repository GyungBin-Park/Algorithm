# Search



## Search, 검색 알고리즘이란?

내가 원하는 `데이터를 찾는다`는 뜻이다.

예를 들어, `list1 = ['a', 'b', 'c', 'd']`라는 `배열(리스트)`가 있다고 할 때

'c'가 있는 위치의 index를 찾는 것이 Search 입니다.



### Search 종류는?

1. linear Search
2. Binary Search
3. Hash



## Linear Search

### Linear Search란?

- 순차검색, Sequential Search 라고도 합니다. 차례대로 검색한다는 뜻



아까의 예시를 다시 들어볼까요? 코드로 구현해보면,

~~~python
def search(array, key):				# 찾으려는 값

	for i in range(array):			# 리스트에서 for
		if list1[i] == key:			# 찾으려는 값이 리스트 안의 값과 같다면
			return i				# 그 값의 리스트 인덱스 반환

        
array1 = ['a', 'b', 'c', 'd']
key = 'c'

print(search(array1, key))

~~~



< 해석 >

- list1의 index들에 대해서 차례대로 검색을 합니다.

- 리스트의 0번부터 차례대로 내가 찾으려는 값이 맞는지 확인을 하는데, 진행 중에 리스트의 어떤 위치에서 내가 찾는 key 값을 찾았다면?!

- 그러면 for을 더 수행하지 않고 return

-> 맨 뒤에서부터 차례대로 검색해도 상관 없다.



가장 쉬운 검색 알고리즘이고, 누구나 익숙하게 생각하는 알고리즘이다.



< problem >

하지만 리스트 안에 우리가 찾으려는 key가 리스트의 맨 끝에 있다고 한다면?

리스트 안에 데이터가 100개가 있다고 하면 ( index : 0~99 )

Sequential Search는 맨 앞에서부터 총 100번의 비교를 해야 한다.

1000개의 데이터 중에서 찾는다면? 1000번 비교, 데이터의 개수가 많아질수록 힘들어진다.

수많은 데이터에서 하나를 찾는다고 생각하면 비교하는 part에서 시간 낭비가 된다.

그래서 Sequential Search보다 더 효율적인 알고리즘이 있다.!



## Binary Search



### Binary Search란?



* 한국말로 이진 검색, 시퀀스형을 2개로 잘라서 검색하는 알고리즘.



< 가장 중요한 점! >

1. <u>__정렬(Sort)__</u>이 되어 있어야 합니다.

   오름차순 혹은 내림차순 정렬이 되어 있어야 한다는 뜻.

   

__ex__ ) list2 = [11, 12, 13, 14, 15, __16__, 17, 18, 19, 20, 21]

11개의 데이터가 들어있는 리스트에서, 14의 index를 찾는다고 합시다.

먼저 리스트에서 가운데 index의 데이터를 봅니다.

가운데 index를 계산하는 방법 = ( 맨 왼쪽의 index + 맨 오른쪽의 index) / 2 )

위의 예시에서는 (0 + 10) / 2 = 5

List[5] = 16이므로, 우리가 찾는 14가 아닙니다. 14는 16보다 작네요?

그 리스트에서 왼쪽의 리스트에 있겠구나! 라고 생각을 하는 거에요.

왼쪽 리스트로 제한을 해서 가운데를 보면, 13입니다!

13은 14보다 작으니, 13에서 오른쪽만 보는거에요.

left = 3, right = 4, (left + right) / 2 = 3

( 이렇게 배열에서 중간을 찾기 애매한 경우에는 나머지를 떼고 계산한 index를 사용하면 됩니다.)

index=3의 데이터를 보니, 14가 맞으니, 찾은겁니다.

비교를 하고, 아! 여기보다는 왼쪽에 있구나, 오른쪽에 있구나.

라고 판단을 해야 하기 때문에 기본적으로 정렬이 되어 있어야 합니다.



```python
def BinarySearch(array, key, low, high)
	if low > high:		# 예외 처리
    	return false

	mid = (low+high) / 2  # 나누기를 했을 때 나머지는 신경 안쓴다.

	if value < array[mid]:			# 우리가 찾는 값이 가운데 기준 왼쪽에 있다는 의미
		return binarySearch(array, value, low, mid-1)
	elif array[mid] < value:		# 우리가 찾는 값이 가운데 기준 오른쪽에 있다는 의미
		return binarySearch(array, value, mid+1, high)
	else:
    	return mid
```





### Binary Search와 Linear Search 비교



비교하는 입장에서만 생각해 봅시다.

`Linear Search` : 데이터가 10개라고 하면 __최대 10번__의 비교 수행

`Binary Search` : 데이터가 10개라고 하면, __최대 4번__의 비교 수행

  → 가장 오래 비교한다고 했을 때, Binary Search가 압도적으로 유리해요.



최소의 경우에는 어떨까요?

Linear Search : 1번!

Binary Search : 1번!

똑같죠?

어떻게 보더라도, `Binary Search`가 유리합니다.



기본적인 차이점은,

Linear Search : 정렬이 되든, 안되든 상관이 없다. 어차피 왼쪽에서부터 순차적으로 맞는지 틀린지만 확인할 것이기 때문이다.

Binary Search : 필수적으로 정렬이 되어 있는 상태이어야 한다.





## Hash, 해시법

* 데이터의 검색 뿐만 아니라, 추가, 삭제 등에도 용이한 알고리즘

  

### what is hash?

- 해싱된 키(Hash Key)를 가지고 배열의 인덱스로 사용하기 때문에 **삽입, 삭제, 검색이 매우 빠르다**.
- 해시 함수(Hash Function)를 사용하는데 **추가적인 연산이 필요**하다.
- 해시 테이블(Hash Table)의 크기가 유한적이고 해시 함수(Hash Function)의 특성상 **해시 충돌(Hash Collision)이 발생**할 수 밖에 없다.
- 충돌이 없거나 적으면 O(1)의 상수 시간에 가까워지고, 충돌이 발생하면 할수록 성능은 점점 O(n)에 가까워진다. ( 극단적 경우 )



* int 값들이 들어있는 시퀀스에서의 해시 함수는 ```나누기``` 함수가 대표적이다.



Ex. list3 = [5, 7, 20, 31, 37, 53, 78, 6]이 있다고 하면,

​	해시 함수 : x % 7, key를 7로 나눈 나머지가 해시 값이 된다.



| list3                  | 5    | 7    | 20   | 31   | 37   | 53   | 78   | 6    |
| ---------------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| hash func ( 나누기 7 ) | 5    | 0    | 6    | 3    | 2    | 4    | 1    | 6    |



* hash Table에는 이렇게 들어간다.

| hash index | 0    | 1    | 2    | 3    | 4    | 5    | 6    |
| ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| hash value | 5    | 78   | 37   | 31   | 53   | 5    | 20   |
|            |      |      |      |      |      |      | 6    |



~~~python

# list3 = [5, 7, 20, 31, 37, 53, 78, 6]

list3 = [5, 7, 20, 31, 37, 53, 78]

def hashTable(list3):
	hashL = [None for i in range(8)]	# 리스트 안의 값이 None인 배열 만들기
	for i in range(7):
		hashL[(list3[i] % 7)] = list3[i] # hash 함수를 적용한 리스트에 넣기
	return hashL

print(hashList(list3))					# Hash 함수를 적용한 리스트 출력


~~~



만약에 Hash Function을 통해서 나누기를 했는데, 같은 해시값이 나올 수 있다!

예를 들어 나누기 7이 해시 함수라고 했을 때, 

데이터가 8, 15가 있다고 한다면 둘 다 나누기 7을 한 나머지는 1이 되는데..

리스트의 index 1에는 데이터가 하나만 들어갈 수 있지 않을까?



여기서 해결 방법은?



1. chained hash 이용
2. 



```python
# Chained hash

class Node:
    
    def __init__(self, key: Any, value: Any, next: Node) -> None:
        self.key   = key    # 키
        self.value = value  # 값
        self.next  = next   # 뒤쪽 노드를 참조

# Do it! 실습 3-5 [B]
class ChainedHash:
    """체인법을 해시 클래스 구현"""

    def __init__(self, capacity: int) -> None:
        self.capacity = capacity            # 해시 테이블의 크기를 지정
        self.table = [None] * self.capacity # 해시 테이블(리스트)을 선언
											# 해시 테이블 - 빈 리스트 

    def hash_value(self, key: Any) -> int:
        """해시값을 구함"""
        if isinstance(key, int):
            return key % self.capacity
        return(int(hashlib.sha256(str(key).encode()).hexdigest(), 16) % self.capacity)
    # string 문자열을 해시값, int로 바꿔주는 것이라고 생각.

# Do it! 실습 3-5[C]
    def search(self, key: Any) -> Any:
        """키가 key인 원소를 검색하여 값을 반환"""
        hash = self.hash_value(key)  # 검색하는 키의 해시값
        p = self.table[hash]         # 노드를 노드

        while p is not None:
            if p.key == key:
                 return p.value  # 검색 성공
            p = p.next           # 뒤쪽 노드를 주목

        return None              # 검색 실패

    def add(self, key: Any, value: Any) -> bool:
        """키가 key이고 값이 value인 원소를 삽입"""
        hash = self.hash_value(key)  # 삽입하는 키의 해시값
        p = self.table[hash]         # 주목하는 노드

        while p is not None:
            if p.key == key:
                return False         # 삽입 실패
            p = p.next               # 뒤쪽 노드에 주목

        temp = Node(key, value, self.table[hash])
        self.table[hash] = temp      # 노드를 삽입
        return True                  # 삽입 성공

# Do it! 실습 3-5[D]
    def remove(self, key: Any) -> bool:
        """키가 key인 원소를 삭제"""
        hash = self.hash_value(key)  # 삭제할 키의 해시값
        p = self.table[hash]         # 주목하고 있는 노드
        pp = None                    # 바로 앞 주목 노드

        while p is not None:
            if p.key == key:  # key를 발견하면 아래를 실행
                if pp is None:
                    self.table[hash] = p.next
                else:
                    pp.next = p.next
                return True  # key 삭제 성공
            pp = p
            p = p.next       # 뒤쪽 노드에 주목
        return False         # 삭제 실패(key가 존재하지 않음)

    def dump(self) -> None:
        """해시 테이블을 덤프"""
        for i in range(self.capacity):
            p = self.table[i]
            print(i, end='')
            while p is not None:
                print(f'  → {p.key} ({p.value})', end='')  # 해시 테이블에 있는 키와 값을 출력
                p = p.next
            print()
```


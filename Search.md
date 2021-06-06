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

- 순차검색, Sequential Search 라고도 합니다. 차례대로 검색한다는 뜻입니다.



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



list1의 index들에 대해서 차례대로 검색을 합니다.

리스트트의 0번부터, 끝까지 진행을 하는데, for 구문을 진행 중에, 어떤 위치에서 key 값을 찾았다?!

그러면 for을 더 수행하지 않고 return

이것이 linear Search입니다.

linear : 직역하면 선형, 순차적으로 라는 뜻이라고 생각하면 되요.

다른 말로, 순차 검색이라고도 합니다.

맨 앞에서부터 혹은 맨 뒤에서부터 차례대로 검색해서 리스트 안에 있는지 없는 지를 살피는 것이죠.



가장 쉬운 검색이에요.



하지만, 잘 생각해 봅시다.

리스트 안에 우리가 찾으려는 값이 맨 뒤에 있다고 한다면?

리스트 안에 데이터가 100개가 있다고 하면 ( index가 0~99까지)

100번 동안 비교를 해야 하는 거에요.

1000개가 있는데 맨 끝에 있다면? 1000번 비교, 뭔가 많다고 느껴지지 않나요?

수많은 데이터에서 하나를 찾는다고 생각하면 시간 낭비가 되겠죠..

그래서 linear Search보다 더 효율적인 알고리즘이 있습니다.



## Binary Search



### Binary Search란?



이진 검색, 2개로 잘라서 검색하는 알고리즘.



가장 중요한 점!

1. <u>__정렬(Sort)__</u>이 되어 있어야 합니다.

   오름차순 혹은 내림차순 정렬이 되어 있어야 한다는 뜻.

   

__ex__ ) list2 = [11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21]

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



### what is hash?






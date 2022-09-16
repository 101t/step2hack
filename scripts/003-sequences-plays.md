# Sets and Tuples

## Set in math as "set theory" using bitwise operators

```python
>>> s1 = {1, 2, 5, 7, 8}
>>> s2 = {4, 6, 7, 8, 9}
```

### 1. Union:

The union of two sets contains all the elements contained in either set (or both sets), The union is notated `s1 ∪ s2`.

```python
>>> s1 | s2 # s1 ∪ s2
{1, 2, 4, 5, 6, 7, 8, 9}
```

### 2. Intersection:

The intersection of two sets contains only the elements that are in both sets, The intersection is notated `s1 ∩ s2`.

```python
>>> s1 & s2 # s1 ∩ s2
{8, 7}
```

### 3. Difference:

The resulting set has elements of the `s1` set with all elements from the `s2` set removed. 

```python
>>> s1 - s2
{1, 2, 5}
```

An element will be in the result if it is in the `s1` set and not in the `s2` set.

```python
>>> s2 -s1
{9, 4, 6}
```

### 4. Symmetric  Difference:

The result is set of all values which are in one of the sets, but not both.

```python
>>> s1 ^ s2 # s1 △ s2
{1, 2, 4, 5, 6, 9}
```

`s1 △ s2` is also expressed by `(s1 ∪ s2) – (s2 ∩ s1)`

```python
>>> (s1 | s2) - (s1 & s2)
{1, 2, 4, 5, 6, 9}
```
or

The symmetric difference of two sets A and B is the set `(s1 – s2) ∪ (s2 – s1)` and is denoted by `s1 △ s2`

```python
>>> (s1 - s2) | (s2 - s1)
{1, 2, 4, 5, 6, 9}
```

## flattening tuple of tuples (or list of lists):

### 1. using flatten method

```python
def flatten(sqnc):
	if sqnc:
		car,*cdr = sqnc
		if isinstance(car,(list,tuple)):
			if cdr: 
				return flatten(car) + flatten(cdr)
			return flatten(car)
		if cdr: 
			return [car] + flatten(cdr)
		return [car]
```

```python
>>> flatten((1,2,3,(4,5,6,(7,8,(((1,2)))))))
[1, 2, 3, 4, 5, 6, 7, 8, 1, 2]
```

### 2. using [https://en.wikipedia.org/wiki/Monoid#Monoids_in_computer_science](Monoid) way, inefficient, But fun

```python
>>> list_of_lists = [[1, 2, 3], [4, 5, 6], [7], [8, 9]]
>>> sum(list_of_lists, [])
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```
source: [https://stackoverflow.com/a/952946/1756032](here)
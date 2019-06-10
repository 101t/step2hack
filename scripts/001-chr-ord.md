## using `chr()` and `ord()`:

1. using `chr()` function:
```python
>>> chr(111)+chr(115)
'os'
```

2. using `ord()` function:
```python
>>> ord('o'),ord('s')
(111, 115)
```

then
```python
>>> ll = [ord(x) for x in "whoami"]
>>> ll
[119, 104, 111, 97, 109, 105]
>>> zz = "".join([chr(z) for z in ll])
>>> zz
'whoami'
```

have this two functions on the way

```python
>>> func1 = lambda list1: "".join([chr(z) for z in list1]) # Input: List, Output: String
>>> func2 = lambda str1: [ord(x) for x in str1] # Input String, Output: List
```

usage

```python
>>> ll = func2("ls /") # encode string as list of ascii value integers
>>> func1(ll) # decode list of ascii integers
'ls /'
```
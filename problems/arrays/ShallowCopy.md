
Did some test about Reference Assignment, Shallow Copy and Deep Copy:

How Copies Work:

Reference Assignment
```
let arr1 = [1,2,3]
let arr2 = arr1;
arr1[0]=9

> arr1

[ 9, 2, 3 ]

> arr2

[ 9, 2, 3 ]
```
Stack: Creates new variable pointing to same heap address
Heap: No new object created
Result: Both variables share the same object


Shallow Copy - Primitives
```
let arr3 = arr1.slice()
> arr1

[ 9, 2, 3 ]

> arr2

[ 9, 2, 3 ]

> arr3

[ 9, 2, 3 ]

> arr1[0]=8;

8

> arr1

[ 8, 2, 3 ]

> arr2

[ 8, 2, 3 ]

> arr3

[ 9, 2, 3 ] 
```

Shallow Copy - Objects

```
> let arrObj1 = [{id:1}, {id:2}, {id:3}];
> let arrObj2 = arrObj1;
> let arrObj3 = arrObj1.slice()
> arrObj1.sort((a,b) => b['id'] - a['id'])
[ { id: 3 }, { id: 2 }, { id: 1 } ]
> arrObj1
[ { id: 3 }, { id: 2 }, { id: 1 } ]
> arrObj2
[ { id: 3 }, { id: 2 }, { id: 1 } ]
> arrObj3
[ { id: 1 }, { id: 2 }, { id: 3 } ]
```

```
> arrObj1[0].id = 9;
9
> arrObj1
[ { id: 9 }, { id: 2 }, { id: 1 } ]
> arrObj2
[ { id: 9 }, { id: 2 }, { id: 1 } ]
> arrObj3
[ { id: 1 }, { id: 2 }, { id: 9 } ]
>
```

Deep Copy


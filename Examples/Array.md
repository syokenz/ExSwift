#Array
###Refer to the [Wiki](https://github.com/pNre/ExSwift/wiki/Array) for updated info.

### Contents ###

- [Array](#array)
    - [Instance Methods](#instance-methods)
    	- [`first`](#first)
    	- [`last`](#last)
    	- [`get`](#get)
    	- [`remove`](#remove)
    	- [`at`](#at)
    	- [`take`](#take)
    	- [`takeWhile`](#takeWhile)
    	- [`tail`](#tail)
    	- [`skip`](#skip)
    	- [`skipWhile`](#skipWhile)
    	- [`contains`](#contains)
    	- [`difference`](#difference)
    	- [`intersection`](#intersection)
    	- [`union`](#union)
    	- [`unique`](#unique)
    	- [`indexOf`](#indexof)
    	- [`zip`](#zip)
    	- [`shuffle`](#shuffle)
    	- [`shuffled`](#shuffled)
    	- [`sample`](#sample)
    	- [`max`](#max)
    	- [`min`](#min)
    	- [`each`](#each)
    	- [`eachRight`](#eachright)
    	- [`any`](#any)
    	- [`all`](#all)
    	- [`reject`](#reject)
    	- [`pop`](#pop)
    	- [`push`](#push)
    	- [`shift`](#shift)
    	- [`unshift`](#unshift)
    	- [`groupBy`](#groupby)   
    	- [`countBy`](#countby)   
    	- [`reduceRight`](#reduceright)   
    	- [`implode`](#implode)
    	- [`flatten`](#flatten)
    - [Class Methods](#class-methods)
    	- [`range`](#range)
    - [Operators](#operators)
    	- [Difference](#difference)
    	- [And](#and)
    	- [Or](#or)
    	- [Subscript with Range](#subscript-with-range)
    	- [Times](#times)
    	- [Implode](#implode-1)
    	
### Instance Methods ###

#### `first` ####
```
let array = [1, 2, 3, 4]
array.first() 
// → 1
```

#### `last` ####
```
let array = [1, 2, 3, 4]
array.last() 
// → 4
```

#### `get` ####
```
let array = [1, 2, 3, 4]

array.get(1) 
// → 2

array.get(0..2)
// → [0, 1]
```

`get` also supports negative indexes:

```
array.get(-1)
// → 4
```

#### `remove` ####
```
let array = [1, 2, 3, 4]
array.remove(1)
println(array) 
// → [2, 3, 4]
```

#### `at` ####
```
let array = [1, 2, 3, 4]

array.at(1, 3)
// → [2, 4]

array[1, 0, 3]
// → [2, 1, 4]
```

`at` also supports negative indexes:

```
array.at(-1, -3)
// → [4, 2]
```

#### `take` ####
```
[1, 2, 3, 4].take(2)
// → [1, 2]
```

#### `takeWhile` ####
```
[1, 2, 3, 4, 5, 2].takeWhile { $0 < 4 }
// → [1, 2, 3]
```

#### `tail` ####
```
[1, 2, 3, 4, 5].tail(3)
// → [3, 4, 5]
```

#### `skip` ####
```
[1, 2, 3, 4, 5].skip(3)
// → [4, 5]
```

#### `skipWhile` ####
```
[1, 2, 3, 4, 5, 2].skipWhile { $0 < 4 }
// → [4, 5, 2]
```

#### `contains` ####
```
[1, 2, 3, 4].contains(2)  
// → true

[1, 2, 3, 4].contains(20) 
// → false

[1, 2, 3, 4].contains(3, 4) 
// → true
```

#### `difference` ####
```
[1, 2, 3, 4].difference([2, 3])	
// → [1, 4]

[1, 2, 3, 4] - [2, 3]
// → [1, 4]
```

#### `intersection` ####
```
[1, 2, 3, 4].intersection([2, 3])	
// → [2, 3]

[1, 2, 3, 4] & [2, 3]
// → [2, 3]
```

#### `union` ####
```
[1, 2, 3, 4].union([5, 6])	
// → [1, 2, 3, 4, 5, 6]

[1, 2, 3, 4].union([2, 3])	
// → [1, 2, 3, 4]
```

#### `unique` ####
```
[1, 1, 3, 3, 4].unique() as Array<Int>
// → [1, 3, 4]
```

#### `indexOf` ####
```
[1, 2, 3, 4].indexOf(3)
// → 2

[1, 2, 3, 4].indexOf(5)
// → -1
```

#### `zip` ####
```
[1, 2].zip(["A", "B"])
// → [[1, "A"], [2, "B"]]
```

#### `shuffle` ####
```
let array = [1, 2, 3, 4]
array.shuffle()
println(array)
// → [3, 2, 4, 1]
```

#### `shuffled` ####
```
[1, 2, 3, 4].shuffled()
// → [2, 4, 3, 1]
```

#### `sample` ####
```
[1, 2, 3, 4].sample()
// → [2]

[1, 2, 3, 4].sample(size: 2)
// → [3, 4]
```

#### `max` ####
```
[1, 2, 3, 4].max() as Int
// → [4]
```

#### `min` ####
```
[1, 2, 3, 4].min() as Int
// → [1]
```

#### `each` ####
```
[1, 2, 3, 4].each {
    (item: Int) in println(item)
}
// → 1 2 3 4

["A", "B", "C"].each {
    (index: Int, item: String) in println(index, item)
}
// → (0, A) (1, B) (2, C)
```

#### `eachRight` ####
```
[1, 2, 3, 4].eachRight {
    (item: Int) in println(item)
}
// → 4 3 2 1

["A", "B", "C"].eachRight {
    (index: Int, item: String) in println(index, item)
}
// → (2, A) (1, B) (0, C)
```

#### `any` ####
```
[1, 2, 3, 4].any {
    return $0 % 2 == 0
}
// → true

[1, 2, 3, 4].any {
    return $0 > 5
}
// → false
```

#### `all` ####
```
[1, 2, 3, 4].all {
    return $0 < 5
}
// → true

[1, 2, 3, 4].all {
    return $0 % 2 == 0
}
// → false
```

#### `reject` ####
```
[1, 2, 3, 4].reject {
    return $0 % 2 == 0
}
// → [1, 3]
```

#### `pop` ####
```
var array = [1, 2, 3, 4]
array.pop()
// → 4
println(array)
// → [1, 2, 3]
```

#### `push` ####
```
var array = [1, 2, 3, 4]
array.push(5)
println(array)
// → [1, 2, 3, 4, 5]
```

#### `shift` ####
```
var array = [1, 2, 3, 4]
array.shift()
// → 1
println(array)
// → [2, 3, 4]
```

#### `unshift` ####
```
var array = [1, 2, 3, 4]
array.unshift(0)
println(array)
// → [0, 1, 2, 3, 4]
```

#### `groupBy` ####
```
let array = array = [1, 2, 3, 4, 5]
let group = array.groupBy(groupingFunction: {
    (value: Int) -> Bool in
    return value > 3
})
// → [true: [5, 6], false: [1, 2, 3]]
```

#### `countBy` ####
```
let array = array = [1, 2, 3, 4, 5]
let group = array.countBy(groupingFunction: {
    (value: Int) -> Bool in
    return value > 3
})
// → [true: 2, false: 3]
```

#### `reduce` ####
Different from the standerd `reduce`. Assumes the elements type `Element` as return type and `self.first()` as initial value.

```
let list = [5, 5, 2, 3]
list.reduce(+)
// → 15
```

#### `reduceRight` ####
With initial argument:

```
let list = [[0, 1], [2, 3], [4, 5]]
list.reduceRight(Array<Int>(), { return $0 + $1 });
// → [4, 5, 2, 3, 0, 1]
```

*Without* initial argument:

```
let list = ["A", "B", "C"]
list.reduceRight(+)
// → "CAB"
```

#### `implode` ####
```
["A", "B", "C"].implode("_")
// → A_B_C
```

#### `flatten` ####
```
let array = [5, [6, [7]], 8]
array.flatten() as Int[]
// → [5, 6, 7, 8]
```

### Class Methods ###

#### `range` ####
```
Array<Int>.range(0..3)
// → [0, 1, 2]
```

### Operators ###

#### Difference ####
```
[1, 2] - [2, 4]
// → [1]

[1, 2] - 1
// → [2]
```

#### And ####
Intersection

```
[1, 2] & [2, 4]
// → [2]
```


#### Or ####
Union

```
[1, 2] | [2, 4]
// → [1, 2, 4]
```

#### Subscript with Range ####
```
let a = [1, 2, 3]
println(a[1...2])
// → [2, 3]
```

#### Times ####
```
let a = [1, 2, 3]
a * 3
// → [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

#### Implode ####
```
let a = ["Hello", "World"]
a * ", "
// → "Hello, World"
```

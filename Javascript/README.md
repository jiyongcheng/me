#### 从数组中删除一个元素
```javascript
var array = [2, 5, 9];
var index = array.indexOf(5);
if (index > -1) {
  array.splice(index, 1);
}
// array = [2, 9]
```
> The second parameter of splice is the number of elements to remove. Note that splice modifies the array in place and returns a new array containing the elements that have been removed.

#### 取两个数组的交集
```javascript
array1.filter(value => -1 !== array2.indexOf(value));
```
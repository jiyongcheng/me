#### 从数组中删除一个元素
```javascript
var array = [2, 5, 9];
var index = array.indexOf(5);
if (index > -1) {
  array.splice(index, 1);
}
// array = [2, 9]
```
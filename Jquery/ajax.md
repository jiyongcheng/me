####$.ajax的使用

```
$.ajax({
  method: "POST",
  url: "some.php",
  data: { name: "John", location: "Boston" }
}).success(function(data) {
    alert( "Data Saved: " + msg );
});
  
```
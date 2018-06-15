####$.ajax的使用

1.
```
$.ajax({
   url: '',
   type: 'POST'
   data: {
      format: 'json'
   },
   error: function() {},
   success: function(data) {},
});

```
2.
```
$.ajax({
   url: '',
   type: 'GET'
   data: {
      format: 'json'
   },
   error: function() {},
   success: function(data) {},
});

```

3.
```
// Assign handlers immediately after making the request,
// and remember the jqXHR object for this request
var jqxhr = $.ajax( "example.php" )
  .done(function() {
    alert( "success" );
  })
  .fail(function() {
    alert( "error" );
  })
  .always(function() {
    alert( "complete" );
  });
 
// Perform other work here ...
 
// Set another completion function for the request above
jqxhr.always(function() {
  alert( "second complete" );
});

```

> done 和 success一样, fail和error一样

####$.get使用

```
var jqxhr = $.get( "example.php", function() {
  alert( "success" );
})
  .done(function() {
    alert( "second success" );
  })
  .fail(function() {
    alert( "error" );
  })
  .always(function() {
    alert( "finished" );
  });
 
// Perform other work here ...
 
// Set another completion function for the request above
jqxhr.always(function() {
  alert( "second finished" );
});
```

> same as 
```
$.ajax({
  url: url,
  data: data,
  success: success,
  dataType: dataType
});
```

####$.post的使用

```
$.post(
  "test.php", 
  { name: "John", time: "2pm" }
)
.done(function( data ) {
  alert( "Data Loaded: " + data );
});
```

> same as 
```
$.ajax({
  type: "POST",
  url: url,
  data: data,
  success: success,
  dataType: dataType
});
```


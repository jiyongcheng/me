####$.ajax的使用

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


$.ajax({
   url: '',
   type: 'GET'
   data: {
      format: 'json'
   },
   error: function() {},
   success: function(data) {},
});

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
####$.ajax的使用

1.
```javascript
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
```javascript
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
```javascript
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

```javascript
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

```javascript
$.ajax({
  url: url,
  data: data,
  success: success,
  dataType: dataType
});
```

####$.post的使用

```javascript
$.post(
  "test.php", 
  { name: "John", time: "2pm" }
)
.done(function( data ) {
  alert( "Data Loaded: " + data );
});
```

> same as 

```javascript
$.ajax({
  type: "POST",
  url: url,
  data: data,
  success: success,
  dataType: dataType
});
```

####ajax的事件顺序

This is the full list of Ajax events, and in the order in which they are triggered. The indented events are triggered for each and every Ajax request (unless a global option has been set). The ajaxStart and ajaxStop events are events that relate to all Ajax requests together.

  * ajaxStart (Global Event)
This event is triggered if an Ajax request is started and no other Ajax requests are currently running.
    * beforeSend (Local Event)
This event, which is triggered before an Ajax request is started, allows you to modify the XMLHttpRequest object (setting additional headers, if need be.)

    * ajaxSend (Global Event)
This global event is also triggered before the request is run.
    * success (Local Event)
This event is only called if the request was successful (no errors from the server, no errors with the data).
    * ajaxSuccess (Global Event)
This event is also only called if the request was successful.
    * error (Local Event)
This event is only called if an error occurred with the request (you can never have both an error and a success callback with a request).
    * ajaxError (Global Event)
This global event behaves the same as the local error event.
    * complete (Local Event)
This event is called regardless of if the request was successful, or not. You will always receive a complete callback, even for synchronous requests.
    * ajaxComplete (Global Event)
This event behaves the same as the complete event and will be triggered every time an Ajax request finishes.

* ajaxStop (Global Event)
This global event is triggered if there are no more Ajax requests being processed.


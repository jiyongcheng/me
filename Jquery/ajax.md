#### $.ajax的使用

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

#### ajax实现文件上传

```html

<form id="email-form" name="email-form">
    <div class="form-group">
        <label class="control-label  pull-left" for="attachment-email">Attachment</label>
        <input type="file" id="attachment-email" class="form-control" name="attachment-email">
    </div>
</form>

```

```javascript

var files = document.getElementById('attachment-email').files;
var formData = new FormData();
// Loop through each of the selected files.
for (var i = 0; i < files.length; i++) {
  var file = files[i];
  // Add the file to the request.
  formData.append('attachment-email', file, file.name);
}
formData.append('content',content);
var url = '/dashboard/manage/process-action?formId=' + globalData.form.id + '&widgetId=' + me.id + '&action=send-email&dashboard=dashboard.submissionView&submissionId=' + globalData.submission.id;

$.ajax({
url: url,
method: 'POST',
processData: false,
contentType: false,
enctype: 'multipart/form-data',
data: formData,
success: function (data) {
  if (data.success) {
    
  }
}
});

```

>formData是没办法打印出来的,只是显示空值

```php
if (!empty($_FILES)) {
  //file_get_contents($_FILES['attachment-email']['tmp_name']
  //$_FILES['attachment-email']['name']
}

```

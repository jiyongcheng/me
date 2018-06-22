#### yii2-mongodb中的Aggregation

我在shell里面使用了如下的方法,把一个collection A中的_id字段复制到另外一个collection B中,并且在B中加入一个字段date.

```bash

db.behaviour_1.aggregate([{$group:{_id:"$_id"}},{"$project":{"dateAdded":new Date()}},{$out:"analytics_queue"}])

```

其中的$group是以_id来分组,$project是映射了一个新的字段并且赋值,$out是指出我要将这个操作的结果导入到哪个collection中.

一开始在网上找到的方法都是以循环来做,而且是javascript的.如下
```javascript
db.behaviour_1.find({}).forEach(
    function(x) {
        db.analytics_queue.update(
        {_id:x._id}, {_id:x._id, dateAdded:new Date()}, {upsert:true}
        )
    }
)
```
这个在shell中也能完成任务. 但是我需要在Yii2里面使用一个migration把collection复制到另一个中,另外这个collection也很大,所以要考虑性能问题.最后我使用了mongodb的aggregate.

如何在yii2中使用aggregate在 [这个链接](https://github.com/yiisoft/yii2-mongodb/blob/master/docs/guide/usage-aggregation.md) 有解释. 我的代码是这样写的




#### mongodb shell update

```
db.form.update(
{_id : new ObjectId('5af2a5cf7b15b90007022a53')}, 
{
$set:{
    "stage.0.page.1.section.1.field.2.config":{"label":"ddd","required":false}
    }
},
{upsert:true, multi:true}
)
```



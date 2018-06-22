#### yii2-mongodb中的Aggregation

我在shell里面使用了如下的方法,把一个collection A中的_id字段复制到另外一个collection B中,并且在B中加入一个字段date.

```bash

db.behaviour_1.aggregate([{$group:{_id:"$_id"}},{"$project":{"dateAdded":new Date()}},{$out:"analytics_queue"}])

```

其中的$group是以_id来分组,$project是映射了一个新的字段并且赋值,$out是指出我要将这个操作的结果导入到哪个collection中

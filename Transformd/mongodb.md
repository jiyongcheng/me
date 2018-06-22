#### yii2-mongodb中的Aggregation

我在shell里面使用了如下的方法,把一个collection A中的_id字段复制到另外一个collection B中,并且在B中加入一个字段date.

```bash

db.behaviour_1.aggregate([{$group:{_id:"$_id"}},{"$project":{"dateAdded":new Date()}},{$out:"analytics_queue"}])

```
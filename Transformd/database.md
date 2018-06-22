#### add migration file

```bash
php yii migrate/create email_verification_sdk2_add_validate_against_field -p=/app/src/dashboard/modules/forms/migrations
```
#### ActiveRecord condition

> and: the operands should be concatenated together using AND. For example, ['and', 'id=1', 'id=2'] will generate id=1 AND id=2. 

> not: requires only operand 1, which will be wrapped in NOT(). For example, ['not', 'id=1'] will generate NOT (id=1).

> between: operand 1 should be the column name, and operand 2 and 3 should be the starting and ending values of the range that the column is in. For example, ['between', 'id', 1, 10] will generate id BETWEEN 1 AND 10.

> in: operand 1 should be a column or DB expression. For example, ['in', 'id', [1, 2, 3]] will generate id IN (1, 2, 3).

> not in: similar to the in operator except that IN is replaced with NOT IN in the generated condition.

> like: operand 1 should be a column or DB expression, and operand 2 be a string or an array representing the values that the column or DB expression should be like. For example, ['like', 'name', 'tester'] will generate name LIKE '%tester%'. 

could check the link [db-query-builder](https://www.yiiframework.com/doc/guide/2.0/en/db-query-builder)

#### 查询总数

```php
//analytics_queue是mongodb的一个collection, _id是主键

//doesn't work
AnalyticsQueue::find($submissionId)->count();

//it works
AnalyticsQueue::find()->where(['_id' => $submissionId])->count();
```
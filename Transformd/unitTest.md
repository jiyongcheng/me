#### Unit Test

1.到container中

```
docker exec -ti web_app_1 bash

```

2.到/app/src目录下面运行migration，生成要测试的数据库

```
/app/src# php console/bin/yii migrate
```

3.在/app/src中运行

    * 运行所有测试
```
    root@c16011ab3739:/app/src# ../vendor/bin/codecept run --env docker
```
    * 运行单个文件的测试
    ```
    root@c16011ab3739:/app/src# ../vendor/bin/codecept run dashboard/tests/unit/modules/forms/helpers/SubmissionViewHelperTest.php --env docker
    ```
    * 生成coverage报告
    ```
    root@c16011ab3739:/app/src# ../vendor/bin/codecept run dashboard/tests/unit/modules/forms/helpers/SubmissionViewHelperTest.php --env docker --coverage-html
    ```
    
4.为什么要到app/src目录下面

> 因为codecept的配置文件在这个目录下面,所以要找到这个配置文件,然后才能执行测试
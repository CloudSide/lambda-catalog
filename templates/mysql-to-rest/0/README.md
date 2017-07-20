# MySQL To REST

为您的MySQL数据库自动生成RESTful API

## API

#### 获取某张表的记录

##### 请求

`GET /api/:table`

##### 响应

```json
{
    "result": "success",
    "json": [
        {
            "id": 1,
            "col1": 15,
            "col2": null,
            "col3": "String"
        }
    ],
    "table": "test",
    "length": 1
}
```

##### 参数

`GET /api/:table?_limit=0,10&_order[id]=DESC&id[GREAT]=4`

##### 功能参数

**MySQL的关键字加下划线前缀，例如: \_limit**¸


* `limit=` [mysql文档](https://dev.mysql.com/doc/refman/5.0/en/select.html)
* `order[column]=` 排序参数，例如：`order[age]=ASC`，`order[time]=DESC` [mysql文档](https://dev.mysql.com/doc/refman/5.0/en/select.html)
* `fields=` 将一个或多个逗号分隔的字段作为参数，过滤结果只显示指定的字段，例如：`fields=id,name` [mysql文档](https://dev.mysql.com/doc/refman/5.0/en/select.html)

##### 字段名作为参数

将字段作为参数，以便实现查询条件

语法: `column=value` or `column[operator]=value`

例如：

`sex=male&age=20`：查询sex为male，age为20的所有记录
`age[GREAT]=20`：查询age大于20的所有记录

操作符列表:

* `GREAT` : \>
* `SMALL` : \<
* `EQGREAT` : \>=
* `EQSMALL` : \<=
* `LIKE` : LIKE
* `EQ` : =

---

#### 获取一行

##### 请求

`GET /api/:table/:id`

---

#### 插入记录

##### 请求

`POST /api/:table`

---

#### 更新记录

##### 请求

`PUT /api/:table/:id`

---

#### 删除记录

##### 请求

`DELETE /api/:table/:id`

##### 响应

```json
{
    "result": "success",
    "json": {
        "deletedID": "1"
    },
    "table": "test"
}
```

#### 插入文档
db.COLLECTION_NAME.insert(document)

#### eg
db.col.insert({title: 'MongoDB 教程', 
  description: 'MongoDB 是一个 Nosql 数据库',
  by: '菜鸟教程',
  url: 'http://www.runoob.com',
  tags: ['mongodb', 'database', 'NoSQL'],
  likes: 100
})

#### 插入单条数据

> var document = db.collection.insertOne({"a": 3})
> document
{
  "acknowledged" : true,
  "insertedId" : ObjectId("571a218011a82a1d94c02333")
}

#### 插入多条数据
> var res = db.collection.insertMany([{"b": 3}, {'c': 4}])
> res
{
  "acknowledged" : true,
  "insertedIds" : [
    ObjectId("571a22a911a82a1d94c02337"),
    ObjectId("571a22a911a82a1d94c02338")
  ]
}

# 插入操作
1. insertOne 插入单条数据

        db.collection.insertOne()
        db.users.insertOne(
           {
              name: "sue",
              age: 19,
              status: "P"
           }
        )
2. insertMany 参入多条数据

        db.collection.insertMany()
        db.users.insertMany(
           [
             { name: "bob", age: 42, status: "A", },
             { name: "ahn", age: 22, status: "A", },
             { name: "xi", age: 34, status: "D", }
           ]
        )

3. 插入一条或多条数据

        db.collection.insert()
        db.users.insert(
           {
              name: "sue",
              age: 19,
              status: "P"
           }
        )
        
              

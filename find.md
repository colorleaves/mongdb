# find 命令
  **查询语句,根据指定的条件查询相关的内容,结果是一个集合**       
1. find()   `查找内容`  
2. find({name:"zhangsan"})  `指定条件去查询`  
3. 比较查询  "<" "<=" ">" ">=" "=" "!=" => $gt", "$gte", "$lt", "$lte", "$ne" "没有关键字"  
  3.1 find({age:{"$lt":3}})   
4. 逻辑查询  "and" "or" "in"  "notin"   =>  "无关键字“, "$or", "$in"，"$nin"    
  4.1 find({"$or":[age:16,age:17}]});   
  4.2 find({age:{"$in":[16,17]}});    
  4.3 find({age:{"$nin":[15,16,17]}});  
5. 正则查询
  5.1 find({age:/5$/})  
6. 复杂条件查询
  6.1 find({"$where":function(){}})  
7. 查询指定字段
  7.1 find({name:/^z/},{age:1})  `传入第二个参数,显示的字段值为1,排除的字段值为0`   

# findOne()
  **查询一条信息** 

# 聚合查询
**常见的聚合操作有：count()，distinct，group，mapReduce()**  

1. count  统计集合的数量   
    1.1 db.collection.find().conut()   
    1.2 db.collection.count({"name":"zhangsan"})      
2. distinct   统计指定条件的集合   
    1.1 db.collection.distinct("name")   
3. group   group做的聚合有些复杂。先选定分组所依据的键，此后MongoDB就会将集合依据选定键值的不同分成若干组。然后可以通过聚合每一组内的文档，产生一个结果文档  

        /*这里将用day作为group的分组键，然后取出time键值为最新时间戳的文档，同时也取出该文档的price键值。*/
            > db.test.group( {
            ... "key" : {"day":true},           /*如果是多个字段，可以为{"f1":true,"f2":true}*/
            ... "initial" : {"time" : "0"},       /*initial表示$reduce函数参数prev的初始值。每个组都有一份该初始值。*/
            ... "$reduce" : function(doc,prev) {  /*reduce函数接受两个参数，doc表示正在迭代的当前文档，prev表示累加器文档。*/
            ...     if (doc.time > prev.time) {
            ...         prev.day = doc.day
            ...         prev.price = doc.price;
            ...         prev.time = doc.time;
            ...     }
            ... } } )
        /*下面的例子是统计每个分组内文档的数量。*/
           
                > db.test.group( {
                ... key: { day: true},
                ... initial: {count: 0},
                ... reduce: function(obj,prev){ prev.count++;},
                ... } )
        /*最后一个是通过完成器修改reduce结果的例子*/
        db.test.group( {
            ... key: { day: true},
            ... initial: {count: 0},
            ... reduce: function(obj,prev){ prev.count++;},
            ... finalize: function(out){ out.scaledCount = out.count * 10 } --在结果文档中新增一个键。
            ... } )
                
                
                
     
   
   
   

  
   
  

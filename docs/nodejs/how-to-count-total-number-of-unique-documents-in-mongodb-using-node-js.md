# 如何使用 Node.js 统计 MongoDB 中唯一文档的总数？

> 原文:[https://www . geesforgeks . org/how-to-count-total-number-in-MongoDB-using-node-js/](https://www.geeksforgeeks.org/how-to-count-total-number-of-unique-documents-in-mongodb-using-node-js/)

**MongoDB** ，最受欢迎的 NoSQL 数据库，我们可以使用 MongoDB Collection . count documents()函数统计 MongoDB Collection 中的文档数量。 **mongodb** **模块**用于连接 mongodb 数据库，也用于操作 MongoDB 中的集合和数据库。

**安装模块:**可以使用以下命令安装 **mongodb** 模块。

```js
npm install mongodb
```

**项目结构:**

![](img/680c11a4a464432626c22f3eee5f7f10.png)

**在本地 IP 上运行服务器:**数据是 MongoDB 服务器所在的目录。

```js
mongod --dbpath=data --bind_ip 127.0.0.1
```

![](img/1e52d87f2ec35e8c724e121c4d12f7e0.png)

**MongoDB 数据库:**

```js
Database:GFG
Collection:aayush
```

以下是本示例中存储在数据库中的示例数据。

![](img/bc961d685cbe113ef4d34918824c1f36.png)

**文件名:index.js**

## java 描述语言

```js
// Requiring module
const MongoClient = require("mongodb");

// Connection URL
const url = 'mongodb://localhost:27017/';

// Database name
const databasename = "GFG";

MongoClient.connect(url).then((client) => {
  const connect = client.db(databasename);

  // Connect to collection
  const collection = connect.collection("aayush");

  // Counting the total unique documents
  collection.distinct("name").then((ans) => {
    // Creating set
    var set1 = new Set();

    // Adding each element in the st   
    ans.forEach(i => {
      set1.add(i); 
    });

    // Printing the size of the set
    console.log(set1.size);
  }).catch((err)=>{
      console.log(err.Message);
  }) 
}).catch((err) => {

  // Printing the error message
  console.log(err.Message);
})
```

使用以下命令运行 **index.js** 文件:

```js
node index.js
```

**输出:**

![](img/5a6fd7deed377d6468defad59152bf2c.png)